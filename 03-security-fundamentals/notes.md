# Security Fundamentals

## CIA Triad
| Prinsip | Artinya |
|---|---|
| Confidentiality | Data cuma boleh diakses pihak yang berhak |
| Integrity | Data ga boleh diubah sembarangan, harus tetep akurat |
| Availability | Sistem/data harus bisa diakses kapan pun dibutuhin |

### Cara cepat identifikasi CIA
1. Ada yang **lihat/akses** data yang harusnya ga boleh? → Confidentiality
2. Ada yang **ubah/rusak** data tanpa izin? → Integrity
3. Ada yang bikin sistem/data jadi **ga bisa dipakai**? → Availability

Satu kejadian bisa kena lebih dari 1 prinsip sekaligus.

### Contoh serangan → CIA yang kena
| Serangan | CIA yang kena |
|---|---|
| Data breach | Confidentiality |
| DDoS | Availability |
| Ransomware | Availability + Confidentiality (kalau double extortion) |
| Man-in-the-Middle | Confidentiality (intip) / Integrity (ubah data) |
| Defacement website | Integrity |

## Jenis-Jenis Serangan
| Serangan | Cara kerja |
|---|---|
| Malware (Virus/Worm/Trojan) | Software jahat, nyusup & rusak sistem |
| Ransomware | Enkripsi data korban, minta tebusan |
| Phishing | Nipu user via email/pesan palsu biar kasih kredensial |
| Spear phishing | Phishing dengan target spesifik + personalisasi |
| Brute Force | Coba banyak kombinasi password sampai ketemu |
| Lateral Movement | Attacker gerak dari 1 device ke device lain dalam network |
| Privilege Escalation | Attacker naikin akses dari low-level ke admin/root |
| DDoS | Banjirin traffic server biar down |
| SQL Injection | Nyelipin command database jahat lewat form input website |

## MITRE ATT&CK
Framework standar industri buat kategoriin teknik & taktik attacker. Contoh: banyak failed login dari IP sama = **Credential Access → Brute Force (T1110)**.

Kenapa penting: laporan ke L2 jadi lebih profesional & konsisten — bukan cuma "kayaknya ada yang aneh", tapi "ini teknik T1110".

## Alur Respons SOC L1 (contoh: alert cross-VLAN traffic)
1. **Triage** — cek source/destination IP & VLAN, jam kejadian, protokol/port
2. **Validasi** — cek apakah ada exception yang sah (misal IT lagi maintenance)
3. **Tentukan** — False Positive (tutup ticket) atau anomali (lanjut investigasi)
4. **Investigasi** — cek riwayat device, pattern berulang, user yang login
5. **Eskalasi ke L2** — kasih bukti lengkap (IP, waktu, port, pattern), bukan cuma "ada yang aneh"

⚠️ SOC L1 tugasnya **triage & investigasi**, BUKAN eksekusi/block sendiri.

## Struktur Halaman MITRE ATT&CK (per technique)
- **ID** — kode referensi (misal T1110)
- **Sub-techniques** — varian lebih spesifik dari teknik utama
- **Description** — penjelasan umum
- **Procedure Examples** — bukti grup/malware nyata yang pernah pakai
- **Mitigations** — cara mencegah
- **Detection** — cara SOC analyst mendeteksi (paling relevan buat kerjaan sehari-hari)

### Contoh: Brute Force (T1110)
Sub-techniques: Password Guessing (T1110.001), Password Cracking (T1110.002), Password Spraying (T1110.003), Credential Stuffing (T1110.004)
