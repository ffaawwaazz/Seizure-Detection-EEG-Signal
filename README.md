# Seizure-Detection-EEG-Signal


# Performance Evaluation of Deep Learning Models for Automatic Seizure Detection

Proyek ini mengevaluasi performa berbagai arsitektur *Deep Learning* untuk deteksi kejang epileptik otomatis menggunakan sinyal **Scalp EEG** pediatrik dari database **CHB-MIT**. Fokus utama penelitian ini adalah menangani ketidakseimbangan kelas (*class imbalance*) dan membandingkan efektivitas model spasial-temporal terhadap data EEG.

## 📌 Ringkasan Proyek

Deteksi kejang secara manual sangat memakan waktu dan rentan terhadap kesalahan. Repositori ini mengimplementasikan pipeline *end-to-end* yang mengubah sinyal EEG mentah menjadi spektrogram waktu-frekuensi menggunakan **STFT** dan mengklasifikasikannya menggunakan tiga arsitektur utama:

1. 
**2D-CNN (Baseline):** Mengekstraksi fitur spasial dari spektrogram seperti gambar statis.


2. 
**LSTM:** Model sekuensial yang dirancang untuk menangkap dinamika temporal dan evolusi jangka panjang dari aktivitas otak.


3. 
**EEGNet (Specialized):** Arsitektur CNN kompak yang dioptimalkan khusus untuk sinyal EEG menggunakan *depthwise* dan *separable convolutions*.



## 📊 Hasil Eksperimen

Berdasarkan pengujian pada data riil yang tidak seimbang (*imbalanced test set*), **EEGNet** terbukti sebagai model paling tangguh:

| Model | Accuracy | Sensitivity (Recall Seizure) | Specificity (Recall Normal) |
| --- | --- | --- | --- |
| **EEGNet** | **100.00%** | **81.15%** | **99.98%** |
| CNN Baseline | 99.00% | 68.03% | 99.05% |
| LSTM Network | 95.00% | 38.52% | 95.14% |

> 
> **Analisis:** EEGNet secara signifikan mengungguli model lain karena kemampuannya mengekstraksi fitur spasial dan temporal secara efisien dengan parameter yang lebih sedikit.
> 
> 

## ⚙️ Metodologi

* 
**Dataset:** CHB-MIT Scalp EEG Database.


* **Preprocessing:**
* 
*Downsampling* dari 256 Hz ke 128 Hz untuk efisiensi komputasi.


* Segmentasi jendela 8 detik dengan *overlap* 50% (4 detik).


* Montage bipolar 18 saluran untuk mengurangi *noise*.




* **Strategi Penanganan Data:**
* 
**Training:** Menggunakan *under-sampling* (100% seizure, 1% normal) untuk menyeimbangkan kelas.


* 
**Testing:** Menggunakan data asli yang tidak seimbang untuk mensimulasikan skenario klinis nyata.


* 
**Cross-Validation:** Skema *Leave-Subject-Out* untuk memastikan generalisasi model pada pasien baru.





## 🛠️ Persyaratan Sistem

* PyTorch
* NumPy & Pandas
* Matplotlib & Seaborn (untuk visualisasi)
* SciPy (untuk STFT dan pemrosesan sinyal)

## 🚀 Cara Penggunaan

1. **Persiapan Data:** Unduh dataset CHB-MIT dan simpan dalam direktori `data/`.
2. 
**Preprocessing:** Jalankan skrip pemrosesan untuk menghasilkan spektrogram dan menangani batching memori.


3. **Training:** Jalankan `train.py` dengan memilih model (`cnn`, `lstm`, atau `eegnet`).
4. 
**Evaluasi:** Gunakan `evaluate.py` untuk melihat metrik performa dan visualisasi *flickering smoothing*.



## 📝 Kontributor

* 
**Rafif Fawwaz Kartika** - [5054231009@student.its.ac.id](mailto:5054231009@student.its.ac.id) 


* 
**Dimas Ahmad Satrio Wicaksono** - [5054231015@student.its.ac.id](mailto:5054231015@student.its.ac.id) 


* 
**Naufal Humam Maulana** - [5054231022@student.its.ac.id](mailto:5054231022@student.its.ac.id) 



---

**Apakah Anda ingin saya menambahkan bagian khusus mengenai visualisasi hasil atau penjelasan kode teknis tertentu?**
