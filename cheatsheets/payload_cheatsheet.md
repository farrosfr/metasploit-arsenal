---

#### `cheatsheets/payload_cheatsheet.md`

Cheatsheet payload dalam format Markdown yang mudah dibaca.

# Metasploit Payload Cheatsheet

Referensi cepat untuk payload yang umum digunakan.

## Windows Payloads

| Jenis Payload | Contoh Path | Deskripsi |
| :--- | :--- | :--- |
| **Staged Meterpreter (TCP)** | `windows/meterpreter/reverse_tcp` | Payload kecil (stager) yang akan men-download sisa payload Meterpreter. Sangat umum digunakan. |
| **Stageless Meterpreter (TCP)** | `windows/meterpreter_reverse_tcp` | Mengirim seluruh payload Meterpreter dalam satu koneksi. Ukuran lebih besar, tapi lebih stabil. |
| **Staged Meterpreter (HTTPS)** | `windows/meterpreter/reverse_https` | Sama seperti reverse_tcp, tapi komunikasi dibungkus dalam SSL/TLS. Baik untuk menghindari deteksi IDS/IPS. |
| **Stageless Shell (TCP)** | `windows/shell_reverse_tcp` | Memberikan command prompt (cmd.exe) biasa. Stageless. |

## Linux Payloads

| Jenis Payload | Contoh Path | Deskripsi |
| :--- | :--- | :--- |
| **Staged Meterpreter (TCP, 64-bit)** | `linux/x64/meterpreter/reverse_tcp` | Meterpreter stager untuk sistem Linux 64-bit. |
| **Stageless Meterpreter (TCP, 64-bit)** | `linux/x64/meterpreter_reverse_tcp` | Versi stageless dari payload di atas. |
| **Stageless Shell (TCP, 64-bit)** | `linux/x64/shell_reverse_tcp` | Memberikan shell `/bin/bash` atau `/bin/sh` pada sistem 64-bit. |
| **Python Shell (Generic)** | `python/meterpreter_reverse_http` | Payload berbasis Python, sangat berguna jika target memiliki Python terinstall. |

## Web / Scripting Payloads

| Jenis Payload | Contoh Path | Deskripsi |
| :--- | :--- | :--- |
| **PHP Meterpreter (Staged)** | `php/meterpreter/reverse_tcp` | Payload untuk dieksekusi di server web yang menjalankan PHP. |
| **Java JSP Meterpreter (Staged)** | `java/jsp_shell_reverse_tcp` | Memberikan shell via halaman JSP yang di-upload ke server Java (Tomcat, dll). |
| **NodeJS Shell (Stageless)** | `nodejs/shell_reverse_tcp` | Reverse shell untuk aplikasi berbasis NodeJS. |

