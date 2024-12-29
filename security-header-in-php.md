
# Keamanan HTTP Headers di PHP

Dokumentasi ini memberikan penjelasan singkat mengenai berbagai header HTTP yang dapat diterapkan untuk meningkatkan keamanan aplikasi PHP. Pengaturan header yang tepat dapat melindungi aplikasi dari berbagai ancaman seperti serangan XSS, CSRF, clickjacking, dan lainnya.

## Daftar Header Keamanan HTTP

### 1. **`X-Frame-Options`**
   **Fungsi**: Mencegah halaman dimuat dalam `<iframe>`, melindungi dari serangan clickjacking.
   - **Nilai yang diperbolehkan**: `DENY`, `SAMEORIGIN`, `ALLOW-FROM uri`
   - **Contoh**:
     ```php
     header('X-Frame-Options: DENY');
     ```

### 2. **`Content-Security-Policy (CSP)`**
   **Fungsi**: Menentukan sumber yang sah untuk skrip, gambar, dan konten lainnya. Mencegah injeksi skrip jahat (XSS).
   - **Contoh**:
     ```php
     header("Content-Security-Policy: default-src 'self'; script-src 'self';");
     ```

### 3. **`Strict-Transport-Security (HSTS)`**
   **Fungsi**: Memaksa browser untuk hanya mengakses aplikasi melalui HTTPS, mencegah downgrade attacks.
   - **Contoh**:
     ```php
     header("Strict-Transport-Security: max-age=31536000; includeSubDomains");
     ```

### 4. **`X-XSS-Protection`**
   **Fungsi**: Mengaktifkan perlindungan XSS di browser. Digunakan untuk mencegah serangan Cross-Site Scripting (XSS).
   - **Contoh**:
     ```php
     header('X-XSS-Protection: 1; mode=block');
     ```

### 5. **`X-Content-Type-Options`**
   **Fungsi**: Mencegah browser menebak tipe MIME, yang bisa digunakan untuk mengeksploitasi file yang tidak diproses dengan benar.
   - **Contoh**:
     ```php
     header('X-Content-Type-Options: nosniff');
     ```

### 6. **`Referrer-Policy`**
   **Fungsi**: Menentukan bagaimana informasi referer dikirim dalam permintaan HTTP.
   - **Contoh**:
     ```php
     header('Referrer-Policy: no-referrer');
     ```

### 7. **`Permissions-Policy`**
   **Fungsi**: Mengatur kebijakan terkait akses perangkat keras dan API browser, seperti kamera, mikrofon, dll.
   - **Contoh**:
     ```php
     header('Permissions-Policy: geolocation=(self), microphone=()');
     ```

### 8. **`Cache-Control`**
   **Fungsi**: Mengontrol cache di browser untuk melindungi data sensitif dari penyimpanan cache yang tidak aman.
   - **Contoh**:
     ```php
     header('Cache-Control: no-store, no-cache, must-revalidate');
     ```

### 9. **`Pragma`**
   **Fungsi**: Digunakan bersama dengan `Cache-Control` untuk mencegah caching di browser.
   - **Contoh**:
     ```php
     header('Pragma: no-cache');
     ```

### 10. **`Expires`**
   **Fungsi**: Menentukan kapan konten akan kedaluwarsa. Digunakan untuk memastikan konten tidak disimpan lebih lama dari yang dimaksudkan.
   - **Contoh**:
     ```php
     header('Expires: 0');
     ```

### 11. **`Set-Cookie`**
   **Fungsi**: Digunakan untuk mengonfigurasi cookie. Dengan menggunakan atribut `Secure` dan `HttpOnly`, kamu bisa melindungi cookie dari serangan.
   - **Contoh**:
     ```php
     setcookie('name', 'value', time() + 3600, '/', '', true, true);
     ```

### 12. **`Access-Control-Allow-Origin`**
   **Fungsi**: Mengatur asal yang diizinkan untuk mengakses sumber daya tertentu pada server (CORS).
   - **Contoh**:
     ```php
     header('Access-Control-Allow-Origin: *');
     ```

### 13. **`Access-Control-Allow-Methods`**
   **Fungsi**: Menentukan metode HTTP yang diizinkan untuk permintaan lintas asal.
   - **Contoh**:
     ```php
     header('Access-Control-Allow-Methods: GET, POST, PUT');
     ```

