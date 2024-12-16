Tentu! Berikut adalah panduan lengkap untuk **instalasi Ruby** di empat platform yang mencakup contoh kode dan cara mengeksekusinya setelah instalasi.

---

### 1. **Instalasi Ruby di Windows**

#### Langkah-langkah Instalasi:
1. **Download dan Instal Ruby**  
   Ikuti langkah-langkah pada bagian **Instalasi Ruby di Windows** di atas, yaitu mengunduh **RubyInstaller** dan menginstalnya.

2. **Verifikasi Instalasi:**
   Setelah instalasi, buka **Command Prompt** dan ketik perintah:
   ```bash
   ruby --version
   ```

   Anda seharusnya mendapatkan output seperti:
   ```
   ruby 3.x.x (202x-xx-xx) [x64-mingw32]
   ```

#### Contoh Kode Ruby:
1. Buat file **`hello.rb`** dengan isi sebagai berikut:
   ```ruby
   # hello.rb
   puts "Hello, World!"
   ```

2. **Menjalankan Kode:**
   - Buka **Command Prompt**.
   - Navigasi ke direktori tempat file **`hello.rb`** berada, lalu jalankan:
     ```bash
     ruby hello.rb
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 2. **Instalasi Ruby di Linux (Debian/Ubuntu)**

#### Langkah-langkah Instalasi:
1. **Perbarui dan Instal Ruby:**
   Ikuti langkah-langkah pada bagian **Instalasi Ruby di Linux** di atas, yaitu menggunakan perintah:
   ```bash
   sudo apt update && sudo apt upgrade
   sudo apt install ruby-full
   ```

2. **Verifikasi Instalasi:**
   Setelah instalasi, periksa versi Ruby dengan perintah:
   ```bash
   ruby --version
   ```

   Anda seharusnya mendapatkan output seperti:
   ```
   ruby 3.x.x
   ```

#### Contoh Kode Ruby:
1. Buat file **`hello.rb`** dengan isi sebagai berikut:
   ```ruby
   # hello.rb
   puts "Hello, World!"
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan navigasi ke direktori tempat file **`hello.rb`** berada.
   - Jalankan perintah:
     ```bash
     ruby hello.rb
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 3. **Instalasi Ruby di macOS**

#### Langkah-langkah Instalasi:
1. **Instalasi Homebrew dan Ruby:**
   Ikuti langkah-langkah pada bagian **Instalasi Ruby di macOS** di atas, yaitu menggunakan perintah:
   ```bash
   brew install ruby
   ```

2. **Verifikasi Instalasi:**
   Setelah instalasi, periksa versi Ruby dengan perintah:
   ```bash
   ruby --version
   ```

   Anda seharusnya mendapatkan output seperti:
   ```
   ruby 3.x.x
   ```

#### Contoh Kode Ruby:
1. Buat file **`hello.rb`** dengan isi sebagai berikut:
   ```ruby
   # hello.rb
   puts "Hello, World!"
   ```

2. **Menjalankan Kode:**
   - Buka terminal dan navigasi ke direktori tempat file **`hello.rb`** berada.
   - Jalankan perintah:
     ```bash
     ruby hello.rb
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### 4. **Instalasi Ruby di Termux (Android)**

#### Langkah-langkah Instalasi:
1. **Perbarui dan Instal Ruby:**
   Ikuti langkah-langkah pada bagian **Instalasi Ruby di Termux** di atas, yaitu dengan menggunakan perintah:
   ```bash
   pkg update && pkg upgrade
   pkg install ruby
   ```

2. **Verifikasi Instalasi:**
   Setelah instalasi, periksa versi Ruby dengan perintah:
   ```bash
   ruby --version
   ```

   Anda seharusnya mendapatkan output seperti:
   ```
   ruby 3.x.x
   ```

#### Contoh Kode Ruby:
1. Buat file **`hello.rb`** dengan isi sebagai berikut:
   ```ruby
   # hello.rb
   puts "Hello, World!"
   ```

2. **Menjalankan Kode:**
   - Buka Termux dan navigasi ke direktori tempat file **`hello.rb`** berada.
   - Jalankan perintah:
     ```bash
     ruby hello.rb
     ```

3. **Output yang Diharapkan:**
   ```
   Hello, World!
   ```

---

### Kesimpulan:
- Setelah mengikuti langkah-langkah di atas, Anda dapat menginstal Ruby dan menguji instalasi dengan menjalankan **contoh kode** yang sederhana.
- Kode Ruby yang digunakan (`puts "Hello, World!"`) hanya untuk menampilkan pesan ke layar, yang sangat berguna untuk memastikan bahwa Ruby telah terinstal dengan benar di sistem Anda.

Jika ada langkah yang kurang jelas atau Anda mengalami kesulitan dalam instalasi, jangan ragu untuk bertanya lebih lanjut!
