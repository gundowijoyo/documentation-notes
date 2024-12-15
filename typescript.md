Untuk membuat program TypeScript yang mencetak sesuatu ke konsol, mulai dari awal (termasuk instalasi TypeScript, konfigurasi, dan build), ikuti langkah-langkah berikut:

### 1. Persiapan Lingkungan

Sebelum memulai, pastikan Node.js telah terinstal. Kamu bisa memeriksa instalasi Node.js dengan menjalankan perintah berikut di terminal:

```bash
node -v
```

Jika Node.js belum terinstal, unduh dan instal dari [situs resmi Node.js](https://nodejs.org/).

### 2. Inisialisasi Proyek

1. **Buat folder proyek baru** dan masuk ke dalamnya.

```bash
mkdir proyek-typescript
cd proyek-typescript
```

2. **Inisialisasi proyek Node.js** untuk membuat file `package.json`.

```bash
npm init -y
```

### 3. Instalasi TypeScript

1. **Instal TypeScript secara lokal** ke dalam proyek.

```bash
npm install typescript --save-dev
```

2. **Instal ts-node** untuk menjalankan TypeScript langsung tanpa perlu melakukan build manual setiap kali.

```bash
npm install ts-node --save-dev
```

3. **Instal tipe definisi untuk Node.js** (opsional tapi disarankan untuk pengembangan di Node.js).

```bash
npm install @types/node --save-dev
```

### 4. Konfigurasi TypeScript

1. **Buat file konfigurasi TypeScript (`tsconfig.json`)**.

```bash
npx tsc --init
```

Ini akan membuat file `tsconfig.json`. Secara default, TypeScript akan mencari file sumber di folder `src` dan menghasilkan output di folder `dist`.

2. **Sesuaikan pengaturan di `tsconfig.json`** agar sesuai dengan kebutuhan proyek kamu. Contoh pengaturan minimal:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

- `rootDir`: Menentukan folder tempat file TypeScript berada (misalnya `./src`).
- `outDir`: Menentukan folder tempat file JavaScript hasil kompilasi disimpan (misalnya `./dist`).

### 5. Menulis Kode TypeScript

1. **Buat folder `src`** untuk menyimpan file sumber TypeScript.

```bash
mkdir src
```

2. **Buat file `index.ts`** di dalam folder `src` dan tulis kode TypeScript berikut untuk mencetak ke konsol:

```typescript
// src/index.ts
console.log("Hello, World! Ini adalah program TypeScript!");
```

### 6. Menjalankan TypeScript secara Langsung dengan `ts-node` (Opsional)

Untuk menjalankan TypeScript tanpa perlu build, kamu bisa menggunakan `ts-node`.

```bash
npx ts-node src/index.ts
```

Ini akan langsung mengeksekusi file `index.ts` dan menampilkan output di konsol.

### 7. Build dan Menjalankan Kode TypeScript

Untuk membuild file TypeScript dan menjalankan JavaScript yang dihasilkan, ikuti langkah-langkah berikut.

1. **Build proyek TypeScript** dengan menjalankan perintah:

```bash
npx tsc
```

Ini akan mengkompilasi file TypeScript dari folder `src` dan menempatkan file JavaScript hasil build di folder `dist`.

2. **Jalankan file JavaScript hasil build**:

```bash
node dist/index.js
```

Ini akan mengeksekusi file JavaScript yang dihasilkan di folder `dist` dan mencetak output ke konsol.

### 8. Menambahkan Skrip ke `package.json`

Agar lebih mudah, kamu bisa menambahkan skrip untuk build dan menjalankan kode di `package.json`.

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "ts-node src/index.ts"
}
```

- `npm run build`: Untuk mengkompilasi TypeScript.
- `npm run start`: Untuk menjalankan hasil build.
- `npm run dev`: Untuk menjalankan kode TypeScript langsung (tanpa perlu build).

### 9. Menjalankan Proyek

- Untuk menjalankan proyek dalam mode pengembangan (langsung menjalankan TypeScript):

```bash
npm run dev
```

- Untuk build proyek dan menjalankan hasilnya:

```bash
npm run build
npm run start
```

### 10. Menyimpulkan

Dengan langkah-langkah di atas, kamu telah membuat proyek TypeScript yang dapat mencetak "Hello, World!" ke konsol. Kamu juga telah mengonfigurasi build TypeScript, menjalankan kode langsung dengan `ts-node`, dan menambahkan skrip untuk mempermudah eksekusi di proyek.

Semoga membantu! Jika ada pertanyaan lebih lanjut, jangan ragu untuk bertanya.
