
# **Dokumentasi API Buku dengan Express.js dan Penyimpanan Data di File JSON**

## **Deskripsi**
API ini memungkinkan pengguna untuk mengelola data buku (menambahkan, mengupdate, menampilkan, dan menghapus buku) menggunakan Express.js. Data buku disimpan secara permanen dalam file JSON (`books.json`), sehingga data akan tetap ada meskipun server dihentikan atau dijalankan ulang.

## **Prasyarat**
- Node.js dan npm sudah terinstal. Jika belum, Anda dapat mengunduhnya di [sini](https://nodejs.org/).
- Pengguna harus memiliki editor teks (seperti VSCode) untuk menulis kode.

---

## **Langkah-Langkah Pembuatan API**

### 1. **Membuat Folder Project**
Buka terminal dan buat folder baru untuk project API:
```bash
mkdir book-api
cd book-api
```

### 2. **Inisialisasi Project**
Inisialisasi project Node.js menggunakan npm:
```bash
npm init -y
```
Perintah ini akan membuat file `package.json` di dalam folder project.

### 3. **Instalasi Express**
Instal Express.js sebagai framework untuk API:
```bash
npm install express
```

### 4. **Membuat File `server.js`**
Buat file `server.js` yang akan berfungsi sebagai entry point API. Berikut adalah kode lengkapnya:

```js
const express = require('express');
const fs = require('fs');
const path = require('path');
const app = express();
const port = 3000;

// Lokasi file JSON
const booksFilePath = path.join(__dirname, 'books.json');

// Middleware untuk mengizinkan akses ke API dengan CORS
app.use(express.json());

// Fungsi untuk membaca data buku dari file JSON
const readBooksFromFile = () => {
    try {
        const data = fs.readFileSync(booksFilePath, 'utf8');
        return JSON.parse(data);
    } catch (err) {
        return []; // Jika file tidak ada atau error, kembalikan array kosong
    }
};

// Fungsi untuk menyimpan data buku ke file JSON
const saveBooksToFile = (books) => {
    fs.writeFileSync(booksFilePath, JSON.stringify(books, null, 2), 'utf8');
};

// Route untuk menampilkan daftar buku
app.get('/api/books', (req, res) => {
    const books = readBooksFromFile();
    res.json(books);
});

// Route untuk menampilkan detail buku berdasarkan ID
app.get('/api/books/:id', (req, res) => {
    const bookId = parseInt(req.params.id);
    const books = readBooksFromFile();
    const book = books.find(b => b.id === bookId);

    if (book) {
        res.json(book);
    } else {
        res.status(404).json({ message: 'Buku tidak ditemukan' });
    }
});

// Route untuk menambah buku baru
app.post('/api/books', (req, res) => {
    const { title, author, year } = req.body;

    if (!title || !author || !year) {
        return res.status(400).json({ message: 'Data buku tidak lengkap' });
    }

    const books = readBooksFromFile();
    const newBook = {
        id: books.length > 0 ? books[books.length - 1].id + 1 : 1, // ID otomatis berdasarkan urutan
        title,
        author,
        year
    };

    books.push(newBook);
    saveBooksToFile(books);
    res.status(201).json(newBook);
});

// Route untuk mengupdate data buku berdasarkan ID
app.put('/api/books/:id', (req, res) => {
    const bookId = parseInt(req.params.id);
    const { title, author, year } = req.body;

    const books = readBooksFromFile();
    const bookIndex = books.findIndex(b => b.id === bookId);

    if (bookIndex === -1) {
        return res.status(404).json({ message: 'Buku tidak ditemukan' });
    }

    // Update data buku
    books[bookIndex] = { id: bookId, title, author, year };
    saveBooksToFile(books);
    res.json(books[bookIndex]);
});

// Route untuk menghapus buku berdasarkan ID
app.delete('/api/books/:id', (req, res) => {
    const bookId = parseInt(req.params.id);
    const books = readBooksFromFile();
    const bookIndex = books.findIndex(b => b.id === bookId);

    if (bookIndex === -1) {
        return res.status(404).json({ message: 'Buku tidak ditemukan' });
    }

    // Hapus buku
    books.splice(bookIndex, 1);
    saveBooksToFile(books);
    res.status(204).send();
});

// Menjalankan server
app.listen(port, () => {
    console.log(`Server berjalan di http://localhost:${port}`);
});
```

### 5. **Membuat File `books.json`**
Buat file `books.json` yang akan menyimpan data buku dalam format JSON. File ini akan berada di direktori yang sama dengan `server.js`.

Contoh isi awal dari `books.json`:
```json
[
    { "id": 1, "title": "Belajar Express.js", "author": "John Doe", "year": 2023 },
    { "id": 2, "title": "Node.js untuk Pemula", "author": "Jane Doe", "year": 2022 },
    { "id": 3, "title": "Mengenal JavaScript", "author": "James Smith", "year": 2021 }
]
```

### 6. **Menjalankan Server**
Setelah semua file dibuat, jalankan server dengan perintah:
```bash
node server.js
```

Server akan berjalan pada `http://localhost:3000`.

