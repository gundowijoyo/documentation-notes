Berikut adalah panduan untuk menginstal **Docker** di 4 sistem operasi yang berbeda: **Windows**, **Linux**, **macOS**, dan **Termux (Android)**. Docker adalah platform untuk mengembangkan, mengirimkan, dan menjalankan aplikasi dalam container.

---

### **1. Instalasi Docker di Windows**

#### Langkah-langkah Instalasi:
1. **Unduh Docker Desktop:**
   - Kunjungi halaman resmi Docker di [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).
   - Pilih versi untuk **Windows** dan unduh installer.

2. **Jalankan Installer:**
   - Buka file installer yang sudah diunduh dan ikuti petunjuk untuk menginstal **Docker Desktop**.
   - Pastikan untuk mengaktifkan **WSL 2 (Windows Subsystem for Linux)** jika diminta (Docker membutuhkan WSL 2 untuk berfungsi di Windows).

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, buka **Docker Desktop** dan pastikan aplikasi berjalan.
   - Di dalam **PowerShell** atau **Command Prompt**, jalankan perintah berikut untuk memastikan Docker terinstal dengan benar:
     ```bash
     docker --version
     ```

   Output yang diharapkan:
   ```
   Docker version 20.x.x, build xxxxxxx
   ```

---

### **2. Instalasi Docker di Linux (Debian/Ubuntu)**

#### Langkah-langkah Instalasi:
1. **Perbarui Daftar Paket:**
   - Buka terminal dan perbarui repositori paket terlebih dahulu:
     ```bash
     sudo apt update
     sudo apt upgrade
     ```

2. **Instal Docker:**
   - Instal Docker dengan perintah berikut:
     ```bash
     sudo apt install docker.io
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi Docker dengan perintah:
     ```bash
     docker --version
     ```

   Output yang diharapkan:
   ```
   Docker version 20.x.x, build xxxxxxx
   ```

#### Instalasi Docker Versi Terbaru (Opsional):
Jika Anda ingin menginstal versi terbaru Docker, gunakan repositori resmi Docker:
1. **Tambahkan Docker Repository:**
   ```bash
   sudo curl -fsSL https://get.docker.com | bash
   ```

2. **Instal Docker:**
   ```bash
   sudo apt install docker-ce
   ```

---

### **3. Instalasi Docker di macOS**

#### Langkah-langkah Instalasi:
1. **Unduh Docker Desktop:**
   - Kunjungi halaman resmi Docker di [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).
   - Pilih **macOS** dan unduh file installer.

2. **Jalankan Installer:**
   - Setelah unduhan selesai, buka file installer dan ikuti petunjuk untuk menginstal **Docker Desktop**.

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, buka **Docker Desktop** dan pastikan aplikasi berjalan.
   - Di dalam terminal macOS, jalankan perintah berikut untuk memastikan Docker terinstal dengan benar:
     ```bash
     docker --version
     ```

   Output yang diharapkan:
   ```
   Docker version 20.x.x, build xxxxxxx
   ```

---

### **4. Instalasi Docker di Termux (Android)**

Pada **Termux**, Docker tidak dapat langsung dijalankan seperti pada sistem berbasis Linux lainnya. Namun, Anda bisa menggunakan alternatif seperti **Podman**, yang kompatibel dengan Docker dan bekerja di Termux.

#### Langkah-langkah Instalasi Podman di Termux:
1. **Perbarui Paket Termux:**
   - Buka aplikasi **Termux** dan jalankan perintah berikut untuk memperbarui repositori paket:
     ```bash
     pkg update && pkg upgrade
     ```

2. **Instal Podman:**
   - Instal **Podman**, yang merupakan alternatif Docker untuk pengelolaan container:
     ```bash
     pkg install podman
     ```

3. **Verifikasi Instalasi:**
   - Setelah instalasi selesai, periksa versi **Podman** (alternatif Docker) dengan perintah:
     ```bash
     podman --version
     ```

   Output yang diharapkan:
   ```
   podman version 3.x.x
   ```

4. **Menggunakan Podman:**
   - Anda bisa menjalankan perintah yang serupa dengan perintah Docker menggunakan **Podman** di Termux. Contoh perintah untuk menarik image Docker menggunakan Podman:
     ```bash
     podman pull ubuntu
     ```

---

### **Ringkasan Instalasi Docker**

- **Windows:**
  - Gunakan **Docker Desktop** yang dapat diunduh dari [docker.com](https://www.docker.com/products/docker-desktop). Pastikan untuk mengaktifkan **WSL 2** jika diperlukan.
  
- **Linux (Debian/Ubuntu):**
  - Instal Docker menggunakan perintah `sudo apt install docker.io` untuk versi stabil, atau `curl -fsSL https://get.docker.com | bash` untuk versi terbaru.

- **macOS:**
  - Gunakan **Docker Desktop** yang dapat diunduh dari [docker.com](https://www.docker.com/products/docker-desktop).

- **Termux (Android):**
  - Docker tidak dapat langsung digunakan di Termux, namun Anda bisa menggunakan **Podman** sebagai alternatif dengan perintah `pkg install podman`.

---

Dengan Docker atau Podman, Anda dapat mulai menggunakan container untuk mengemas dan menjalankan aplikasi di berbagai platform.
