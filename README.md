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

├── custom_modules/     # Untuk modul Metasploit kustom Anda
├── resource_scripts/   # Skrip .rc untuk otomatisasi msfconsole
├── cheatsheets/        # Referensi cepat (payloads, commands, dll)
└── walkthroughs/       # Panduan langkah-demi-langkah untuk skenario tertentu

## Contoh Use Case & Implementasi

Berikut adalah beberapa contoh praktis yang ada di repositori ini.

### Resource Script: Listener Otomatis

Seringkali kita perlu menyiapkan *listener* `multi/handler` dengan cepat. Skrip `.rc` ini mengotomatiskannya.

**File**: [`resource_scripts/multi_handler_listener.rc`](resource_scripts/multi_handler_listener.rc)

**Implementasi**:
Jalankan dari terminal Anda (bukan di dalam msfconsole):
```bash
msfconsole -r resource_scripts/multi_handler_listener.rc
```
Ini akan langsung memulai listener dengan konfigurasi yang telah ditentukan di dalam file.

