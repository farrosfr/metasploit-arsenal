# Metasploit Offensive Security Arsenal

> "May the eyes of cowards never sleep." - Khalid bin Walid

Repositori ini adalah koleksi pribadi skrip, modul kustom, *cheatsheets*, dan *walkthrough* terkait Metasploit Framework. Dikelola oleh **FarrosFR**, repositori ini bertujuan untuk menjadi gudang pengetahuan praktis dalam dunia *offensive security* dan *penetration testing*.

<br>

<details>
<summary>⚠️ Disclaimer Penting</summary>
<br>
Semua informasi, skrip, dan teknik dalam repositori ini ditujukan HANYA UNTUK TUJUAN PENDIDIKAN DAN RISET KEAMANAN SIBER SECARA ETIS. Penggunaan alat dan teknik ini untuk menyerang target yang tidak Anda miliki izin eksplisitnya adalah ilegal. Penulis (FarrosFR) tidak bertanggung jawab atas penyalahgunaan informasi di dalam repositori ini. Gunakan dengan risiko Anda sendiri dan selalu bertindak secara profesional dan etis.
</details>

---

##  Daftar Isi

1.  [Tentang Repositori Ini](#tentang-repositori-ini)
2.  [Struktur Direktori](#struktur-direktori)
3.  [Contoh Use Case & Implementasi](#contoh-use-case--implementasi)
    * [Resource Script: Listener Otomatis](#resource-script-listener-otomatis)
    * [Cheatsheet: Payloads](#cheatsheet-payloads)
    * [Walkthrough: Eksploitasi MS17-010 (EternalBlue)](#walkthrough-eksploitasi-ms17-010-eternalblue)
4.  [Cara Menggunakan Repositori Ini](#cara-menggunakan-repositori-ini)
5.  [Kontribusi](#kontribusi)
6.  [Lisensi](#lisensi)

---

## Tentang Repositori Ini

Repositori ini berfungsi sebagai:
* **Tempat Penyimpanan Modul Kustom**: Menyimpan modul `exploit`, `auxiliary`, atau `post` yang dibuat atau dimodifikasi.
* **Koleksi Resource Scripts (.rc)**: Otomatisasi tugas-tugas berulang di `msfconsole`.
* **Pusat Cheatsheets**: Kumpulan cepat perintah, payloads, dan teknik penting.
* **Dokumentasi Walkthrough**: Catatan langkah-demi-langkah dari skenario pentesting nyata atau dari platform lab seperti Hack The Box & TryHackMe.

## Struktur Direktori

```

/
├── custom\_modules/     \# Untuk modul Metasploit kustom Anda
├── resource\_scripts/   \# Skrip .rc untuk otomatisasi msfconsole
├── cheatsheets/        \# Referensi cepat (payloads, commands, dll)
└── walkthroughs/       \# Panduan langkah-demi-langkah untuk skenario tertentu

````

## Contoh Use Case & Implementasi

Berikut adalah beberapa contoh praktis yang ada di repositori ini.

### Resource Script: Listener Otomatis

Seringkali kita perlu menyiapkan *listener* `multi/handler` dengan cepat. Skrip `.rc` ini mengotomatiskannya.

**File**: [`resource_scripts/multi_handler_listener.rc`](resource_scripts/multi_handler_listener.rc)

**Implementasi**:
Jalankan dari terminal Anda (bukan di dalam msfconsole):
```bash
msfconsole -r resource_scripts/multi_handler_listener.rc
````

Ini akan langsung memulai listener dengan konfigurasi yang telah ditentukan di dalam file.

### Cheatsheet: Payloads

Referensi cepat untuk berbagai jenis payload yang umum digunakan di Metasploit, dikategorikan berdasarkan sistem operasi target.

**File**: [`cheatsheets/payload_cheatsheet.md`](https://www.google.com/search?q=cheatsheets/payload_cheatsheet.md)

**Contoh Cuplikan**:
| Platform | Jenis Payload | Contoh |
| :--- | :--- | :--- |
| Windows | Staged Reverse TCP (Meterpreter) | `windows/meterpreter/reverse_tcp` |
| Linux | Stageless Reverse TCP (Shell) | `linux/x64/shell_reverse_tcp` |

### Walkthrough: Eksploitasi MS17-010 (EternalBlue)

Panduan langkah-demi-langkah untuk melakukan eksploitasi pada kerentanan MS17-010, salah satu kerentanan paling terkenal yang menargetkan protokol SMB di Windows.

**File**: [`walkthroughs/case_ms17-010_eternalblue.md`](https://www.google.com/search?q=walkthroughs/case_ms17-010_eternalblue.md)

Walkthrough ini mencakup:

1.  Identifikasi target.
2.  Pemilihan modul exploit di Metasploit.
3.  Konfigurasi `RHOSTS`, `LHOST`, dan `PAYLOAD`.
4.  Eksekusi exploit dan mendapatkan sesi Meterpreter.

## Cara Menggunakan Repositori Ini

1.  **Clone Repositori**

    ```bash
    git clone [https://github.com/FarrosFR/metasploit-arsenal.git](https://github.com/FarrosFR/metasploit-arsenal.git)
    cd metasploit-arsenal
    ```

2.  **Menambahkan Modul Kustom**
    Salin modul `.rb` Anda ke direktori yang sesuai di dalam `custom_modules/`. Di dalam `msfconsole`, gunakan perintah `loadpath` untuk memuatnya:

    ```
    msf > loadpath /path/to/your/repo/metasploit-arsenal/custom_modules
    msf > reload_all
    ```

## Kontribusi

Saat ini, repositori ini dikelola untuk keperluan pribadi. Namun, jika Anda menemukan kesalahan atau memiliki saran, silakan buka *Issue*.

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](https://www.google.com/search?q=LICENSE).

```
