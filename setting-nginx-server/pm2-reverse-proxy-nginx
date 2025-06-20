## ✅ Langkah Setup PM2 untuk Menjalankan Project Node.js

### 1. **Install PM2 secara global**

```bash
npm install -g pm2
```

---

### 2. **Jalankan project pakai PM2**

Masuk ke folder project kamu (misal `/var/www/restapi`) lalu:

```bash
cd /var/www/your-directory
pm2 start index.js --name your-directory
```

Penjelasan:

* `index.js` → nama file yang dijalankan
* `--name your-directory` → nama alias supaya gampang dikenali di PM2

---

### 3. **Cek status aplikasi di PM2**

```bash
pm2 status
```

Contoh output:

```
┌─────┬─────────┬──────┬──────┬────────┬───────┬────────┐
│ id  │ name    │ mode │ pid  │ status │ cpu   │ memory │
├─────┼─────────┼──────┼──────┼────────┼───────┼────────┤
│ 0   │ restapi │ fork │ 1234 │ online │  1.0% │ 50 MB  │
└─────┴─────────┴──────┴──────┴────────┴───────┴────────┘
```

---

### 4. **Buat PM2 jalan otomatis saat server boot (auto restart)**

```bash
pm2 startup
```

Output-nya biasanya seperti ini:

```
[PM2] Init system found: systemd
[PM2] To setup the startup script, copy/paste the following command:
sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u root --hp /root
```

Tinggal **copy-paste** perintah yang disarankan (biasanya yang diawali `sudo env...`), lalu jalankan.

---

### 5. **Simpan proses ke konfigurasi startup**

```bash
pm2 save
```

Ini menyimpan semua app yang sedang berjalan supaya otomatis dinyalakan ulang setelah reboot.

---

### 6. **(Opsional) Melihat log aplikasi**

```bash
pm2 logs restapi
```

Untuk keluar dari tampilan log: tekan `Ctrl + C`

---

### 7. **Perintah penting lainnya:**

| Perintah                     | Fungsi                                            |
| ---------------------------- | ------------------------------------------------- |
| `pm2 restart restapi`        | Restart aplikasi                                  |
| `pm2 stop restapi`           | Hentikan aplikasi                                 |
| `pm2 delete restapi`         | Hapus aplikasi dari PM2                           |
| `pm2 reload restapi`         | Reload dengan zero-downtime (kalau pakai cluster) |
| `pm2 list` atau `pm2 status` | Lihat semua app yang sedang berjalan              |

