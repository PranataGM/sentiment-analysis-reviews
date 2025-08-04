# Deteksi Sentimen Ulasan (Sentiment Analysis of Reviews)

---

## Gambaran Umum Proyek

Proyek ini bertujuan untuk membangun sistem Machine Learning yang mampu menganalisis teks ulasan (misalnya ulasan produk atau film) dan secara otomatis mengklasifikasikannya sebagai memiliki sentimen **positif** atau **negatif/netral**. Di tengah banjirnya ulasan daring, kemampuan untuk secara otomatis memahami opini pelanggan adalah aset tak ternilai bagi bisnis dan analisis pasar.

Proyek ini menggunakan pendekatan **Supervised Learning** dengan fokus pada **Natural Language Processing (NLP)** untuk tugas klasifikasi teks.

---

## Dataset

Dataset yang digunakan berisi koleksi ulasan teks beserta label sentimennya. **Perhatian: File data tidak disertakan dalam repositori ini karena ukurannya yang besar.**

* **File Data yang Dibutuhkan**:
    * `train_data.csv` (untuk pelatihan model)
    * `test_data.csv` (untuk pengujian model)
* **Struktur Data**: Kedua file CSV memiliki dua kolom utama:
    * `sentence`: Berisi teks ulasan.
    * `sentiment`: Berisi label sentimen (0 untuk negatif/netral, 1 untuk positif).
* **Distribusi Sentimen (Data Latih)**: Dataset latih memiliki distribusi sentimen yang sangat seimbang, dengan sekitar 50.33% sentimen negatif/netral dan 49.67% sentimen positif.

---

## Alur Kerja Data Science

Proyek ini mengikuti alur kerja standar dalam pembangunan model Machine Learning untuk NLP:

### 1. Pengumpulan & Pemahaman Data
* Memuat `train_data.csv` dan `test_data.csv` ke dalam Pandas DataFrame.
* Menganalisis statistik dasar, tipe data, dan distribusi sentimen.

### 2. Pra-pemrosesan Teks (Text Preprocessing)
* **Pembersihan Teks**: Menerapkan fungsi pra-pemrosesan sederhana untuk mengubah semua teks menjadi huruf kecil dan menghapus karakter non-alfabet (angka dan tanda baca). Ini membantu mengurangi *noise* dan membuat teks lebih konsisten.

### 3. Vektorisasi Teks (Text Vectorization)
* Mengubah teks yang sudah bersih menjadi representasi numerik yang dapat dipahami oleh algoritma Machine Learning.
* Menggunakan **TF-IDF Vectorizer (Term Frequency-Inverse Document Frequency)**: Teknik ini memberikan bobot pada kata berdasarkan seberapa sering muncul dalam dokumen dan seberapa jarang muncul di seluruh korpus, sehingga kata-kata penting memiliki bobot lebih tinggi. `stop_words='english'` digunakan untuk menghapus kata-kata umum bahasa Inggris.

### 4. Pembangunan & Pelatihan Model
* Menggunakan model **Multinomial Naive Bayes**: Algoritma ini sangat cocok untuk tugas klasifikasi teks dengan fitur berbasis frekuensi (seperti TF-IDF).
* Model dilatih pada data latih yang sudah di-*vectorize* (`X_train_tfidf`) dan label sentimen yang sesuai (`y_train`).

### 5. Evaluasi Model
* Model dievaluasi pada **test set** (`X_test_tfidf`, `y_test`) menggunakan metrik-metrik klasifikasi standar:
    * **Accuracy**
    * **Precision**
    * **Recall**
    * **F1-Score**
    * **Classification Report** (detail metrik per kelas)
    * **Confusion Matrix** (visualisasi performa prediksi)

* **Hasil Performa Model Multinomial Naive Bayes:**
    * Accuracy: `0.7967`
    * Precision (untuk sentimen positif): `0.8225`
    * Recall (untuk sentimen positif): `0.7637`
    * F1-Score (untuk sentimen positif): `0.7920`

* **Kesimpulan Evaluasi**:
    Model Multinomial Naive Bayes menunjukkan performa yang solid dalam mengklasifikasikan sentimen ulasan, dengan akurasi hampir 80%. Metrik precision, recall, dan F1-score yang seimbang untuk kedua kelas (positif dan negatif/netral) menunjukkan bahwa model ini bekerja dengan baik pada dataset yang seimbang ini.

---

## Bagaimana Menjalankan Proyek Ini?

1.  **Clone repositori ini:**
    ```bash
    git clone [https://github.com/YourGitHubUsername/sentiment-analysis-reviews.git](https://github.com/YourGitHubUsername/sentiment-analysis-reviews.git)
    cd sentiment-analysis-reviews
    ```
2.  **Dapatkan Dataset:**
    Anda memerlukan file `train_data.csv` dan `test_data.csv`. Karena ukurannya besar, file-file ini tidak disertakan langsung dalam repositori. **Pastikan Anda memiliki kedua file ini di komputer lokal Anda dari sumber aslinya.**
3.  **Tempatkan Dataset:**
    Unggah kedua file CSV (`train_data.csv` dan `test_data.csv`) ke **Google Drive Anda**.
4.  **Buka di Google Colab:**
    Buka file `sentiment_analysis_review.ipynb` (nama notebook yang Anda gunakan) di Google Colab.
5.  **Sesuaikan Path Data:**
    Di bagian kode "Muat Data" dalam notebook, pastikan Anda:
    * Menjalankan `drive.mount('/content/drive')` untuk menghubungkan Colab ke Google Drive Anda.
    * Mengganti `base_path = '/content/drive/MyDrive/Dataset_ML/Sentiment/'` dengan path folder yang **benar** di Google Drive Anda tempat `train_data.csv` dan `test_data.csv` berada.
6.  **Jalankan Sel-sel Kode:**
    Jalankan setiap sel kode secara berurutan (`Runtime > Run all`) untuk mereplikasi seluruh alur kerja proyek.

---

## Teknologi yang Digunakan

* **Python**
* **Pandas** (untuk manipulasi data)
* **Re** (untuk regular expressions dalam pra-pemrosesan teks)
* **Scikit-learn** (untuk TF-IDF Vectorizer dan model Multinomial Naive Bayes, serta metrik evaluasi)
* **Matplotlib** (untuk visualisasi)
* **Seaborn** (untuk visualisasi)
* **Google Colab** (sebagai lingkungan pengembangan)
