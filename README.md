# Tugas UTS Machine Learning

**Nama:** Muhamad Fatir  
**NIM:** 241011402714  
**Kelas:** 05 TPLM 005 / Reg B

## Tentang Tugas
Notebook ini menjawab dua pertanyaan:
- Apakah biaya iklan bisa membantu memperkirakan penjualan?
- Apakah sebuah email kemungkinan merupakan spam?

Untuk pertanyaan pertama, model mencari garis yang paling sesuai dengan data. Untuk pertanyaan kedua, model menghitung peluang email termasuk spam lalu memilih label berdasarkan batas peluang. Notebook juga berisi grafik, animasi proses Gradient Descent, cara memeriksa hasil, jawaban konsep, contoh prediksi, dan perbandingan bonus.

Perhitungan model utama dibuat dengan NumPy. scikit-learn hanya digunakan pada bagian bonus. Angka acak ditetapkan `14`, sesuai dua digit terakhir NIM.

## File
```text
.
├── README.md
├── tugas_UTS.ipynb
├── Ads_Data.csv
└── Email_Data.csv
```

`Ads_Data.csv` berisi 40 catatan biaya iklan dan penjualan. `Email_Data.csv` berisi 60 email, dengan jumlah tautan, kata promosi, dan label spam. Letakkan kedua CSV bersama notebook agar mudah ditemukan.

## Cara Menjalankan
Perlu Python dan Jupyter. Pasang pustaka yang dipakai notebook:
```bash
python -m pip install numpy pandas matplotlib scikit-learn jupyter
```

Buka `tugas_UTS.ipynb` di Jupyter atau VS Code, pilih kernel Python tersebut, lalu pilih **Run All**. Bonus perbandingan memerlukan scikit-learn.

## Hasil Terakhir
Angka ini berasal dari notebook yang dijalankan dengan angka acak 14. Sebanyak 32 dari 40 catatan iklan dipakai untuk membuat model; 8 sisanya untuk mengujinya. Untuk email, pembagiannya 45 untuk belajar dan 15 untuk pengujian.

- Garis perkiraan penjualan: `y_hat = 29.145637 + 8.855992 × BiayaIklan`. Pada garis ini, tambahan biaya iklan Rp1 juta berkaitan dengan kenaikan perkiraan penjualan sekitar Rp8.856 juta.
- Pada 8 catatan iklan uji, rata-rata besar selisih perkiraan sekitar Rp4.751 juta (`RMSE`); nilai `R²` sebesar `0.9728` menunjukkan garis mengikuti pola data uji dengan baik. Jumlah data uji kecil, jadi hasil ini bukan jaminan untuk bulan lain.
- Percobaan Gradient Descent: ukuran langkah `0.001` membaik lebih lambat; `0.02` mendekati garis hitung langsung; `0.1` membuat kesalahan membesar dan dihentikan pada putaran 141. Percobaan yang gagal tetap ditampilkan di notebook.
- Pada 15 email uji dengan batas peluang `0.5`, 14 dinilai benar. Ada 1 email biasa yang salah ditandai spam dan tidak ada spam yang terlewat. Ringkasan: accuracy `0.9333`, precision `0.8889`, recall `1.0000`, F1 `0.9412`; tabel hitungannya `[[bukan spam benar=6, salah ditandai spam=1], [spam terlewat=0, spam benar=8]]`.
- Batas peluang `0.3`, `0.5`, dan `0.7` kebetulan menghasilkan label yang sama untuk kumpulan uji ini. Batas awal tetap `0.5` karena tidak ada aturan biaya kesalahan atau data validasi terpisah untuk memilih batas lain.
- Pada bonus, kedua cara menghasilkan garis penjualan yang sama. Koefisien model spam berbeda karena scikit-learn menambahkan aturan bawaan untuk menahan koefisien; hasil penilaian pada email uji kebetulan sama.

Hasil berlaku untuk data dan pembagian yang tercantum di atas. Model belum diuji pada kumpulan data lain.