### 14. **`Access-Control-Allow-Headers`**
   **Fungsi**: Menentukan header yang diizinkan dalam permintaan lintas asal.
   - **Contoh**:
     ```php
     header('Access-Control-Allow-Headers: Content-Type, Authorization');
     ```

### 15. **`Content-Security-Policy-Report-Only`**
   **Fungsi**: Seperti CSP biasa, tetapi hanya melaporkan pelanggaran tanpa mencegahnya.
   - **Contoh**:
     ```php
     header("Content-Security-Policy-Report-Only: default-src 'self'; report-uri /report-violation");
     ```

### 16. **`Expect-CT`**
   **Fungsi**: Mengaktifkan dan memverifikasi penggunaan Certificate Transparency (CT) dalam sertifikat SSL/TLS.
   - **Contoh**:
     ```php
     header('Expect-CT: max-age=86400, enforce');
     ```

### 17. **`Feature-Policy` (Deprecated, now `Permissions-Policy`)**
   **Fungsi**: Menentukan fitur-fitur browser yang boleh digunakan oleh situs.
   - **Contoh**:
     ```php
     header('Feature-Policy: vibrate "none"');
     ```

### 18. **`Strict-Transport-Security (HSTS)`**
   **Fungsi**: Menginstruksikan browser untuk selalu menggunakan HTTPS saat mengakses aplikasi dalam periode waktu tertentu.
   - **Contoh**:
     ```php
     header('Strict-Transport-Security: max-age=31536000; includeSubDomains');
     ```

### 19. **`X-Content-Security-Policy`**
   **Fungsi**: Digunakan pada versi lama browser untuk mengonfigurasi kebijakan keamanan konten (mirip dengan CSP).
   - **Contoh**:
     ```php
     header('X-Content-Security-Policy: default-src "self"');
     ```

### 20. **`X-Permitted-Cross-Domain-Policies`**
   **Fungsi**: Mengontrol akses cross-domain untuk Flash dan aplikasi web berbasis Adobe.
   - **Contoh**:
     ```php
     header('X-Permitted-Cross-Domain-Policies: none');
     ```

### 21. **`X-Download-Options`**
   **Fungsi**: Menonaktifkan penanganan file otomatis di browser (untuk file yang diunduh).
   - **Contoh**:
     ```php
     header('X-Download-Options: noopen');
     ```

### 22. **`X-DNS-Prefetch-Control`**
   **Fungsi**: Mengontrol apakah browser harus melakukan DNS prefetching (untuk mengoptimalkan waktu loading halaman).
   - **Contoh**:
     ```php
     header('X-DNS-Prefetch-Control: off');
     ```

### 23. **`X-UA-Compatible`**
   **Fungsi**: Menentukan mode render browser yang harus digunakan (misalnya, untuk mengaktifkan IE terbaru).
   - **Contoh**:
     ```php
     header('X-UA-Compatible: IE=edge');
     ```

### 24. **`X-Content-Transfer-Encoding`**
   **Fungsi**: Mengatur encoding yang digunakan untuk pengiriman konten (umumnya untuk data binary).
   - **Contoh**:
     ```php
     header('X-Content-Transfer-Encoding: binary');
     ```

### 25. **`X-Requested-With`**
   **Fungsi**: Menunjukkan bahwa permintaan adalah AJAX, sering digunakan untuk memverifikasi permintaan yang sah.
   - **Contoh**:
     ```php
     header('X-Requested-With: XMLHttpRequest');
     ```

---

**Catatan**: Semua header ini perlu dikonfigurasi dengan hati-hati dan diuji di aplikasi kamu untuk memastikan kompatibilitas dengan browser serta tidak mengganggu fungsionalitas yang ada.

## Referensi Lain
Untuk informasi lebih lanjut, pastikan untuk memeriksa dokumentasi resmi dari masing-masing header, seperti:
- [MDN Web Docs: HTTP headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
- [OWASP Secure Headers Project](https://owasp.org/www-project-secure-headers/)

Semoga dokumentasi ini bermanfaat untuk meningkatkan keamanan aplikasi PHP kamu!
