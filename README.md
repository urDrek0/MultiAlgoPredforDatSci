# Munich Traffic Flow & Occupancy Prediction 🚗📊

Proyek ini bertujuan untuk menganalisis dan memprediksi kondisi lalu lintas (arus/flow dan okupansi/occupancy) menggunakan data lalu lintas dari Munich. Proyek ini membandingkan kinerja tiga algoritma Machine Learning yang berbeda dan menggunakan logika Fuzzy untuk mengklasifikasikan status lalu lintas berdasarkan hasil prediksi.

## 📂 Struktur Repository

Repository ini terdiri dari empat notebook utama yang mencakup tahapan analisis data hingga prediksi model:

### 1. Exploratory Data Analysis (EDA)
- **File:** `EDAMunichforPred.ipynb`
- **Deskripsi:** Notebook ini berfokus pada pemahaman data awal.
- **Fitur Utama:**
  - Pemuatan data (*Data Loading*) dari Google Drive.
  - Manipulasi data menggunakan Pandas.
  - Visualisasi korelasi antar variabel menggunakan Heatmap (Seaborn) dan Grafik (Matplotlib).
  - Analisis distribusi data Flow dan Occupancy.

### 2. Machine Learning Models
Terdapat tiga pendekatan model yang digunakan untuk memprediksi `flow` dan `occupancy` berdasarkan input `interval` (waktu dalam detik):

* **A. Random Forest**
    * **File:** `RandomForestPredDSA.ipynb`
    * **Metode:** Menggunakan `RandomForestRegressor`.
    * **Fitur:** Memprediksi nilai numerik untuk arus dan okupansi, kemudian diklasifikasikan menggunakan fungsi fuzzy.

* **B. Polynomial Regression**
    * **File:** `PolynomReggPredDSA.ipynb`
    * **Metode:** Menggunakan `PolynomialFeatures` untuk mentransformasi fitur input, kemudian dimodelkan dengan Regresi Linear.
    * **Tujuan:** Menangkap pola non-linear pada data lalu lintas.

* **C. XGBoost (Extreme Gradient Boosting)**
    * **File:** `XboostPredDSA.ipynb`
    * **Metode:** Menggunakan `XGBRegressor`.
    * **Keunggulan:** Biasanya memberikan performa yang lebih baik dan efisien untuk data tabular berskala besar.

## 🛠️ Alur Kerja Sistem

1.  **Input User:**
    Sistem meminta input berupa `Interval` waktu dalam detik (range: 0 - 86400 detik, merepresentasikan 24 jam).
2.  **Prediksi Model:**
    Model (Random Forest/PolyReg/XGBoost) memprediksi dua nilai utama:
    - **Flow:** Jumlah kendaraan.
    - **Occupancy:** Kepadatan jalan.
3.  **Klasifikasi Fuzzy (`fuzzydefining`):**
    Hasil prediksi numerik diproses melalui logika fuzzy untuk menentukan status lalu lintas, misalnya:
    - *Lancar*
    - *Padat*
    - *Macet*

## 🚀 Cara Menjalankan

### Prasyarat
Pastikan Anda telah menginstal library Python berikut:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```
### Langkah Penggunaan
1. **Persiapan Data:**Pastikan dataset lalu lintas Munich sudah tersedia. Jika menggunakan Google Colab, pastikan Google Drive sudah di-mount dengan benar (sesuaikan path file di kode).
2. **Pilih Model:** Buka salah satu file .ipynb prediksi (misal: XboostPredDSA.ipynb).
3. **Jalankan Notebook:**Eksekusi semua sel (Run All) dari atas ke bawah untuk melatih model.
4. **Input Nilai:** Pada sel terakhir, Anda akan diminta memasukkan angka.

**Catatan:** Proyek ini dikembangkan menggunakan Google Colab. Kode mencakup perintah drive.mount('/content/drive'). Jika Anda menjalankannya di mesin lokal (VS Code / Jupyter Lab), harap hapus bagian tersebut dan sesuaikan lokasi file dataset Anda.
