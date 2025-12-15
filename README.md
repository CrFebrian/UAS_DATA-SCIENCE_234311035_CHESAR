# 📘 Judul Proyek
*Klasifikasi Emosi Musik Berdasarkan Fitur Akustik Menggunakan Pendekatan Baseline Model, Machine Learning dan Deep Learning*

## 👤 Informasi
- *Nama*: *Chesar Rizqi Febrianto*  
- *Repo*: https://github.com/CrFebrian/UAS_DATA-SCIENCE_234311035_CHESAR
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
*Dataset asli memiliki 51 fitur, namun proyek ini hanya menggunakan 6 fitur utama paling relevan untuk klasifikasi emosi suara (happy dan angry).
Berikut tabel fitur yang digunakan:*

| Fitur                  | Deskripsi                                                                                                        |
|------------------------|------------------------------------------------------------------------------------------------------------------|
| RMSenergy_Mean         | Nilai rata-rata energi sinyal audio (Root Mean Square) yang merepresentasikan tingkat kekuatan atau intensitas suara |
| Tempo_Mean             | Nilai rata-rata tempo audio yang menggambarkan kecepatan ritme suara, berkaitan dengan ekspresi emosi                |
| Spectralcentroid_Mean  | Rata-rata titik pusat spektrum frekuensi yang menunjukkan tingkat kecerahan suara                                    |
| Spectralflatness_Mean  | Rata-rata tingkat keseragaman spektrum yang mengindikasikan apakah suara bersifat tonal atau noise-like              |
| MFCC_Mean_1            | Nilai rata-rata koefisien MFCC pertama yang merepresentasikan karakteristik spektral utama sinyal audio              |
| EntropyofSpectrum_Mean | Rata-rata entropi spektrum yang menggambarkan tingkat kompleksitas dan ketidakaturan sinyal audio                    |

---

# 4. 🔧 Data Preparation
- Cleaning : Pemeriksaan missing values, data duplikat, outliers, serta range nilai pada keenam fitur akustik. Dataset sebelumnya terdapat duplicasi namun setelah pemeriksaan, data berada dalam kondisi bersih dan tidak memerlukan proses cleaning tambahan. 
- Transformasi : Memilih `6` fitur akustik utama yang paling relevan dalam merepresentasikan karakteristik emosi suara (happy dan angry), yaitu RMSenergy_Mean, Tempo_Mean, Spectralcentroid_Mean, Spectralflatness_Mean, MFCC_Mean_1, dan EntropyofSpectrum_Mean.
- Scaling : Menerapkan StandardScaler untuk menormalkan fitur sehingga memiliki mean 0 dan standar deviasi 1. Proses scaling ini penting untuk menjaga stabilitas training, terutama pada model deep learning dan memastikan konsistensi preprocessing.
- Splitting : Pembagian dataset menjadi data training dan data test menggunakan `X_train, X_test, y_train, y_test` dengan random_state tetap untuk menjaga reproducibility. Pada model deep learning, sebagian data training digunakan sebagai validation set selama proses training.

---

# 5. 🤖 Modeling
- Model 1 – Baseline : *Linier Regression*
- Model 2 – Advanced ML : *Random Forest*
- Model 3 – Deep Learning : *Multilayer Perceptron*

---

# 6. 🧪 Evaluation
**Metrik:** Accuracy / F1 / MAE / MSE

### Hasil Singkat
| Model                 | Accuracy | Precision | Recall | F1-Score | Training Time (s) | Inference Time (s) |
|:---------------------:|:--------:|:---------:|:------:|:--------:|:-----------------:|:------------------:|
| Model 1 (Baseline)    | 0.7436   | 0.7143    | 0.7895 | 0.7500   | 0.0125            | 0.0021             |
| Model 2 (Random Forest) | 0.8462   | 0.7600    | 1.0000 | 0.8636   | 0.6588            | 0.0230             |
| Model 3 (Deep Learning) | 0.7949   | 0.7200    | 0.9474 | 0.8182   | 4.7943            | 0.1509             |
---

# 7. 🏁 Kesimpulan
- Model terbaik: Model Random Forest (Advanced Machine Learning) 
- Alasan:
  - Model Random Forest mampu memberikan performa yang paling seimbang berdasarkan metrik evaluasi (accuracy, precision, recall, dan F1-score), dengan waktu training yang relatif efisien serta kemampuan interpretasi yang baik melalui analisis feature importance. Dibandingkan model deep learning, Random Forest memberikan hasil yang sebanding dengan kompleksitas yang lebih rendah dan lebih stabil pada data uji.  
- Insight penting:
  - Fitur akustik seperti energi, tempo, dan karakteristik spektral terbukti efektif dalam membedakan emosi happy dan angry.
  - Model dengan kompleksitas menengah dapat memberikan performa optimal tanpa perlu arsitektur deep learning yang terlalu kompleks.
  - Proses preprocessing yang konsisten (scaling dan penyimpanan model) sangat penting untuk memastikan sistem dapat digunakan kembali pada data audio baru secara andal.  

---

# 8. 🔮 Future Work
[ x ] Menambah kelas emosi selain happy dan angry
[ x ] Menggunakan fitur audio tambahan atau spectrogram
[ x ] Melakukan tuning hyperparameter model
[ x ] Mengembangkan sistem ke tahap deployment

---

# 9. 🔁 Reproducibility
Gunakan environment:

Library Utama:

python >= 3.9
numpy
pandas
scikit-learn
matplotlib
seaborn
joblib

python >= 3.9
numpy
pandas
scikit-learn
tensorflow
matplotlib
joblib
