### ✅ Langkah-Langkah Mendapatkan Google Client ID

#### 1. **Buka Google Cloud Console**

Masuk ke:
👉 [https://console.cloud.google.com/](https://console.cloud.google.com/)

---

#### 2. **Buat Project Baru**

* Klik **Project Selector** (pojok kiri atas) → **New Project**
* Beri nama project, lalu klik **Create**

---

#### 3. **Aktifkan OAuth Consent Screen**

* Buka menu **"APIs & Services" > "OAuth consent screen"**
* Pilih **External** (kalau aplikasi untuk umum)
* Isi informasi seperti:

  * App name
  * User support email
  * Developer contact info
* Klik **Save and Continue** sampai selesai (tidak perlu isi scopes/permissions dulu)

---

#### 4. **Buat OAuth 2.0 Client ID**

* Buka menu **"APIs & Services" > "Credentials"**

* Klik **“+ Create Credentials”** → pilih **OAuth client ID**

* Pilih **Web application**

* Isi:

  * **Name**: bebas
  * **Authorized JavaScript origins**: contoh: `http://localhost:3000` (frontend URL kamu)
  * **Authorized redirect URIs**: kalau pakai flow redirect (bisa kosong kalau pakai Google Identity Services one-tap)

* Klik **Create**

---

#### 5. **Salin Client ID**

Setelah sukses, kamu akan melihat **Client ID** dan **Client Secret**. Salin **Client ID**, itu yang kamu gunakan di frontend:

```js
data-client_id="PASTE_CLIENT_ID_DISINI"
```

#### LANJUTT...

#### 1. **Pasang Google Identity Services (GIS)**

Kamu bisa pakai **Google Identity Services** untuk ambil `Google ID token` dan user data.

📌 Tambahkan script Google di file HTML kamu:

```html
<script src="https://accounts.google.com/gsi/client" async defer></script>
```

---

#### 2. **Siapkan tombol login Google**

```html
<div id="g_id_onload"
     data-client_id="YOUR_GOOGLE_CLIENT_ID"
     data-context="signup"
     data-callback="handleGoogleRegister"
     data-auto_prompt="false">
</div>

<div class="g_id_signin"
     data-type="standard"
     data-shape="rectangular"
     data-theme="outline"
     data-text="signup_with"
     data-size="large"
     data-logo_alignment="left">
</div>
```

> Ganti `YOUR_GOOGLE_CLIENT_ID` dengan client ID dari Google Console.

---

#### 3. **Tangani callback di JavaScript**

```html
<script>
  async function handleGoogleRegister(response) {
    const idToken = response.credential;

    // Verifikasi token ini ke Google untuk ambil data user (opsional)
    // atau langsung kirim ke backend
    try {
      const res = await fetch("https://www.googleapis.com/oauth2/v3/tokeninfo?id_token=" + idToken);
      const profile = await res.json();

      const registerResponse = await fetch('http://localhost:3000/api/auth/register', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          provider: 'google',
          provider_id: profile.sub, // ID Google unik
          email: profile.email,
          username: profile.name,
          phone_number: '' // optional
        })
      });

      const result = await registerResponse.json();
      console.log(result);

      if (result.success) {
        alert('Register berhasil!');
      } else {
        alert('Gagal register: ' + result.message);
      }

    } catch (err) {
      console.error('Error register via Google:', err);
    }
  }
</script>
```

---

### ✨ Summary

* Gunakan Google Identity Services (GIS) untuk ambil token.
* Pakai `tokeninfo` endpoint Google untuk ambil profil user dari token.
* Kirim `provider_id`, `email`, `username`, dan lainnya ke API-mu.

---

Kalau kamu pakai **React** atau framework lain, tinggal integrasikan logika yang sama, tapi dengan hook atau component masing-masing. Mau aku bantu versi React juga?
