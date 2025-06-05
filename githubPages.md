## ✅ Cara Hosting Website di GitHub Pages via GitHub Web

### 1. **Buat Repository Baru**

1. Masuk ke [https://github.com](https://github.com)
2. Klik tombol **`+`** di kanan atas, lalu pilih **"New repository"**
3. Isi nama repositori (misalnya: `portfolio`, `my-website`, dll)
4. Centang **"Add a README file"** *(opsional tapi disarankan)*
5. Klik **Create repository**

---

### 2. **Upload File Website**

Jika kamu sudah punya file HTML/CSS/JS:

1. Buka repositori yang sudah dibuat
2. Klik tombol **`Add file` → `Upload files`**
3. Pilih file seperti `index.html`, `style.css`, dll dari komputer kamu
4. Klik **Commit changes**

---

### 3. **Aktifkan GitHub Pages**

1. Masuk ke tab **Settings** di repositori
2. Scroll ke bawah ke bagian **Pages**
3. Di bagian **"Source"**, pilih:

   * **Branch:** `main`
   * **Folder:** `/ (root)` atau `/docs` jika file HTML ada di folder `docs`
4. Klik **Save**

> Setelah beberapa detik, akan muncul link:
> ✅ **Your site is published at** `https://username.github.io/nama-repo`

---

### 4. **Akses Website Kamu**

Kunjungi URL yang muncul tadi, misalnya:

```
https://your-username.github.io/portfolio/
```

Website kamu sudah online 🎉

---

## 📌 Tips

* Pastikan kamu punya file `index.html` di root folder (halaman utama).
* Untuk update, tinggal upload file baru → commit changes.
* Gunakan folder `docs/` jika tidak ingin menaruh file di root.

---
