## ✅ **1. Install Nginx di Ubuntu 25.04**

### 🔹 Update paket terlebih dahulu

```bash
sudo apt update
```

### 🔹 Install Nginx

```bash
sudo apt install nginx -y
```

### 🔹 Cek status Nginx

```bash
sudo systemctl status nginx
```

Untuk memastikan Nginx berjalan otomatis saat boot:

```bash
sudo systemctl enable nginx
```

---

## ✅ **2. Akses Nginx dari Browser**

Setelah instalasi berhasil, buka browser dan akses:

```
http://<IP-server-Anda>
```

Jika berhasil, akan tampil **“Welcome to nginx!”**.

---

## ✅ **3. Struktur Direktori Nginx di Ubuntu**

| Path                          | Fungsi                                                |
| ----------------------------- | ----------------------------------------------------- |
| `/etc/nginx/nginx.conf`       | File konfigurasi utama                                |
| `/etc/nginx/sites-available/` | Tempat file konfigurasi virtual host                  |
| `/etc/nginx/sites-enabled/`   | File konfigurasi aktif (symlink ke `sites-available`) |
| `/var/www/html/`              | Direktori default root web                            |

---

## ✅ **4. Konfigurasi Virtual Host (Server Block)**

Untuk mengatur domain atau subdomain:

### 🔹 Buat file konfigurasi baru

Misal untuk domain `contoh.local`:

```bash
sudo nano /etc/nginx/sites-available/contoh.local
```

Isi contoh konfigurasi:

```nginx
server {
    listen 80;
    server_name contoh.local www.contoh.local;

    root /var/www/contoh.local;
    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.x-fpm.sock;  # ganti sesuai versi PHP Anda
    }

    location ~ /\.ht {
        deny all;
    }
}
```

### 🔹 Buat direktori root-nya

```bash
sudo mkdir -p /var/www/contoh.local
echo "<h1>Hello dari contoh.local</h1>" | sudo tee /var/www/contoh.local/index.html
```

### 🔹 Aktifkan virtual host

```bash
sudo ln -s /etc/nginx/sites-available/contoh.local /etc/nginx/sites-enabled/
```

### 🔹 Uji konfigurasi dan reload Nginx

```bash
sudo nginx -t
sudo systemctl reload nginx
```

### 🔹 Tambahkan ke `/etc/hosts` (untuk akses lokal)

Jika ini untuk development lokal:

```bash
sudo nano /etc/hosts
```

Tambahkan:

```
127.0.0.1   contoh.local
```

---

## ✅ **5. Perintah Penting Nginx**

| Perintah                      | Keterangan                       |
| ----------------------------- | -------------------------------- |
| `sudo systemctl start nginx`  | Menjalankan Nginx                |
| `sudo systemctl stop nginx`   | Menghentikan Nginx               |
| `sudo systemctl reload nginx` | Reload konfigurasi tanpa restart |
| `sudo nginx -t`               | Uji konfigurasi sebelum reload   |
| `sudo journalctl -xeu nginx`  | Lihat log error Nginx            |
