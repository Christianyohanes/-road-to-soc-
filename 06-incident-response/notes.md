# Incident Response (IR) Flow

## 6 Tahap Standar IR (NIST Framework)
| Tahap | Artinya | Contoh aktivitas |
|---|---|---|
| 1. Preparation | Persiapan sebelum insiden terjadi | Bikin SOP, training tim, pastiin tools (SIEM) udah siap |
| 2. Detection & Analysis | Deteksi & analisis awal insiden | SIEM kasih alert → SOC L1 triage → tentuin True/False Positive |
| 3. Containment | Isolasi biar ga makin nyebar | Block IP di firewall, putus koneksi device yang kena, disable akun yang dicurigai |
| 4. Eradication | Hilangin akar masalahnya | Hapus malware, patch kerentanan yang dieksploitasi |
| 5. Recovery | Balikin sistem ke normal | Restore dari backup, aktifin lagi service yang sempet dimatiin |
| 6. Lessons Learned | Evaluasi setelah kasus selesai | Post-mortem meeting, update SOP biar kejadian serupa ga kejadian lagi |

## Peran SOC L1 di tiap tahap
| Tahap | Peran L1 |
|---|---|
| Detection & Analysis | Fokus utama L1 — triage alert, tentuin severity, kumpulin bukti awal |
| Containment | L1 kasih rekomendasi; eksekusi block/isolasi biasanya butuh approval L2/L3 |
| Eradication, Recovery | Di luar scope L1, diambil alih L2/L3/Incident Responder |
| Lessons Learned | L1 bisa kontribusi insight dari sisi apa yang pertama kali terlihat di alert |

## Contoh Alur Lengkap

1. SIEM generate alert: "5x failed SSH login dari IP 203.0.113.5"
2. [Detection] SOC L1 buka alert, cek journalctl/auth.log detail-nya
3. [Analysis] Mapping ke MITRE ATT&CK → Credential Access, T1110 (Brute Force)
4. Cek CIA Triad yang terancam → Confidentiality (kalau berhasil login)
5. [Containment] Rekomendasi block IP di firewall (eksekusi butuh approval)
6. [Eskalasi] Kirim laporan ke L2 dengan bukti lengkap: IP, waktu, jumlah percobaan, technique
7. [Recovery] (kalau perlu) reset password akun yang jadi target
8. [Lessons Learned] Rekomendasi: aktifin account lockout policy


## Insight
- L1 paling banyak kerja di 2 tahap awal (Detection & Analysis), bagian kecil di awal Containment (rekomendasi, bukan eksekusi)
- Kerangka 6 tahap ini standar yang hampir pasti muncul di pertanyaan interview kerja SOC
