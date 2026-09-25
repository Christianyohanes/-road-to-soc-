# Log Analysis & SIEM — Wazuh

## Arsitektur Wazuh
| Komponen | Fungsi |
|---|---|
| Wazuh Manager | "Otak" — nerima, olah, simpan log dari semua Agent |
| Wazuh Agent | "Pengirim" — di-install di device yang dipantau, kirim log ke Manager |
| Wazuh Indexer | Database penyimpanan log (berbasis OpenSearch) |
| Filebeat | Ngirim data dari Manager ke Indexer |
| Dashboard | Visualisasi & interface buat analyst |

## Cara akses
`https://<IP-manager>:443` — login pakai `admin` + password yang di-generate saat instalasi

## Pengalaman Troubleshooting (real-world skill)
- Disk space penuh → cek dengan `df -h`, `du -h`, bersihin cache/docker
- Partition resize: `growpart`, `resize2fs`, hapus partition swap yang ngeblok ruang kosong
- RAM kritis → bikin swapfile (`fallocate`, `mkswap`, `swapon`) sebagai buffer
- systemd timeout → override service config via `/etc/systemd/system/<service>.service.d/override.conf`
- Lock file issue → proses lama yang "nyangkut" bisa nge-block restart service baru

## Insight
- Stack SIEM (Indexer + Manager + Dashboard) itu berat — butuh resource jauh lebih besar dari sekadar baca log manual. Ini kenapa perusahaan biasanya alokasiin server khusus buat SIEM, bukan jalan bareng aplikasi lain.
- Masalah performa infrastruktur (RAM, disk, timeout) itu sama pentingnya buat dipahami SOC analyst — bukan cuma paham cara baca alert-nya doang.
