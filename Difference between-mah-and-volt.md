Perbedaan antara **10000mAh** dan **7Volt** adalah dua hal yang berbeda dalam konteks spesifikasi daya dan baterai, yaitu **kapasitas** dan **tegangan**. Mari kita bahas lebih detail:

### 1. **10000mAh (Milliampere-hour)**
   - **mAh** adalah satuan kapasitas baterai, yang menunjukkan seberapa banyak daya yang bisa disimpan oleh baterai dan seberapa lama baterai tersebut dapat memberi daya pada perangkat yang mengkonsumsinya.
   - **10000mAh** berarti baterai tersebut dapat memberikan **10000 miliampere (mA)** selama **1 jam**, atau **1000 mA** selama 10 jam, atau lebih sedikit miliampere selama waktu yang lebih lama (misalnya 100mA selama 100 jam). Dengan kata lain, **mAh** menunjukkan seberapa banyak energi yang bisa disalurkan oleh baterai.
   - Semakin besar nilai mAh, semakin lama baterai dapat bertahan untuk memberikan daya, tetapi kapasitas ini tidak menyebutkan tegangan atau bagaimana energi itu dikalikan dengan tegangan untuk menghasilkan daya (Watt).

### 2. **7Volt**
   - **Volt (V)** adalah satuan yang mengukur **tegangan listrik** atau beda potensial antara dua titik. Tegangan ini mengukur "dorongan" atau kekuatan yang menggerakkan arus listrik melalui sirkuit.
   - **7Volt** menunjukkan bahwa baterai atau sumber daya tersebut memberikan tegangan sebesar 7V, yang cukup umum untuk beberapa perangkat dan sistem, terutama dalam baterai **7.4V Li-ion** yang sering digunakan pada berbagai perangkat.
   - Tegangan adalah faktor penting karena perangkat yang membutuhkan daya tertentu memerlukan tegangan yang sesuai. Misalnya, jika ESP32 membutuhkan 3.3V atau 5V untuk beroperasi, Anda perlu menyesuaikan atau mengonversi tegangan dari baterai 7V.

### Hubungan antara Kapasitas (mAh) dan Tegangan (Volt)
- Untuk mengukur **daya total** (dalam watt-jam, Wh), kita mengalikan **kapasitas (mAh)** dengan **tegangan (V)** dan kemudian membaginya dengan 1000 (karena 1Wh = 1000mAh * V).
  - **Formula**: 
    \[
    \text{Wh} = \frac{\text{mAh} \times \text{V}}{1000}
    \]
  - Sebagai contoh:
    - Jika baterai memiliki kapasitas **10000mAh** dan **tegangan 7V**, maka kapasitas energinya adalah:
    \[
    \text{Wh} = \frac{10000 \times 7}{1000} = 70 \text{Wh}
    \]
    Ini berarti baterai tersebut bisa menyediakan **70 watt-jam energi** sebelum habis.

### Perbedaan Utama:
- **10000mAh** mengukur **kapasitas** baterai (berapa lama baterai dapat memberikan daya pada perangkat).
- **7Volt** mengukur **tegangan** yang dikeluarkan oleh baterai atau sumber daya.

Jika Anda menggunakan baterai 10000mAh dengan tegangan 7V, Anda akan memiliki baterai dengan kapasitas energi **70Wh**, yang memberi tahu Anda berapa banyak energi yang bisa disuplai ke perangkat Anda, yang penting untuk mengetahui seberapa lama baterai itu bisa bertahan dengan perangkat tertentu yang membutuhkan daya.

### Kesimpulan:
- **10000mAh** menunjukkan seberapa banyak daya yang dapat diberikan oleh baterai (kapasitas).
- **7Volt** menunjukkan seberapa kuat dorongan listrik yang diberikan oleh baterai (tegangan).
- Keduanya bekerja bersama untuk menentukan **berapa lama** dan **berapa banyak daya** yang dapat Anda dapatkan dari baterai tersebut.
