# Networking Fundamentals

## Model Dasar
Data dikirim berlapis-lapis (TCP/IP model): Application, Transport, Internet, Network Access.

## IP Address & Subnetting
- IP address = alamat device di jaringan (contoh: 192.168.1.10)
- IP publik vs privat, subnet mask, CIDR (/24, /16, dst)
- Cek IP sendiri: `ipconfig` (Windows) / `ifconfig` atau `ip a` (Linux)

## TCP vs UDP & Port
| Konsep | Penjelasan |
|---|---|
| TCP | Reliable, ada handshake (SYN, SYN-ACK, ACK), lebih lambat tapi terjamin sampai |
| UDP | Ga ada handshake, cepat tapi ga jamin sampai |
| Port | "Nomor pintu" di IP address. Contoh: 80 (HTTP), 443 (HTTPS), 22 (SSH) |

## DNS
Nerjemahin domain (google.com) jadi IP address. Test: `nslookup google.com`

## Cisco / Router & Switch
| Istilah | Penjelasan |
|   ---   |     ---    |
| Router | Nyambungin beda network (LAN ke internet) |
| Switch | Nyambungin device dalam satu network lokal (LAN) |
| VLAN | Sekat virtual dalam satu switch fisik, misahin broadcast domain |
| Subnetting | Bagi network besar jadi kecil (/24 = 256 IP, /25 = 128 IP) |
| Default Gateway | IP router jadi "pintu keluar" ke network lain |

### Command Cisco penting
- `show ip route` — lihat tabel routing
- `show interfaces` — status tiap port (up/down, IP)
- `show vlan brief` — lihat VLAN yang udah dikonfigurasi
- `ping` — test koneksi ke IP tertentu
- `traceroute` — lihat jalur/hop paket ke tujuan

### Cisco CLI Mode
| Mode | Command masuk | Prompt |
|---   |---            |---      |
| User EXEC | (default) | `Switch>` |
| Privileged EXEC | `enable` | `Switch#` |
| Global Config | `configure terminal` (`conf t`) | `Switch(config)#` |
| Interface Config | `interface <nama>` | `Switch(config-if)#` |

### Konfigurasi VLAN dasar

enable
configure terminal
vlan 10
name HR
exit
interface fa0/1
switchport mode access
switchport access vlan 10
exit


## Insight Praktik
- Dua device beda subnet **ga bisa** langsung ping tanpa router
- Dua device satu subnet tapi **beda VLAN** juga ga bisa ping — VLAN motong komunikasi di level switch, lebih "kuat" dari subnet
- Switch nyimpen MAC Address Table (`show mac address-table`) buat inget device mana nyambung ke port mana

## Command Linux/Networking berguna
- `ss -tlnp` — lihat port TCP yang listening (t=TCP, l=listening, n=numeric, p=proses)
