
---

```markdown
# Dokumentasi Koneksi Domain dan Hosting di Vercel

Dokumentasi ini menjelaskan langkah-langkah untuk menghubungkan domain (misalnya Pendia) dengan hosting di Vercel, mulai dari pengelolaan nameserver hingga konfigurasi DNS.

## Langkah 1: Akses Panel Pengelolaan Domain

1. **Login ke Akun Registrar Domain**  
   Masuk ke akun registrar domain Anda (misalnya Pendia) di tempat Anda membeli domain.

2. **Cari Pengaturan DNS / Nameserver**  
   Cari menu yang mengarah ke pengelolaan DNS atau Nameserver. Biasanya berada di bagian "Domain Management" atau "DNS Settings".

## Langkah 2: Mengubah Nameserver ke Vercel

1. **Dapatkan Nameserver Vercel**  
   Vercel menyediakan nameserver yang dapat Anda gunakan untuk menghubungkan domain Anda ke Vercel. Berikut adalah nameserver Vercel yang umum:
   
   ```
   ns1.vercel-dns.com
   ns2.vercel-dns.com
   ```
   
2. **Ubah Nameserver di Registrar**  
   Di panel pengelolaan domain Anda, ubah nameserver domain Anda ke nameserver Vercel yang telah disediakan. Biasanya ada dua kolom untuk memasukkan nameserver, yaitu `NS1` dan `NS2`.

3. **Simpan Perubahan**  
   Setelah Anda mengubah nameserver, simpan perubahan dan tunggu beberapa saat untuk propagasi.

## Langkah 3: Tambahkan Domain di Vercel

1. **Login ke Akun Vercel**  
   Masuk ke akun Vercel Anda.

2. **Buka Dashboard Vercel**  
   Pilih proyek atau aplikasi yang ingin Anda sambungkan dengan domain.

3. **Akses Pengaturan Domain**  
   Klik pada tab "Settings" di proyek Anda, lalu pilih "Domains".

4. **Tambahkan Domain Baru**  
   Klik tombol "Add" untuk menambahkan domain baru dan masukkan nama domain Anda (misalnya `example.com`).

5. **Verifikasi Kepemilikan Domain**  
   Vercel akan meminta Anda untuk memverifikasi kepemilikan domain. Biasanya, Vercel akan memberikan file verifikasi atau instruksi untuk menambahkan DNS record tertentu (misalnya, TXT record) ke pengaturan DNS domain Anda.

## Langkah 4: Pengaturan DNS di Vercel

1. **Masukkan Record DNS**  
   Setelah domain ditambahkan, Vercel akan memberikan instruksi lebih lanjut tentang pengaturan DNS untuk memastikan bahwa domain Anda dapat mengarah ke proyek di Vercel. Beberapa pengaturan umum termasuk:

   - **A Record**  
     Masukkan IP Vercel untuk mengarahkan domain ke hosting Vercel.
     
   - **CNAME Record**  
     Jika menggunakan subdomain (misalnya `www`), masukkan CNAME yang mengarah ke `cname.vercel-dns.com`.
   
   - **TXT Record**  
     Menambahkan TXT record untuk verifikasi kepemilikan domain.

2. **Periksa Propagasi DNS**  
   Setelah DNS diatur, Anda perlu menunggu hingga propagasi DNS selesai. Proses ini bisa memakan waktu beberapa jam hingga 48 jam tergantung pada registrar.

## Langkah 5: Verifikasi Koneksi

1. **Periksa Status Domain di Vercel**  
   Setelah DNS berhasil dipropagasikan, kembali ke Vercel dan periksa status domain. Vercel akan mengonfirmasi bahwa domain Anda telah berhasil terhubung.

2. **Akses Website dengan Domain Kustom**  
   Sekarang Anda dapat mengakses aplikasi Anda menggunakan domain kustom (misalnya `www.example.com`) yang sudah terhubung dengan Vercel.

---

Dengan langkah-langkah di atas, Anda telah berhasil menghubungkan domain Anda dengan hosting di Vercel. Jika ada masalah atau kesulitan, Anda dapat memeriksa dokumentasi Vercel atau menghubungi support dari registrar domain.

```

---
