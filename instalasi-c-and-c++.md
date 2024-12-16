Berikut adalah panduan instalasi **C** dan **C++** di 4 platform yang telah disebutkan: **Windows**, **Linux**, **macOS**, dan **Termux** (Android). Di setiap platform, kita akan menginstal **GNU Compiler Collection (GCC)**, yang mencakup kompiler untuk C dan C++.

---

### 1. **Instalasi C & C++ di Windows**

**Langkah-langkah:**

1. **Download dan Instal MinGW (Minimalist GNU for Windows):**
   - Kunjungi halaman [MinGW-w64](https://sourceforge.net/projects/mingw-w64/) dan unduh installer untuk Windows (misalnya `mingw-w64-install.exe`).
   - Jalankan installer, pilih **Architecture** yang sesuai (misalnya `x86_64` untuk 64-bit), dan pilih **Threads: win32** dan **Exception: sjlj** (jika tidak ada pilihan lain).

2. **Set Path:**
   - Setelah instalasi selesai, tambahkan direktori `bin` dari MinGW ke dalam PATH lingkungan Windows.
     - Misalnya, jika MinGW diinstal di `C:\Program Files\mingw-w64\mingw32\bin`, tambahkan path ini ke **System Properties > Environment Variables** di bagian **System variables** → **Path**.

3. **Verifikasi Instalasi:**
   - Buka **Command Prompt** dan ketik perintah berikut untuk memeriksa apakah GCC terinstal:
     ```bash
     gcc --version
     ```
     Untuk memeriksa versi C++:
     ```bash
     g++ --version
     ```
     Outputnya akan menunjukkan versi GCC yang terinstal.

4. **Menguji Kompilasi:**
   - Untuk menguji instalasi, buat file `hello.c` dan `hello.cpp`, lalu kompilasi dengan perintah:
     ```bash
     gcc hello.c -o hello
     g++ hello.cpp -o hello_cpp
     ```

---

### 2. **Instalasi C & C++ di Linux (Debian/Ubuntu)**

**Langkah-langkah:**

1. **Perbarui Paket Sistem:**
   - Buka terminal dan jalankan perintah berikut untuk memperbarui sistem:
     ```bash
     sudo apt update && sudo apt upgrade
     ```

2. **Instal GCC (C & C++ Compiler):**
   - Instal GCC dengan perintah:
     ```bash
     sudo apt install build-essential
     ```
   - Paket `build-essential` akan menginstal GCC, G++, dan alat pengembangan lain yang diperlukan untuk kompilasi C dan C++.

3. **Verifikasi Instalasi:**
   - Periksa versi GCC (untuk C) dan G++ (untuk C++) dengan perintah:
     ```bash
     gcc --version
     g++ --version
     ```
     Outputnya akan menunjukkan versi yang terinstal, seperti:
     ```
     gcc (Ubuntu 10.x.x) 10.x.x
     g++ (Ubuntu 10.x.x) 10.x.x
     ```

4. **Menguji Kompilasi:**
   - Untuk menguji kompilasi, buat file `hello.c` dan `hello.cpp`, lalu kompilasi dengan perintah:
     ```bash
     gcc hello.c -o hello
     g++ hello.cpp -o hello_cpp
     ```

---

### 3. **Instalasi C & C++ di macOS**

**Langkah-langkah:**

1. **Instalasi menggunakan Xcode Command Line Tools:**
   - Xcode Command Line Tools sudah menyertakan GCC dan G++ untuk pengembangan C dan C++.
   - Untuk menginstal Xcode Command Line Tools, buka terminal dan jalankan perintah:
     ```bash
     xcode-select --install
     ```

2. **Verifikasi Instalasi:**
   - Periksa versi GCC (untuk C) dan G++ (untuk C++) dengan perintah:
     ```bash
     gcc --version
     g++ --version
     ```
     Outputnya akan menunjukkan versi yang terinstal, seperti:
     ```
     gcc (Homebrew GCC x.x.x) x.x.x
     g++ (Homebrew GCC x.x.x) x.x.x
     ```

3. **Menguji Kompilasi:**
   - Untuk menguji instalasi, buat file `hello.c` dan `hello.cpp`, lalu kompilasi dengan perintah:
     ```bash
     gcc hello.c -o hello
     g++ hello.cpp -o hello_cpp
     ```

---

### 4. **Instalasi C & C++ di Termux (Android)**

**Langkah-langkah:**

1. **Perbarui Paket Termux:**
   - Pertama, pastikan repositori paket Termux terbaru dengan menjalankan:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal GCC (C & C++ Compiler):**
   - Instal GCC untuk C dan C++ dengan perintah:
     ```bash
     pkg install clang
     ```

3. **Verifikasi Instalasi:**
   - Periksa versi GCC (untuk C) dan G++ (untuk C++) dengan perintah:
     ```bash
     clang --version
     ```
     Outputnya akan menunjukkan versi yang terinstal.

4. **Menguji Kompilasi:**
   - Untuk menguji instalasi, buat file `hello.c` dan `hello.cpp`, lalu kompilasi dengan perintah:
     ```bash
     clang hello.c -o hello
     clang++ hello.cpp -o hello_cpp
     ```

---

### Kesimpulan:

- **Windows:** Gunakan **MinGW** untuk menginstal GCC dan G++.
- **Linux (Debian/Ubuntu):** Gunakan `sudo apt install build-essential` untuk menginstal GCC dan G++.
- **macOS:** Gunakan **Xcode Command Line Tools** untuk menginstal GCC dan G++.
- **Termux (Android):** Gunakan `pkg install clang` untuk menginstal GCC dan G++.

Setelah mengikuti langkah-langkah di atas, Anda siap untuk mengembangkan aplikasi menggunakan C dan C++ di berbagai platform!
