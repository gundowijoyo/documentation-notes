## 📦 Tahapan Lengkap Membuat Email Bisnis Sendiri di VPS Ubuntu

---

### 🔧 1. **Siapkan VPS + Domain**

* VPS aktif dengan IP publik `123.123.xxx.xxx`
* Domain aktif: `yourdomain.com`
* Akses root ke VPS (Ubuntu 20.04/22.04/24.04)

---

### 🌐 2. **Atur DNS Record untuk Email**

Login ke DNS manager (Cloudflare, cPanel, Hostinger, dll), lalu tambahkan:

| Tipe | Name / Host         | Nilai / Value                                             |
| ---- | ------------------- | --------------------------------------------------------- |
| A    | mail                | 123.123.xxx.xxx                                           |
| MX   | @                   | mail.yourdomain.com (priority: 10)                        |
| TXT  | @                   | `v=spf1 ip4:123.123.xxx.xxx -all`                         |
| TXT  | default.\_domainkey | (akan diisi nanti setelah generate DKIM)                  |
| TXT  | \_dmarc             | `v=DMARC1; p=quarantine; rua=mailto:admin@yourdomain.com` |

---

### 📭 3. **Install Mail Server: Postfix, Dovecot, DKIM**

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install postfix dovecot-core dovecot-imapd mailutils opendkim opendkim-tools -y
```

Saat setup postfix, pilih:

* **"Internet Site"**
* **System mail name**: `yourdomain.com`

---

### 📩 4. **Konfigurasi Postfix (SMTP)**

Edit `/etc/postfix/main.cf`:

```bash
sudo nano /etc/postfix/main.cf
```

Tambahkan/ubah bagian berikut:

```ini
myhostname = mail.yourdomain.com
mydomain = yourdomain.com
myorigin = /etc/mailname
inet_interfaces = all
inet_protocols = all
mydestination = $myhostname, localhost.$mydomain, localhost
home_mailbox = Maildir/
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_auth_only = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
```

---

### 📥 5. **Konfigurasi Dovecot (IMAP/POP3)**

Aktifkan protokol dan lokasi email:

```bash
sudo nano /etc/dovecot/conf.d/10-mail.conf
```

Set:

```ini
mail_location = maildir:~/Maildir
```

Aktifkan otentikasi:

```bash
sudo nano /etc/dovecot/conf.d/10-auth.conf
```

```ini
disable_plaintext_auth = no
auth_mechanisms = plain login
```

Aktifkan socket autentikasi Postfix:

```bash
sudo nano /etc/dovecot/conf.d/10-master.conf
```

```ini
unix_listener /var/spool/postfix/private/auth {
  mode = 0660
  user = postfix
  group = postfix
}
```

---

### 🔑 6. **Konfigurasi OpenDKIM dan Generate Key**

```bash
sudo mkdir -p /etc/opendkim/keys/yourdomain.com
cd /etc/opendkim/keys/yourdomain.com
sudo opendkim-genkey -s default -d yourdomain.com
sudo chown opendkim:opendkim default.private
```

---

### ⚙️ 7. **Konfigurasi OpenDKIM File Utama**

Edit `/etc/opendkim.conf`:

```ini
Socket                  inet:12301@localhost
KeyTable                /etc/opendkim/key.table
SigningTable            /etc/opendkim/signing.table
ExternalIgnoreList      /etc/opendkim/trusted.hosts
InternalHosts           /etc/opendkim/trusted.hosts
```

---

### 🗂️ Buat File Konfigurasi Tambahan

#### `/etc/opendkim/key.table`

```ini
default._domainkey.yourdomain.com yourdomain.com:default:/etc/opendkim/keys/yourdomain.com/default.private
```

#### `/etc/opendkim/signing.table`

```ini
*@yourdomain.com default._domainkey.yourdomain.com
```

#### `/etc/opendkim/trusted.hosts`

```ini
127.0.0.1
localhost
yourdomain.com
mail.yourdomain.com
```

---

### 🔗 8. **Integrasi OpenDKIM ke Postfix**

Edit `/etc/postfix/main.cf`, tambahkan:

```ini
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:12301
non_smtpd_milters = inet:localhost:12301
```

---

### 🔁 9. **Restart Semua Layanan**

```bash
sudo systemctl restart opendkim
sudo systemctl restart postfix
sudo systemctl restart dovecot
```

---

### 👤 10. **Buat Akun Email**

Misalnya untuk `admin@yourdomain.com`:

```bash
sudo adduser admin
```

---

### 📱 11. **Setting di Mail Client**

| Setting     | Value                                                              |
| ----------- | ------------------------------------------------------------------ |
| Email       | [admin@yourdomain.com](mailto:admin@yourdomain.com)                |
| IMAP Server | mail.yourdomain.com (port 143, TLS/STARTTLS)                       |
| SMTP Server | mail.yourdomain.com (port 587, TLS)                                |
| Username    | [admin@yourdomain.com](mailto:admin@yourdomain.com) (atau `admin`) |
| Password    | (password user Linux `admin`)                                      |

---

### 🧪 12. **Uji dan Verifikasi**

#### 📤 Uji Kirim:

```bash
echo "Hello from yourdomain.com" | mail -s "Test Email" youremail@gmail.com
```

#### 📄 Lihat log:

```bash
tail -f /var/log/mail.log
```

#### 📧 Buka Gmail → "Show Original" → Lihat hasil:

* SPF: `PASS`
* DKIM: `PASS`
* DMARC: `PASS`

---

### 🧪 Tambahan Tes:

Cek skor pengiriman dan reputasi di:

* [https://www.mail-tester.com](https://www.mail-tester.com)
* [https://mxtoolbox.com](https://mxtoolbox.com)

---

## 🚀 Email Bisnis Siap Digunakan

Kamu sekarang punya:

* Alamat email bisnis `admin@yourdomain.com`
* Email keluar tidak masuk spam
* SPF, DKIM, dan DMARC valid
* Bisa diakses dari HP / Outlook / Thunderbird
