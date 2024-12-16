Berikut adalah panduan instalasi **Node.js** dan **npm** di 4 sistem operasi: **Windows**, **Linux**, **macOS**, dan **Termux**.

---

### **1. Instalasi Node.js dan npm di Windows**

#### Langkah-langkah Instalasi:
1. **Unduh Node.js:**
   - Kunjungi halaman resmi **Node.js** di [https://nodejs.org/en/](https://nodejs.org/en/).
   - Pilih **LTS (Long Term Support)** untuk versi yang lebih stabil, atau **Current** untuk versi terbaru.
   
2. **Jalankan Installer:**
   - Setelah unduhan selesai, buka file installer dan ikuti petunjuk instalasi. Pastikan untuk mencentang opsi **"Install npm package manager"** agar **npm** terinstal secara otomatis.

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, buka **Command Prompt** atau **PowerShell** dan periksa versi Node.js dan npm dengan perintah berikut:
     ```bash
     node -v
     npm -v
     ```

   Output yang diharapkan:
   ```
   v16.x.x    # atau versi lainnya, tergantung yang diinstal
   7.x.x      # atau versi npm yang terinstal
   ```

---

### **2. Instalasi Node.js dan npm di Linux (Debian/Ubuntu)**

#### Langkah-langkah Instalasi:
1. **Perbarui Daftar Paket:**
   - Buka terminal dan perbarui repositori paket terlebih dahulu:
     ```bash
     sudo apt update
     ```

2. **Instal Node.js dan npm:**
   - Instal **Node.js** dan **npm** dengan perintah berikut:
     ```bash
     sudo apt install nodejs npm
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Node.js dan npm dengan perintah:
     ```bash
     node -v
     npm -v
     ```

   Output yang diharapkan:
   ```
   v16.x.x    # atau versi terbaru yang terinstal
   7.x.x      # versi npm yang terinstal
   ```

#### Instalasi Node.js Versi Terbaru (Opsional):
- Jika Anda ingin menginstal versi terbaru dari **Node.js**, disarankan menggunakan **NodeSource** repository:
  ```bash
  curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
  sudo apt install -y nodejs
  ```

---

### **3. Instalasi Node.js dan npm di macOS**

#### Langkah-langkah Instalasi:
1. **Instalasi menggunakan Homebrew:**
   - Jika Anda belum menginstal **Homebrew**, jalankan perintah berikut di terminal:
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```

2. **Instal Node.js dan npm dengan Homebrew:**
   - Setelah **Homebrew** terinstal, jalankan perintah berikut untuk menginstal **Node.js** dan **npm**:
     ```bash
     brew install node
     ```

3. **Verifikasi Instalasi:**
   - Periksa versi **Node.js** dan **npm** dengan perintah:
     ```bash
     node -v
     npm -v
     ```

   Output yang diharapkan:
   ```
   v16.x.x    # atau versi terbaru yang terinstal
   7.x.x      # versi npm yang terinstal
   ```

---

### **4. Instalasi Node.js dan npm di Termux (Android)**

#### Langkah-langkah Instalasi:
1. **Perbarui Paket Termux:**
   - Buka aplikasi **Termux** dan jalankan perintah berikut untuk memperbarui repositori paket:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal Node.js dan npm:**
   - Instal **Node.js** dan **npm** dengan perintah berikut:
     ```bash
     pkg install nodejs
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi **Node.js** dan **npm** dengan perintah:
     ```bash
     node -v
     npm -v
     ```

   Output yang diharapkan:
   ```
   v16.x.x    # atau versi terbaru yang terinstal
   7.x.x      # versi npm yang terinstal
   ```

---

### **Ringkasan Instalasi Node.js dan npm**

- **Windows:** 
  - Unduh dan instal **Node.js** dari [nodejs.org](https://nodejs.org/en/). **npm** akan terinstal otomatis.
  
- **Linux (Debian/Ubuntu):**
  - Gunakan perintah `sudo apt install nodejs npm` untuk menginstal Node.js dan npm. Jika Anda ingin versi terbaru, gunakan **NodeSource**.

- **macOS:**
  - Gunakan **Homebrew** (`brew install node`) untuk menginstal Node.js dan npm.

- **Termux (Android):**
  - Gunakan perintah `pkg install nodejs` untuk menginstal Node.js dan npm.

---

Dengan instalasi **Node.js** dan **npm** di atas, Anda dapat mulai mengembangkan aplikasi JavaScript baik di sisi server (menggunakan Node.js) maupun manajemen paket untuk pustaka JavaScript (menggunakan npm).
