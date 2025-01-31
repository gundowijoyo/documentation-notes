Tentu, berikut adalah dokumentasi aturan coding dalam bahasa pemrograman Python yang lengkap:

### 1. **Indentasi**
   - Python sangat bergantung pada indentasi (spasi atau tab) untuk menentukan struktur blok kode.
   - Umumnya, indentasi menggunakan 4 spasi per tingkat indentasi. Jangan mencampur tab dan spasi dalam satu file.
   - Contoh:
     ```python
     def hello_world():
         print("Hello, World!")
     ```

### 2. **Komentar**
   - Komentar digunakan untuk menjelaskan kode agar lebih mudah dipahami oleh programmer lain (atau diri sendiri di masa depan).
   - Komentar baris tunggal diawali dengan tanda `#`:
     ```python
     # Ini adalah komentar
     print("Hello, World!")
     ```
   - Komentar multi-baris dapat menggunakan tanda kutip tiga kali (`'''` atau `"""`):
     ```python
     """
     Ini adalah komentar
     yang bisa lebih dari satu baris
     """
     print("Hello, World!")
     ```

### 3. **Penamaan Variabel dan Fungsi**
   - Gunakan gaya penamaan **snake_case** (huruf kecil dengan pemisah garis bawah) untuk variabel dan nama fungsi.
   - Nama variabel atau fungsi tidak boleh dimulai dengan angka.
   - Nama variabel atau fungsi harus menjelaskan fungsinya dengan jelas.
     ```python
     # Penamaan yang baik
     total_harga = 100
     def hitung_diskon():
         pass
     
     # Penamaan yang buruk
     t = 100
     def hd():
         pass
     ```

### 4. **Struktur Program**
   - Setiap file Python biasanya berisi beberapa bagian:
     - **Import statements**: untuk mengimpor modul eksternal.
     - **Definisi fungsi dan kelas**: tempat mendefinisikan fungsi dan kelas.
     - **Kode utama**: sering kali dimulai dengan konstruk `if __name__ == "__main__":`
   
     Contoh struktur file Python:
     ```python
     import os

     def greet(name):
         print(f"Hello, {name}!")

     if __name__ == "__main__":
         greet("World")
     ```

### 5. **Penggunaan Library/Modul**
   - Modul atau library yang digunakan dalam Python dapat diimpor dengan menggunakan kata kunci `import`.
     ```python
     import math  # untuk mengimpor modul matematika
     print(math.sqrt(16))  # Menghitung akar kuadrat dari 16
     ```
   - Anda juga bisa mengimpor hanya bagian tertentu dari modul menggunakan `from ... import ...`.
     ```python
     from math import sqrt
     print(sqrt(16))  # Langsung menggunakan sqrt tanpa math.
     ```

### 6. **Struktur Kontrol**
   - Python mendukung kontrol alur standar seperti `if`, `else`, `elif`, `while`, dan `for`.
   - Contoh penggunaan `if` dan `else`:
     ```python
     x = 10
     if x > 5:
         print("x lebih besar dari 5")
     else:
         print("x kurang dari atau sama dengan 5")
     ```

   - Contoh penggunaan `for` dan `while`:
     ```python
     # Penggunaan for
     for i in range(5):
         print(i)

     # Penggunaan while
     i = 0
     while i < 5:
         print(i)
         i += 1
     ```

### 7. **Pemrograman Berorientasi Objek (OOP)**
   - Python mendukung paradigma OOP. Anda dapat membuat kelas menggunakan kata kunci `class`.
   - Contoh definisi kelas:
     ```python
     class Mobil:
         def __init__(self, merk, warna):
             self.merk = merk
             self.warna = warna

         def info(self):
             print(f"Mobil ini adalah {self.merk} berwarna {self.warna}")

     mobil_saya = Mobil("Toyota", "Merah")
     mobil_saya.info()
     ```

### 8. **Exceptions (Penanganan Kesalahan)**
   - Penanganan kesalahan dapat dilakukan menggunakan `try`, `except`, `else`, dan `finally`.
     ```python
     try:
         x = 10 / 0
     except ZeroDivisionError:
         print("Tidak bisa membagi dengan nol")
     else:
         print("Operasi berhasil")
     finally:
         print("Blok finally selalu dijalankan")
     ```

### 9. **Fungsi dan Parameter**
   - Fungsi didefinisikan dengan kata kunci `def`.
   - Parameter fungsi bisa memiliki nilai default dan mendukung parameter variabel dengan menggunakan `*args` (untuk argumen posisi) dan `**kwargs` (untuk argumen kata kunci).
     ```python
     def tambah(a, b=0):
         return a + b

     print(tambah(5))  # Output: 5
     print(tambah(5, 3))  # Output: 8
     ```

### 10. **List, Tuple, dan Dictionary**
   - **List**: Struktur data yang dapat diubah dan mendukung duplikasi.
     ```python
     daftar = [1, 2, 3, 4]
     daftar.append(5)
     ```
   - **Tuple**: Struktur data yang tidak dapat diubah dan mendukung duplikasi.
     ```python
     tupel = (1, 2, 3, 4)
     ```
   - **Dictionary**: Struktur data pasangan kunci-nilai.
     ```python
     kamus = {'nama': 'John', 'umur': 25}
     print(kamus['nama'])
     ```

### 11. **List Comprehension**
   - List comprehension adalah cara singkat untuk membuat list baru dengan iterasi.
     ```python
     angka = [1, 2, 3, 4, 5]
     kuadrat = [x**2 for x in angka]
     print(kuadrat)  # Output: [1, 4, 9, 16, 25]
     ```

### 12. **Fungsi Lambda**
   - Fungsi lambda adalah fungsi anonim yang dapat dituliskan dalam satu baris.
     ```python
     tambah = lambda x, y: x + y
     print(tambah(3, 4))  # Output: 7
     ```

### 13. **File Handling**
   - Python menyediakan cara untuk membaca dan menulis file menggunakan fungsi `open()`.
     ```python
     with open('file.txt', 'w') as file:
         file.write("Hello, World!")
     
     with open('file.txt', 'r') as file:
         print(file.read())
     ```

### 14. **Pengecekan Tipe Data**
   - Gunakan fungsi `type()` untuk mengecek tipe data suatu objek.
     ```python
     x = 10
     print(type(x))  # Output: <class 'int'>
     ```

### 15. **PEP 8 (Python Enhancement Proposal)**
   - PEP 8 adalah pedoman gaya penulisan kode Python yang berisi konvensi untuk menulis kode Python yang bersih dan mudah dibaca.
   - Beberapa poin penting dalam PEP 8:
     - Gunakan 4 spasi untuk indentasi.
     - Jangan gunakan spasi di sekitar operator `=` pada penugasan.
     - Pisahkan fungsi dan kelas dengan dua baris kosong.
     - Gunakan penamaan variabel yang jelas dan deskriptif.

Ini adalah garis besar aturan dan konvensi dasar dalam penulisan kode Python. Setiap aspek ini bertujuan untuk membuat kode Python lebih mudah dipahami dan dipelihara.
