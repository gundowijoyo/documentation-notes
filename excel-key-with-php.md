# Simple Alfabet
 Anda ingin membuat urutan alfabet yang dimulai dari `a` hingga `z`, kemudian berlanjut ke `aa`, `ab`, `ac`, dan seterusnya, seperti sistem penghitungan berbasis huruf. Setelah `z`, urutannya melanjutkan ke kombinasi dua huruf seperti `aa`, `ab`, `ac`, dan seterusnya, lalu `ba`, `bb`, dan seterusnya.

Berikut adalah contoh kode PHP untuk menghasilkan urutan seperti itu:

### Kode PHP:

```php
<?php
// Jumlah urutan yang ingin dihasilkan
$limit = 100;  // Misalnya 100 urutan pertama

// Looping untuk menghasilkan urutan alfabet
for ($i = 0; $i < $limit; $i++) {
    echo numToAlpha($i) . "<br>";
}

// Fungsi untuk mengubah angka menjadi urutan alfabet (a-z, aa, ab, ac, ... )
function numToAlpha($num) {
    $letters = '';
    
    while ($num >= 0) {
        $letters = chr($num % 26 + 97) . $letters;  // Menambahkan huruf ke kiri
        $num = floor($num / 26) - 1;  // Mengurangi angka dan membaginya dengan 26
        if ($num < 0) break;
    }
    
    return $letters;
}
?>
```

### Penjelasan:
1. **`numToAlpha($num)`**: Fungsi ini mengonversi angka ke dalam urutan alfabet yang Anda inginkan.
    - Menggunakan operasi modulus (`%`) untuk mengambil sisa pembagian angka dengan 26, dan mengubahnya menjadi huruf sesuai urutan `a-z`.
    - Setelah `z`, proses akan melanjutkan ke kombinasi dua huruf (`aa`, `ab`, `ac`, dll).
    - Setelah mencapai `z`, angka berikutnya menghasilkan `aa`, `ab`, dan seterusnya.
2. **`chr($num % 26 + 97)`**: Fungsi `chr()` mengonversi angka menjadi karakter ASCII. `97` adalah kode ASCII untuk huruf 'a'. Modulus digunakan untuk memastikan urutannya tetap dalam rentang `a-z`.

### Hasil:
Jika Anda menggunakan `100` sebagai jumlah urutan, outputnya akan seperti ini:

```
a
b
c
...
z
aa
ab
ac
...
az
ba
bb
bc
...
```

Urutan akan terus meningkat sesuai dengan format yang Anda inginkan, yaitu dari `a` hingga `z`, lalu `aa`, `ab`, `ac`, dan seterusnya, hingga batas yang Anda tentukan di variabel `$limit`.
