# TryHackMe: Junior Security Analyst Intro

**Path:** SOC Level 1 > Blue Team Introduction
**Status:** Completed ✅
**Link:** [tryhackme.com/room/jrsecanalystintrouxo](https://tryhackme.com/room/jrsecanalystintrouxo)

## Ringkasan
Room pengantar yang mensimulasikan hari kerja seorang SOC Analyst (Junior/L1) — mulai dari struktur tim SOC, tanggung jawab harian, sampai simulasi menangani alert pertama di dashboard.

## Peran dalam Tim SOC
| Role | Fungsi |
|---|---|
| SOC Analyst (L1) — posisi saya | Monitoring & investigasi alert harian |
| Senior Analyst | Handle kasus kompleks setelah L1 lakukan analisis awal |
| SOC Engineer | Maintain tools security & konfigurasi alert (bukan analisis langsung) |
| SOC Manager | Laporan ke management, koordinasi tim |
| Incident Responder | Turun tangan khusus pas ada insiden besar (misal ransomware) |

## Insight Utama
- Kerjaan SOC L1 itu volume-heavy — banyak "tiket" (alert) yang harus di-*resolve* tepat waktu dalam satu shift
- SOC itu kerja tim berlapis — L1 investigasi awal, eskalasi ke Senior Analyst kalau kompleks, bukan diselesaikan sendirian
- Salah satu alur kerja dasar: **deteksi alert → identifikasi indikator (misal malicious IP) → eskalasi ke Senior Analyst → mitigasi (block di firewall) → verifikasi hasil**

## Simulasi Lab: Handling Malicious IP Alert
Berhasil identifikasi IP mencurigakan dari alert dashboard, eskalasi ke Senior Analyst (Will Griffin) sesuai SOP, dan lakukan mitigasi block di firewall.
