## ✅ 1. **Install MySQL Server**

```bash
sudo apt update
sudo apt install mysql-server -y
```

Setelah terpasang, pastikan MySQL berjalan:

```bash
sudo systemctl status mysql
```

**(Opsional) Amankan MySQL:**

```bash
sudo mysql_secure_installation
```

Ikuti petunjuknya untuk mengatur root password, menghapus user anonim, dan sebagainya.

---

## ✅ 2. **Install PHP**

Karena phpMyAdmin membutuhkan PHP, install PHP dan ekstensi yang dibutuhkan:

```bash
sudo apt install php-fpm php-mysql -y
```

Pastikan PHP-FPM berjalan:

```bash
sudo systemctl status php7.*-fpm  # tergantung versi PHP-nya
```

---

## ✅ 3. **Install phpMyAdmin (Tanpa Apache)**

Secara default, installer phpMyAdmin mencoba mengkonfigurasi Apache. Karena kita memakai Nginx, kita akan melewatkannya.

```bash
sudo apt install phpmyadmin -y
```

Saat diminta:

* Pilih **`<No>`** ketika diminta memilih web server (karena kita menggunakan Nginx).
* Pilih **Yes** untuk mengonfigurasi database untuk phpMyAdmin.
* Masukkan password untuk user `phpmyadmin`.

Jika tidak muncul prompt karena penginstalan otomatis:

```bash
sudo dpkg-reconfigure phpmyadmin
```

---

## ✅ 4. **Konfigurasi Nginx untuk phpMyAdmin**

Tambahkan konfigurasi di file Nginx untuk server Anda, misalnya:

```bash
sudo nano /etc/nginx/sites-available/default
```

Tambahkan block ini di dalam `server {}` block:

```nginx
location /phpmyadmin {
    root /usr/share/;
    index index.php index.html index.htm;

    location ~ ^/phpmyadmin/(.+\.php)$ {
        try_files $uri =404;
        root /usr/share/;
        fastcgi_pass unix:/run/php/php7.x-fpm.sock;  # Ganti dengan versi PHP Anda
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        root /usr/share/;
    }
}
```

Ganti `php7.x-fpm.sock` dengan yang sesuai versi PHP Anda. Cek dengan:

```bash
ls /run/php/
```

Setelah itu, reload Nginx:

```bash
sudo systemctl reload nginx
```

---

## ✅ 5. **Akses phpMyAdmin**

Buka browser dan akses:

```
http://<IP-Server-Anda>/phpmyadmin
```

Login dengan:

* **Username**: `root` atau `phpmyadmin`
* **Password**: yang telah Anda atur saat instalasi

---

## 🛡️ Tips Keamanan (Opsional tapi Disarankan)

1. **Nonaktifkan login root** dari phpMyAdmin.
2. **Batasi akses** ke `/phpmyadmin` hanya dari IP tertentu.
3. **Gunakan HTTPS** dengan sertifikat SSL (misalnya dari Let’s Encrypt).

Jika Anda butuh contoh konfigurasi keamanan tambahan, saya bisa bantu juga.

---

Ingin saya bantu generate konfigurasi Nginx lengkap sesuai setup Anda?
