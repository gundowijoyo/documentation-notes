Berikut adalah panduan untuk menginstal **Perl** di 4 sistem operasi: **Windows**, **Linux**, **macOS**, dan **Termux** (Android). Saya juga akan memberikan contoh kode untuk pengujian setelah instalasi.

---

### 1. **Instalasi Perl di Windows**

#### Langkah-langkah Instalasi:
1. **Download Perl:**
   - Kunjungi halaman unduhan **Strawberry Perl** di [https://strawberryperl.com/](https://strawberryperl.com/).
   - Pilih versi terbaru Perl (misalnya `strawberry-perl-5.x.x.x-64bit.msi` untuk sistem 64-bit).

2. **Jalankan Installer:**
   - Klik dua kali file installer yang telah diunduh dan ikuti petunjuk untuk menginstal.
   - Pastikan untuk mencentang opsi **"Add Perl to PATH"** agar dapat mengakses Perl dari Command Prompt.

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, buka **Command Prompt** dan ketik:
     ```bash
     perl --version
     ```

   Output yang diharapkan:
   ```
   This is perl 5.x.x (xxxx) built for MSWin32-x64-multi-thread
   ```

#### Contoh Kode Perl:
1. Buat file **`hello.pl`** dengan isi berikut:
   ```perl
   # hello.pl
   print "Hello, World!\n";
   ```

2. **Menjalankan Kode:**
   - Buka **Command Prompt** dan arahkan ke direktori tempat file **`hello.pl`** berada.
   - Jalankan perintah:
     ```bash
     perl hello.pl
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 2. **Instalasi Perl di Linux (Debian/Ubuntu)**

#### Langkah-langkah Instalasi:
1. **Perbarui Paket Sistem:**
   - Buka terminal dan jalankan perintah untuk memperbarui repositori paket:
     ```bash
     sudo apt update && sudo apt upgrade
     ```

2. **Instal Perl:**
   - Instal Perl dengan perintah berikut:
     ```bash
     sudo apt install perl
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Perl dengan perintah:
     ```bash
     perl --version
     ```

   Output yang diharapkan:
   ```
   This is perl 5.x.x
   ```

#### Contoh Kode Perl:
1. Buat file **`hello.pl`** dengan isi berikut:
   ```perl
   # hello.pl
   print "Hello, World!\n";
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan arahkan ke direktori tempat file **`hello.pl`** berada.
   - Jalankan perintah:
     ```bash
     perl hello.pl
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 3. **Instalasi Perl di macOS**

#### Langkah-langkah Instalasi:
1. **Instalasi menggunakan Homebrew:**
   - Jika belum menginstal Homebrew, jalankan perintah berikut di terminal:
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```

2. **Instal Perl:**
   - Setelah Homebrew terinstal, instal Perl dengan perintah berikut:
     ```bash
     brew install perl
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Perl dengan perintah:
     ```bash
     perl --version
     ```

   Output yang diharapkan:
   ```
   This is perl 5.x.x
   ```

#### Contoh Kode Perl:
1. Buat file **`hello.pl`** dengan isi berikut:
   ```perl
   # hello.pl
   print "Hello, World!\n";
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan arahkan ke direktori tempat file **`hello.pl`** berada.
   - Jalankan perintah:
     ```bash
     perl hello.pl
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 4. **Instalasi Perl di Termux (Android)**

#### Langkah-langkah Instalasi:
1. **Perbarui Paket Termux:**
   - Buka aplikasi Termux dan jalankan perintah berikut untuk memperbarui repositori paket:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal Perl:**
   - Instal Perl dengan perintah berikut:
     ```bash
     pkg install perl
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Perl dengan perintah:
     ```bash
     perl --version
     ```

   Output yang diharapkan:
   ```
   This is perl 5.x.x
   ```

#### Contoh Kode Perl:
1. Buat file **`hello.pl`** dengan isi berikut:
   ```perl
   # hello.pl
   print "Hello, World!\n";
   ```

2. **Menjalankan Kode:**
   - Buka Termux dan arahkan ke direktori tempat file **`hello.pl`** berada.
   - Jalankan perintah:
     ```bash
     perl hello.pl
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### Kesimpulan:

- **Windows:** Gunakan **Strawberry Perl** untuk instalasi Perl di Windows.
- **Linux (Debian/Ubuntu):** Gunakan `sudo apt install perl` untuk menginstal Perl.
- **macOS:** Gunakan **Homebrew** (`brew install perl`) untuk menginstal Perl.
- **Termux (Android):** Gunakan `pkg install perl` untuk menginstal Perl di Termux.

Dengan mengikuti langkah-langkah ini, Anda akan siap untuk menjalankan dan mengembangkan skrip Perl di setiap sistem operasi.
