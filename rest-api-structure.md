<h1>Simple Rest Api Structure</h1>

Berikut adalah struktur proyek REST API yang bisa kamu gunakan beserta penjelasan untuk masing-masing folder dan file yang ada di dalamnya:

```
|--config
|   |--db.js                // File konfigurasi database, misalnya untuk menghubungkan ke MongoDB atau MySQL
|   
|
|--controllers
|   |--userController.js    // Mengatur logika untuk endpoint terkait pengguna
|   |--authController.js    // Mengatur logika untuk autentikasi (login, registrasi, dsb.)
|   |--uploadController.js  // Mengatur logika untuk proses upload file
|
|--data
|   |--uploads/             // Folder untuk menyimpan file yang di-upload oleh pengguna
|
|--middleware
|   |--authMiddleware.js    // Middleware untuk memverifikasi token atau autentikasi pengguna
|   |--errorMiddleware.js   // Middleware untuk menangani error secara global
|
|--models
|   |--userModel.js         // Model untuk pengguna, digunakan dengan ORM atau ODM seperti Mongoose
|   |--uploadModel.js       // Model untuk menyimpan data file yang di-upload (misalnya nama file, path, dsb.)
|
|--routes
|   |--userRoutes.js        // Mendefinisikan route terkait pengguna (misalnya /register, /login)
|   |--uploadRoutes.js      // Mendefinisikan route terkait upload file (misalnya /upload)
|
|--package.json            // File konfigurasi proyek yang berisi dependencies dan skrip
|--.env                    // File konfigurasi lingkungan (environment variables) seperti port, database, dsb.
|--server.js               // File utama yang menjalankan server dan mengatur middleware serta routes
```

### Penjelasan:

- **`config/`**  
  Folder ini berisi file konfigurasi untuk berbagai kebutuhan aplikasi, seperti koneksi ke database, pengaturan variabel lingkungan, dan pengaturan lainnya.

- **`controllers/`**  
  Folder ini menyimpan file-file yang mengatur logika bisnis dari API. Setiap controller akan menangani permintaan HTTP yang diterima pada endpoint tertentu. Misalnya, `userController.js` mengatur logika untuk registrasi dan login, `uploadController.js` mengatur logika untuk menerima file yang di-upload.

- **`data/`**  
  Folder ini tempat menyimpan file-file yang di-upload oleh pengguna. Biasanya ini berisi subfolder (misalnya `uploads/`) yang digunakan untuk menyimpan file secara fisik di server.

- **`middleware/`**  
  Middleware berfungsi untuk memproses data sebelum sampai ke route handler, misalnya untuk autentikasi atau menangani error. `authMiddleware.js` memeriksa apakah permintaan pengguna memiliki token valid, sedangkan `errorMiddleware.js` bisa menangani error global dalam aplikasi.

- **`models/`**  
  Folder ini berisi model untuk database yang digunakan dalam aplikasi. Model ini menggambarkan struktur data dan fungsi-fungsi terkait dalam database, misalnya `userModel.js` untuk model pengguna dan `uploadModel.js` untuk data yang terkait dengan file upload.

- **`routes/`**  
  Folder ini mendefinisikan route untuk aplikasi. Setiap file route akan mengatur endpoint dan menghubungkannya dengan controller yang sesuai. Misalnya, `userRoutes.js` akan mendefinisikan rute untuk `/login`, `/register`, dsb., dan `uploadRoutes.js` mendefinisikan rute untuk `/upload` atau endpoint terkait upload file.

- **`package.json`**  
  File ini menyimpan metadata proyek seperti nama proyek, dependensi (misalnya Express, dotenv, multer), dan skrip untuk menjalankan aplikasi.

- **`.env`**  
  File ini menyimpan variabel lingkungan (environment variables) yang tidak ingin kamu simpan dalam kode sumber, seperti port server, kunci API, atau string koneksi database.

- **`server.js`**  
  Ini adalah file utama yang memulai aplikasi Express, mengatur middleware global, dan menghubungkan route yang sesuai. Ini adalah tempat di mana server akan dijalankan dan mendengarkan permintaan.

### Contoh `server.js`:

```javascript
const express = require('express');
const app = express();
const dotenv = require('dotenv');
const userRoutes = require('./routes/userRoutes');
const uploadRoutes = require('./routes/uploadRoutes');
const errorMiddleware = require('./middleware/errorMiddleware');

// Menggunakan dotenv untuk membaca file .env
dotenv.config();

// Middleware
app.use(express.json()); // Menggunakan middleware untuk parsing JSON
app.use('/uploads', express.static('data/uploads')); // Mengatur folder uploads sebagai statis

// Routes
app.use('/api/users', userRoutes);
app.use('/api/upload', uploadRoutes);

// Error handling middleware
app.use(errorMiddleware);

// Menjalankan server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
```

### Contoh `uploadController.js`:

```javascript
const multer = require('multer');
const path = require('path');
const Upload = require('../models/uploadModel');

// Setup storage engine for Multer
const storage = multer.diskStorage({
    destination: (req, file, cb) => {
        cb(null, 'data/uploads/');
    },
    filename: (req, file, cb) => {
        cb(null, Date.now() + path.extname(file.originalname)); // Nama file unik berdasarkan waktu
    }
});

const upload = multer({ storage });

// Controller to handle file upload
exports.uploadFile = async (req, res) => {
    try {
        if (!req.file) {
            return res.status(400).json({ message: 'No file uploaded' });
        }

        // Save file info to database
        const upload = new Upload({
            filename: req.file.filename,
            path: req.file.path
        });

        await upload.save();

        res.status(200).json({ message: 'File uploaded successfully', file: req.file });
    } catch (err) {
        res.status(500).json({ message: 'Server error' });
    }
};

exports.uploadMiddleware = upload.single('file'); // Middleware untuk meng-handle upload file
```

### Contoh `uploadRoutes.js`:

```javascript
const express = require('express');
const router = express.Router();
const uploadController = require('../controllers/uploadController');

// Route untuk upload file
router.post('/', uploadController.uploadMiddleware, uploadController.uploadFile);

module.exports = router;
```

Dengan struktur ini, kamu sudah siap mengembangkan aplikasi REST API yang mampu menangani file upload, autentikasi pengguna, dan banyak lagi.