---

## **API Endpoints**

### 1. **GET `/api/books`**
Mengambil daftar semua buku.

- **Request**: 
  - Method: `GET`
  - URL: `http://localhost:3000/api/books`
- **Response**: 
  - Status: `200 OK`
  - Body: Daftar buku dalam format JSON.
  ```json
  [
      { "id": 1, "title": "Belajar Express.js", "author": "John Doe", "year": 2023 },
      { "id": 2, "title": "Node.js untuk Pemula", "author": "Jane Doe", "year": 2022 },
      { "id": 3, "title": "Mengenal JavaScript", "author": "James Smith", "year": 2021 }
  ]
  ```

### 2. **GET `/api/books/:id`**
Mengambil detail buku berdasarkan ID.

- **Request**: 
  - Method: `GET`
  - URL: `http://localhost:3000/api/books/1`
- **Response**: 
  - Status: `200 OK`
  - Body: Data buku dengan ID yang sesuai.
  ```json
  { "id": 1, "title": "Belajar Express.js", "author": "John Doe", "year": 2023 }
  ```

### 3. **POST `/api/books`**
Menambahkan buku baru.

- **Request**: 
  - Method: `POST`
  - URL: `http://localhost:3000/api/books`
  - Body (JSON):
  ```json
  {
      "title": "Node.js Advanced",
      "author": "Alice Cooper",
      "year": 2024
  }
  ```
- **Response**: 
  - Status: `201 Created`
  - Body: Data buku yang baru ditambahkan.
  ```json
  { "id": 4, "title": "Node.js Advanced", "author": "Alice Cooper", "year": 2024 }
  ```

### 4. **PUT `/api/books/:id`**
Memperbarui data buku berdasarkan ID.

- **Request**: 
  - Method: `PUT`
  - URL: `http://localhost:3000/api/books/1`
  - Body (JSON):
  ```json
  {
      "title": "Belajar Express.js untuk Pemula",
      "author": "John Doe",
      "year": 2023
  }
  ```
- **Response**: 
  - Status: `200 OK`
  - Body: Data buku yang diperbarui.
  ```json
  { "id": 1, "title": "Belajar Express.js untuk Pemula", "author": "John Doe", "year": 2023 }
  ```

### 5. **DELETE `/api/books/:id`**
Menghapus buku berdasarkan ID.

- **Request**: 
  - Method: `DELETE`
  - URL: `http://localhost:3000/api/books/1`
- **Response**: 
  - Status: `204 No Content`
  - Body: Tidak ada (berhasil menghapus buku).

---

## **Catatan**
- **File `books.json`**: Semua data buku disimpan dalam file `books.json`. Data ini akan tetap ada meskipun server dijalankan ulang.
- **Handling Error**: Jika file JSON tidak ada atau terjadi error saat membaca atau menulis, API akan mengembalikan data kosong atau error yang sesuai.
- **ID Buku**: ID buku otomatis dihasilkan berdasarkan urutan ID terakhir yang ada dalam data buku.

---

Semoga dokumentasi ini membantu Anda dalam membuat API buku menggunakan Express.js dan penyimpanan data di file JSON!
