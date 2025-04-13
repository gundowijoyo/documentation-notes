
```markdown
# Perbaikan GPG Key Repository di Kali Linux Lama / Rusak

Dokumentasi ini menjelaskan langkah-langkah debug dan solusi jika sistem Kali kamu gagal update karena masalah GPG key yang expired dan sertifikat SSL yang tidak dipercaya saat mengakses repo resmi Kali Linux.

## Gejala Error

Saat menjalankan:

sudo apt update
```

Muncul error:
```bash
EXPKEYSIG ED444FF07D8D0BF6 Kali Linux Repository <devel@kali.org>
```

Dan saat mencoba mengunduh key:
```bash
wget https://archive.kali.org/archive-key.asc
```

Muncul error:
```
ERROR: The certificate of 'archive.kali.org' is not trusted.
```

---

## Langkah Debug dan Perbaikan

### 1. Download Key Tanpa Verifikasi SSL

Gunakan `--no-check-certificate` untuk bypass SSL (karena `ca-certificates` belum tersedia):

```bash
wget --no-check-certificate https://archive.kali.org/archive-key.asc
```

### 2. Tambahkan Key ke Sistem

Jika `gpg` **BELUM tersedia** di sistem, gunakan key `.asc` langsung:

```bash
sudo cp archive-key.asc /etc/apt/trusted.gpg.d/kali-archive-keyring.asc
```

> Ini menambahkan key ke sistem trusted tanpa perlu mengubah format `.gpg`.

### 3. Update APT Package Index

Setelah key ditambahkan, jalankan:

```bash
sudo apt update
```

Jika berhasil, maka error `EXPKEYSIG` tidak akan muncul lagi.

---

## (Opsional) Setelah APT Berfungsi

Install kembali paket penting:

```bash
sudo apt install ca-certificates gnupg curl nano -y
```

Lalu simpan key dalam format `.gpg` jika ingin rapi:
```bash
gpg --dearmor archive-key.asc
sudo mv archive-key.asc.gpg /etc/apt/trusted.gpg.d/kali-archive-keyring.gpg
```

---

## Catatan Tambahan

- Pastikan `sources.list` kamu hanya berisi:
  ```
  deb http://http.kali.org/kali kali-rolling main non-free contrib
  ```

- Bersihkan cache lama sebelum update:
  ```bash
  sudo rm -rf /var/lib/apt/lists/*
  sudo apt clean
  ```

---

## Troubleshooting

### wget: command not found
> Solusi: Install wget setelah APT berfungsi.
```bash
sudo apt install wget
```

### gpg: command not found
> Solusi: Install dengan:
```bash
sudo apt install gnupg
```
