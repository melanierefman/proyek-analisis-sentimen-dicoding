# Proyek Analisis Sentimen Shopee Reviews

Proyek ini bertujuan untuk menganalisis sentimen dari ulasan produk yang diambil dari dataset Shopee. Sentimen tersebut diklasifikasikan ke dalam tiga kategori: positif, negatif, dan netral. Berbagai model machine learning diuji untuk memprediksi sentimen berdasarkan teks ulasan produk.

## Deskripsi Dataset

Dataset yang digunakan adalah `shopee_reviews_filtered.csv`, yang berisi ulasan produk dari pengguna Shopee. Dataset ini mencakup informasi berikut:

- **username**: Nama pengguna yang memberikan ulasan.
- **comment**: Teks ulasan produk yang diberikan oleh pengguna.
- **rating**: Rating yang diberikan oleh pengguna (dari 1 hingga 5).
- **label**: Label sentimen yang telah ditentukan untuk masing-masing ulasan (positif, negatif, netral).

## Langkah-langkah Implementasi

### 1. **Memuat Dataset**
Dataset dimuat menggunakan `pandas` untuk analisis lebih lanjut. Informasi tentang dataset, seperti jumlah baris, kolom, dan tipe data, ditampilkan untuk memastikan data sudah siap untuk diproses.

### 2. **Pra-pemrosesan Data**
Beberapa langkah pra-pemrosesan dilakukan pada dataset:

- **Penanganan data yang hilang**: Baris dengan nilai kosong pada kolom `username` dihapus.
- **Pembersihan teks**: Menghapus angka dan tanda baca serta mengubah teks menjadi huruf kecil.
- **Penentuan label sentimen**: Menggunakan pustaka `TextBlob` untuk menentukan sentimen ulasan berdasarkan polaritas teks.

### 3. **Pemisahan Data**
Dataset dibagi menjadi data pelatihan dan data pengujian dengan rasio 80/20. Label sentimen yang telah ditentukan diubah menjadi format numerik menggunakan `LabelEncoder`.

### 4. **Eksperimen dengan Tiga Skema Pelatihan**
Tiga model berbeda diuji pada data yang telah diproses:

- **Model 1: SVM dengan TF-IDF**
  Model Support Vector Machine (SVM) diterapkan menggunakan representasi fitur berbasis TF-IDF untuk memproses teks.
  - SMOTE diterapkan pada data pelatihan untuk menangani masalah ketidakseimbangan kelas.
  
- **Model 2: Random Forest dengan TF-IDF**
  Model Random Forest digunakan dengan representasi fitur berbasis TF-IDF.

- **Model 3: Deep Learning dengan LSTM**
  Model jaringan saraf berbasis LSTM digunakan untuk memproses teks. Model ini dilatih dengan data yang diproses menggunakan Tokenizer dan padding.

### 5. **Evaluasi Model**
Setelah melatih ketiga model, hasil evaluasi dilakukan menggunakan metrik seperti akurasi dan laporan klasifikasi (`classification_report`). Visualisasi juga ditampilkan untuk memperlihatkan perubahan dalam loss dan akurasi selama pelatihan model LSTM.

### 6. **Perbandingan Model**
Model terbaik dibandingkan berdasarkan akurasi tertinggi. Model yang terpilih digunakan untuk memprediksi sentimen ulasan pada data pengujian, dan hasilnya dibandingkan dengan label asli untuk melihat seberapa baik model memprediksi sentimen.

## Persyaratan

Untuk menjalankan proyek ini, pastikan Anda memiliki pustaka berikut yang diinstal:

```bash
pip install pandas numpy scikit-learn imbalanced-learn tensorflow textblob matplotlib
```

## Struktur Proyek

```
.
├── shopee_reviews_filtered.csv     # Dataset ulasan Shopee
├── analisis_sentimen.ipynb        # Notebook yang berisi implementasi
├── README.md                      # Dokumentasi proyek
```

## Hasil

Setelah melatih ketiga model, hasil evaluasi menunjukkan bahwa model terbaik dipilih berdasarkan akurasi tertinggi. Perbandingan antara label asli dan prediksi untuk model terbaik ditampilkan untuk menunjukkan kinerja model dalam memprediksi sentimen ulasan.

## Penutup

Proyek ini menunjukkan penggunaan berbagai model machine learning untuk analisis sentimen pada teks ulasan produk. Penggunaan TF-IDF dan LSTM menunjukkan hasil yang baik, dengan LSTM menunjukkan kinerja yang sangat baik dalam memahami teks yang lebih kompleks.

---
