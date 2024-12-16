Berikut adalah panduan untuk menginstal **PHP** di 4 sistem operasi: **Windows**, **Linux**, **macOS**, dan **Termux** (Android). Saya juga akan memberikan contoh kode PHP untuk pengujian setelah instalasi.

---

### 1. **Instalasi PHP di Windows**

#### Langkah-langkah Instalasi:
1. **Download PHP:**
   - Kunjungi halaman unduhan **PHP untuk Windows** di [https://windows.php.net/download](https://windows.php.net/download).
   - Pilih versi **Thread Safe** (untuk penggunaan di server) atau **Non Thread Safe** (untuk penggunaan di CLI).
   - Pilih versi yang sesuai dengan sistem Anda (misalnya `x64` untuk 64-bit).

2. **Ekstrak File:**
   - Setelah mengunduh file ZIP, ekstrak ke folder pilihan Anda, misalnya `C:\php`.

3. **Set Path:**
   - Tambahkan direktori PHP ke dalam **Environment Variables** di **Path** untuk bisa menjalankan PHP dari Command Prompt.
     - Cari **Environment Variables** di Windows, lalu edit **Path** di bagian **System variables** dan tambahkan path ke folder tempat Anda mengekstrak PHP (misalnya `C:\php`).

4. **Verifikasi Instalasi:**
   - Setelah pengaturan selesai, buka **Command Prompt** dan ketik:
     ```bash
     php -v
     ```

   Output yang diharapkan:
   ```
   PHP 7.x.x (cli) (built: xxxx) (NTS Windows)
   ```

#### Contoh Kode PHP:
1. Buat file **`hello.php`** dengan isi berikut:
   ```php
   <?php
   echo "Hello, World!";
   ?>
   ```

2. **Menjalankan Kode:**
   - Buka **Command Prompt** dan arahkan ke direktori tempat file **`hello.php`** berada.
   - Jalankan perintah:
     ```bash
     php hello.php
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 2. **Instalasi PHP di Linux (Debian/Ubuntu)**

#### Langkah-langkah Instalasi:
1. **Perbarui Paket Sistem:**
   - Buka terminal dan jalankan perintah untuk memperbarui repositori paket:
     ```bash
     sudo apt update && sudo apt upgrade
     ```

2. **Instal PHP:**
   - Instal PHP dan beberapa paket terkait (seperti `php-cli` untuk penggunaan CLI):
     ```bash
     sudo apt install php php-cli
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi PHP dengan perintah:
     ```bash
     php -v
     ```

   Output yang diharapkan:
   ```
   PHP 7.x.x (cli) (built: xxxx)
   ```

#### Contoh Kode PHP:
1. Buat file **`hello.php`** dengan isi berikut:
   ```php
   <?php
   echo "Hello, World!";
   ?>
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan arahkan ke direktori tempat file **`hello.php`** berada.
   - Jalankan perintah:
     ```bash
     php hello.php
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 3. **Instalasi PHP di macOS**

#### Langkah-langkah Instalasi:
1. **Instalasi menggunakan Homebrew:**
   - Jika Anda belum menginstal **Homebrew**, jalankan perintah berikut di terminal:
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```

2. **Instal PHP:**
   - Setelah Homebrew terinstal, instal PHP dengan perintah berikut:
     ```bash
     brew install php
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi PHP dengan perintah:
     ```bash
     php -v
     ```

   Output yang diharapkan:
   ```
   PHP 7.x.x (cli) (built: xxxx)
   ```

#### Contoh Kode PHP:
1. Buat file **`hello.php`** dengan isi berikut:
   ```php
   <?php
   echo "Hello, World!";
   ?>
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan arahkan ke direktori tempat file **`hello.php`** berada.
   - Jalankan perintah:
     ```bash
     php hello.php
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 4. **Instalasi PHP di Termux (Android)**

#### Langkah-langkah Instalasi:
1. **Perbarui Paket Termux:**
   - Buka aplikasi **Termux** dan jalankan perintah untuk memperbarui repositori paket:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal PHP:**
   - Instal PHP dengan perintah berikut:
     ```bash
     pkg install php
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi PHP dengan perintah:
     ```bash
     php -v
     ```

   Output yang diharapkan:
   ```
   PHP 7.x.x (cli) (built: xxxx)
   ```

#### Contoh Kode PHP:
1. Buat file **`hello.php`** dengan isi berikut:
   ```php
   <?php
   echo "Hello, World!";
   ?>
   ```

2. **Menjalankan Kode:**
   - Buka **Termux** dan arahkan ke direktori tempat file **`hello.php`** berada.
   - Jalankan perintah:
     ```bash
     php hello.php
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### Kesimpulan:

- **Windows:** Gunakan **PHP for Windows** yang diunduh dari situs resmi PHP, dan pastikan untuk menambahkan path PHP ke dalam **Environment Variables**.
- **Linux (Debian/Ubuntu):** Gunakan perintah `sudo apt install php php-cli` untuk menginstal PHP.
- **macOS:** Gunakan **Homebrew** untuk menginstal PHP dengan perintah `brew install php`.
- **Termux (Android):** Gunakan perintah `pkg install php` untuk menginstal PHP di Termux.

Dengan mengikuti langkah-langkah di atas, Anda dapat menginstal PHP di berbagai platform dan memverifikasi instalasi dengan contoh kode sederhana.
