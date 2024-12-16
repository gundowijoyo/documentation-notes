Berikut adalah panduan instalasi **Go (Golang)** di tiga sistem operasi: **Windows**, **Linux**, dan **macOS**. Saya juga akan menambahkan cara instalasi di **Termux** untuk Android.

---

### 1. **Instalasi Golang di Windows**

**Langkah-langkah:**

1. **Download Go:**
   - Kunjungi halaman unduhan Go di [https://golang.org/dl/](https://golang.org/dl/).
   - Pilih versi Go yang sesuai untuk Windows (misalnya `go1.x.x.windows-amd64.msi` untuk sistem 64-bit).

2. **Jalankan Installer:**
   - Klik dua kali file installer `.msi` yang telah diunduh.
   - Ikuti instruksi di layar untuk menginstal Go ke sistem.
   - Secara default, Go akan diinstal di folder `C:\Go`.

3. **Set Path (otomatis terpasang pada installer):**
   - Secara otomatis, installer akan menambahkan Go ke dalam **PATH**. Namun, jika perlu menambahkannya secara manual, buka **System Properties > Environment Variables**, kemudian tambahkan path berikut ke **PATH**:
     ```
     C:\Go\bin
     ```

4. **Verifikasi Instalasi:**
   - Buka **Command Prompt** dan jalankan perintah:
     ```bash
     go version
     ```
   - Jika instalasi berhasil, outputnya akan menunjukkan versi Go yang terinstal, seperti:
     ```
     go version go1.x.x windows/amd64
     ```

---

### 2. **Instalasi Golang di Linux (Debian/Ubuntu)**

**Langkah-langkah:**

1. **Perbarui Paket Sistem:**
   - Buka terminal dan jalankan perintah untuk memperbarui sistem:
     ```bash
     sudo apt update && sudo apt upgrade
     ```

2. **Instal Golang:**
   - Instal Go dari repositori resmi dengan perintah:
     ```bash
     sudo apt install golang
     ```

   - Atau, untuk menginstal versi terbaru langsung dari situs resmi Go, Anda dapat menggunakan langkah-langkah berikut:
     - Kunjungi [https://golang.org/dl/](https://golang.org/dl/) untuk mendownload arsip `.tar.gz` dari versi terbaru.
     - Unduh ke direktori `/usr/local/` atau direktori lain yang sesuai.

3. **Set Path:**
   - Setelah mengunduh dan mengekstrak Go, tambahkan Go ke dalam PATH. Misalnya, jika Anda menginstal di `/usr/local/go`, tambahkan baris berikut ke dalam `~/.bashrc` atau `~/.zshrc`:
     ```bash
     export PATH=$PATH:/usr/local/go/bin
     ```
   - Lakukan refresh pada terminal:
     ```bash
     source ~/.bashrc
     ```

4. **Verifikasi Instalasi:**
   - Jalankan perintah berikut untuk memeriksa versi Go:
     ```bash
     go version
     ```
     Outputnya akan menunjukkan versi Go yang terinstal, seperti:
     ```
     go version go1.x.x linux/amd64
     ```

---

### 3. **Instalasi Golang di macOS**

**Langkah-langkah:**

1. **Instalasi menggunakan Homebrew (rekomendasi):**
   - Jika belum menginstal Homebrew, jalankan perintah berikut di terminal:
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```

2. **Instal Golang dengan Homebrew:**
   - Setelah Homebrew terinstal, jalankan perintah berikut untuk menginstal Golang:
     ```bash
     brew install go
     ```

3. **Verifikasi Instalasi:**
   - Periksa versi Go yang terinstal dengan perintah:
     ```bash
     go version
     ```
     Outputnya akan menunjukkan versi Go yang terinstal, seperti:
     ```
     go version go1.x.x darwin/amd64
     ```

---

### 4. **Instalasi Golang di Termux (Android)**

**Langkah-langkah:**

1. **Perbarui Paket Termux:**
   - Pertama, pastikan repositori paket Termux terbaru dengan menjalankan:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal Golang:**
   - Install Golang dengan perintah:
     ```bash
     pkg install golang
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Go yang terinstal:
     ```bash
     go version
     ```
     Outputnya akan menunjukkan versi Go yang terinstal, seperti:
     ```
     go version go1.x.x android/arm
     ```

---

### Kesimpulan:

- **Windows:** Gunakan installer dari [golang.org/dl](https://golang.org/dl/) dan ikuti instruksi instalasi.
- **Linux:** Gunakan `sudo apt install golang` untuk distribusi berbasis Debian/Ubuntu atau unduh langsung dari situs resmi untuk versi terbaru.
- **macOS:** Gunakan Homebrew (`brew install go`) untuk instalasi yang mudah.
- **Termux (Android):** Gunakan `pkg install golang` untuk menginstal Golang di Termux.

Setelah mengikuti langkah-langkah di atas, Anda siap untuk mengembangkan aplikasi Go di masing-masing sistem operasi!
