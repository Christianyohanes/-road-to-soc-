# OS Internals — Windows & Linux

## Windows

| Istilah | Penjelasan |
|---|---|
| Process | Program yang lagi jalan di memory |
| Service | Proses background, auto-start pas boot |
| Task Manager | Lihat process & service yang jalan |
| Event Viewer | Tempat baca log Windows |

### Folder penting di Event Viewer
- **Security** → log login/logout, akses (paling penting buat SOC)
- **Application** → error software
- **System** → hardware/driver

### Event ID penting
- **4624** = Successful logon
- **4625** = Failed logon

### Logon Type (field di detail event)
- `2` = Interactive (login langsung di keyboard)
- `3` = Network (dari device lain via jaringan — waspada kalau failed berkali-kali)
- `5` = Service
- `10` = RemoteInteractive (RDP)

### Registry
`regedit` — database konfigurasi Windows. Key `...\CurrentVersion\Run` sering dipakai malware buat persistence (auto-jalan pas restart).

### Cara buka Event Viewer
- Windows + R → ketik `eventvwr.msc`, Enter
- Atau search "Event Viewer" di Start Menu

---

## Linux

| Istilah | Penjelasan |
|---|---|
| File permission | Format `-rwxr-xr--` = read/write/execute untuk owner/group/others |
| `ls -l` | Lihat permission file |
| `chmod` | Ubah permission file |
| systemd | "Pengatur" service Linux modern |
| `systemctl list-units --type=service` | Lihat service yang jalan |
| journalctl | Command baca log systemd (setara Event Viewer) |
| `journalctl -f` | Live monitoring real-time |
| `/var/log/auth.log` | Log percobaan login (paling sering dicek SOC) |

### Command cari log penting
```bash
sudo journalctl | grep "Failed password"    # login gagal
sudo journalctl | grep "Accepted password"  # login berhasil
sudo journalctl -u ssh | grep "Failed"      # spesifik service SSH
```

### Contoh log SSH beneran (dari praktik)

Sep 21 23:37:45 kali sshd-session[17377]: Failed password for kali from ::1 port 38308 ssh2
Sep 21 23:40:38 kali sshd-session[18984]: Accepted password for kali from ::1 port 60006 ssh2

Format: `[timestamp] [hostname] [service+PID]: [status] for [user] from [IP] port [port] [protokol]`

### Setup SSH server (kalau belum aktif)
```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh
```

## Insight Praktik
- 3x failed login dalam waktu singkat dari IP yang sama = pola dasar **brute force**
- `from ::1` = localhost (diri sendiri) → normal kalau kamu sendiri yang tes
- Kalau grep hasilnya kosong, coba keyword lebih pendek dulu — jangan langsung asumsi "ga ada kejadian"
