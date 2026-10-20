# UTS Machine Learning – Linear & Logistic Regression

- **Nama  :** Ditia Wulandari
- **NIM   :** 241011401219
- **Kelas :** Reg B (05TPLM003)
- **random_state :** 19 (2 digit terakhir NIM)

## Isi Repositori
| File | Keterangan |
|---|---|
| `tugas_UTS.ipynb` | Notebook jawaban lengkap (sudah dijalankan, output dan grafik terlihat) |
| `Ads_Data.csv` | Dataset biaya iklan vs penjualan (40 data) |
| `Email_Data.csv` | Dataset email spam (60 data) |

Model dan metrik diimplementasikan sendiri dengan NumPy. scikit-learn hanya dipakai pada soal bonus.

## Ringkasan Hasil

### Bagian A – Linear Regression (split 80:20, 32 train / 8 test)
- Persamaan (normal equation): **ŷ = 27,72 + 9,13 · BiayaIklan**
- Setiap kenaikan biaya iklan 1 juta Rp, penjualan naik sekitar 9,13 juta Rp.

| | MAE | MSE | RMSE | R² |
|---|---|---|---|---|
| Training | 4,962 | 41,913 | 6,474 | 0,934 |
| Testing | 2,940 | 13,397 | 3,660 | 0,979 |

- Gradient descent (5000 iterasi): lr 0,001 terlalu lambat (belum konvergen), lr 0,02 sama dengan normal equation, lr 0,1 divergen (`nan`).
- Prediksi: 4,5 juta → 68,78; 7 juta → 91,60; 12 juta → 137,22 (ekstrapolasi, kurang dapat dipercaya).

### Bagian B – Logistic Regression (split 75:25, 45 train / 15 test)
- Persamaan: **P(Spam) = σ(−8,41 + 0,727 · JumlahLink + 0,729 · KataPromo)**
- Log loss turun dari 0,693 ke 0,324 dan stabil.
- Data testing: accuracy = 1,0, precision = 1,0, recall = 1,0, F1 = 1,0 (accuracy training 0,867).
- Threshold dipilih 0,7 (mengutamakan precision karena FP lebih merugikan).
- Prediksi email baru: E1 bukan spam, E2 bukan spam, E3 spam, E4 spam.

### Bonus – scikit-learn
- Linear Regression: identik dengan implementasi sendiri.
- Logistic Regression: koefisien berbeda karena scikit-learn memakai regularisasi L2 (C=1) secara default.
