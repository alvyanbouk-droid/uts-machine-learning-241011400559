# UTS Machine Learning – Linear & Logistic Regression

- **Nama** : Alfianus Feri Bouk
- **NIM** : 241011400559
- **Kelas** : Reg B
- **random_state** : 59 (2 digit terakhir NIM)

## Isi Repositori
- `tugas_UTS.ipynb` – notebook lengkap (kode, output, grafik, analisis)
- `Ads_Data.csv` – data biaya iklan vs penjualan (40 baris)
- `Email_Data.csv` – data email spam (60 baris)

Semua model dan metrik dibuat sendiri dengan NumPy (scikit-learn hanya dipakai pada soal bonus).

## Ringkasan Hasil

### Bagian A – Linear Regression (Ads_Data)
- Persamaan: ŷ = 27.7414 + 9.0967 · BiayaIklan
- Data testing: MAE 4.7274, RMSE 5.5641, **R² = 0.9231** (training R² = 0.9423)
- Gradient descent (5000 iterasi): lr 0.001 terlalu lambat, lr 0.02 sama dengan normal equation, lr 0.1 divergen (overflow, `nan`)
- Prediksi: 4.5 juta → 68.68 juta; 7 juta → 91.42 juta; 12 juta → 136.90 juta (ekstrapolasi, kurang dapat dipercaya)

### Bagian B – Logistic Regression (Email_Data)
- P(Spam) = σ(−11.5670 + 1.0532 · JumlahLink + 0.9422 · KataPromo)
- Data testing: **accuracy 0.9333**, precision 1.0, recall 0.75, F1 0.8571 (TN 11, FP 0, FN 1, TP 3)
- Decision boundary: KataPromo = 12.2772 − 1.1179 · JumlahLink
- Threshold yang dipilih: **0.7** (FP dianggap lebih merugikan daripada FN)
- Prediksi email baru: E1 Bukan Spam, E2 Bukan Spam, E3 Spam, E4 Spam

### Bonus – scikit-learn
- Linear Regression: hasil identik dengan implementasi sendiri
- Logistic Regression: akurasi sama; koefisien berbeda karena regularisasi L2 default (`C=1.0`) dan konvergensi solver
