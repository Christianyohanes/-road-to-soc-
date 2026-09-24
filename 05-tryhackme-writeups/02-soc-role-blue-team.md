# TryHackMe: SOC Role in Blue Team

**Path:** SOC Level 1 > Blue Team Introduction
**Status:** Completed ✅
**Link:** [tryhackme.com/room/soc-role-blue-team](https://tryhackme.com/room/soc-role-blue-team)

## Struktur Keamanan Perusahaan
Prioritas keamanan tiap perusahaan beda-beda (firma hukum fokus privasi dokumen, pabrik fokus availability produksi, RS fokus keamanan data pasien). Struktur umumnya:

CEO → CISO (Chief Information Security Officer) → 3 departemen besar:
- **Red Team** — offensive security, pentester, ethical hacker
- **GRC Team** — kepatuhan & regulasi (misal PCI DSS)
- **Blue Team** — defensive security (SOC, engineer, incident responder)

## Struktur Blue Team

### 1. SOC (Security Operations Center) — titik awal karir saya
| Role | Tugas |
|---|---|
| L1 Analyst | Triage alert, eskalasi kasus kompleks ke L2 |
| L2 Analyst | Investigasi serangan yang lebih advanced |
| Engineer | Konfigurasi tools security (EDR, SIEM) |
| Manager | Mengelola tim SOC secara keseluruhan |

### 2. CIRT/CSIRT/CERT — "pemadam kebakaran" cyber
Dipanggil on-demand kalau SOC ga sanggup handle atau insiden lepas kendali. Kerjaannya: deep forensics, identifikasi ancaman tersembunyi, recovery sistem yang breach.

### 3. Role Spesialis (butuh pengalaman luas dulu di SOC/IT)
- Digital Forensics Analyst — analisis disk & memory
- Threat Intelligence Analyst — riset kelompok ancaman
- AppSec Engineer — keamanan software development lifecycle
- AI Researcher — riset ancaman berbasis AI

## Internal SOC vs MSSP
| Aspek | Internal SOC | MSSP (outsourced) |
|---|---|---|
| Contoh | Kerja di SOC 1 bank | Kerja di MSSP yang handle 60 client sekaligus |
| Ritme kerja | Lebih santai, ga terlalu ngebut | Shift mulai dari antrian alert yang urgent |
| Tools | Cuma beberapa tools, tapi harus dikuasai dalam-dalam | Puluhan tools berbeda-beda |
| Exposure insiden | Lebih jarang ketemu insiden besar | Lebih sering, belajar lebih cepat |

## Career Path SOC L1
1. Bangun skill dasar SOC (+ skill pendukung: red teaming, IT umum)
2. Proaktif — ikut CTF, update cyber news, pertimbangkan sertifikasi **SAL1**
3. Siapin interview, paham beda internal SOC vs MSSP, apply kerja
4. Setelah beberapa tahun pengalaman, lanjut ke role lebih senior (L2, Engineer, CIRT, atau jalur manajerial ke CISO)

## Insight Utama
- SOC L1 itu **bukan jalur buntu** — banyak percabangan karir setelahnya (L2, Engineer, CIRT, bahkan CISO)
- **MSSP** bisa jadi entry point yang bagus buat cepat dapat exposure banyak insiden, walau lebih high-pressure
- Sertifikasi **SAL1** (Security Analyst Level 1) worth dipertimbangkan sebagai next step setelah portofolio dasar
