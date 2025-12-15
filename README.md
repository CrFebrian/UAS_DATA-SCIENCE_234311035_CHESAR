# 📘 Judul Proyek
*Klasifikasi Emosi Musik Berdasarkan Fitur Akustik Menggunakan Pendekatan Baseline Model, Machine Learning dan Deep Learning*

## 👤 Informasi
- *Nama*:*Chesar Rizqi Febrianto*  
- *Repo*:*https://github.com/CrFebrian/UAS_DATA-SCIENCE_234311035_CHESAR *  
- *Video*: *( MASIH KOSONG )*

---

# 1. 🎯 Ringkasan Proyek
- Membangun sistem klasifikasi emosi suara berbasis fitur akustik untuk membedakan emosi happy dan angry  
- Melakukan data preparation dan feature engineering pada data audio sebelum pemodelan  
- Mengembangkan 3 model klasifikasi : *Baseline*, *Advanced* (Random Forest) , *Deep Learning* (MLP)  
- Melakukan evaluasi performa model dan menentukan model terbaik serta menyimpan model dan scaler untuk penggunaan kembali 

---

# 2. 📄 Problem & Goals
*Problem Statements:*
- Data audio cenderung mengandung noise dan variasi nilai yang cukup tinggi antar fitur, sehingga dibutuhkan proses data preparation yang sistematis meliputi data cleaning, feature engineering, dan data transformation sebelum dilakukan pemodelan.
- Pemilihan model yang kurang sesuai dengan karakteristik data berpotensi menghasilkan performa yang tidak stabil, khususnya pada model deep learning yang sensitif terhadap ukuran dataset dan kompleksitas fitur.
- Perlu diketahui fitur akustik spesifik apa (misalnya: apakah Tempo, RMS Energy, atau Spectral Centroid) yang menjadi faktor penentu utama dalam membedakan kemarahan dan kebahagiaan.

*Goals:*
- Membangun sistem klasifikasi emosi berbasis fitur akustik yang mampu membedakan dua kelas emosi yaitu happy dan angry dengan performa yang terukur menggunakan metrik evaluasi yang relevan  
- Menerapkan dan mengevaluasi tiga pendekatan pemodelan yang berbeda yaitu model baseline, model machine learning, dan model deep learning untuk melihat perbedaan performa serta karakteristik masing masing model.
- Mengidentifikasi fitur-fitur audio yang paling dominan (Feature Importance) dalam mempengaruhi keputusan model.
- Menghasilkan model akhir yang tersimpan (saved model) beserta scaler-nya agar dapat digunakan kembali untuk prediksi data baru secara konsisten.

---
## 📁 Struktur Folder
```
project/
│
├── data/                   # Dataset (tidak di-commit, download manual)
│
├── notebooks/              # Jupyter notebooks
│   └── ML_Project.ipynb
│
├── src/                    # Source code
│   
├── models/                 # Saved models
│   ├── model_baseline.pkl
│   ├── model_rf.pkl
│   └── model_cnn.h5
│
├── images/                 # Visualizations
│   └── r
│
├── requirements.txt        # Dependencies
├── .gitignore
└── README.md
```
---

# 3. 📊 Dataset
- *Sumber :* *https://archive.ics.uci.edu/dataset/862/turkish+music+emotion*
- *Jumlah Data:* *400 Baris, 51 Fiture* 
- *Tipe :* *Tabular* 

### Fitur Utama
*Dataset asli memiliki 51 fitur, namun proyek ini hanya menggunakan 6 fitur utama yang relevan dengan pendidikan, ekonomi, dan pengangguran.
Berikut tabel fitur yang digunakan:*

| Fitur | Deskripsi |
| RMSenergy_Mean | Nilai rata-rata energi sinyal audio (Root Mean Square) yang merepresentasikan tingkat kekuatan atau intensitas suara |
| Fitur | Deskripsi |


---

# 4. 🔧 Data Preparation
- Cleaning : Pemeriksaan missing values, data duplikat, outliers, serta range nilai pada keenam fitur akustik. Dataset sebelumnya terdapat duplicasi namun setelah pemeriksaan, data berada dalam kondisi bersih dan tidak memerlukan proses cleaning tambahan. 
- Transformasi : Memilih 6 fitur akustik utama yang paling relevan dalam merepresentasikan karakteristik emosi suara (happy dan angry), yaitu RMSenergy_Mean, Tempo_Mean, Spectralcentroid_Mean, Spectralflatness_Mean, MFCC_Mean_1, dan EntropyofSpectrum_Mean.
- Scaling : Menerapkan StandardScaler untuk menormalkan fitur sehingga memiliki mean 0 dan standar deviasi 1. Proses scaling ini penting untuk menjaga stabilitas training, terutama pada model deep learning dan memastikan konsistensi preprocessing.
- Splitting : Pembagian dataset menjadi data training dan data test menggunakan X_train, X_test, y_train, y_test dengan random_state tetap untuk menjaga reproducibility. Pada model deep learning, sebagian data training digunakan sebagai validation set selama proses training.

---

# 5. 🤖 Modeling
- Model 1 – Baseline : *Linier Regression*
- Model 2 – Advanced ML : *Random Forest*
- Model 3 – Deep Learning : *Multilayer Perceptron*

---

# 6. 🧪 Evaluation
**Metrik:** Accuracy / F1 / MAE / MSE (pilih sesuai tugas)

### Hasil Singkat
| Model | Score | Catatan |
|-------|--------|---------|
| Baseline | [...] | |
| Advanced | [...] | |
| Deep Learning | [...] | |

---

# 7. 🏁 Kesimpulan
- Model terbaik: [...]  
- Alasan: [...]  
- Insight penting: [...]  

---

# 8. 🔮 Future Work
- [ ] Tambah data  
- [ ] Tuning model  
- [ ] Coba arsitektur DL lain  
- [ ] Deployment  

---

# 9. 🔁 Reproducibility
Gunakan environment:
