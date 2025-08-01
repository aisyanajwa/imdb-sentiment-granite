# Sentiment Classification of IMDB Movie Reviews using IBM Granite

#### Hacktiv8 Capstone Project: Data Classification and Summarization Using IBM Granite

---

## Dataset

- **Sumber**: [IMDB Dataset of 50K Movie Reviews](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)

- **Deskripsi**: Dataset untuk klasifikasi sentimen biner (positif/negatif) dengan 50.000 ulasan film.
- [Link Colab](https://colab.research.google.com/drive/1IkPIArdamVR-KEuibIrAahxjfqAFtQPs?usp=sharing) dan [Link PPT](https://www.canva.com/design/DAGuzsVr5KY/6aJeFhWEJREEoFVXK95tMQ/view?utm_content=DAGuzsVr5KY&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hcb63847c3b)

---

## Project Overview

Proyek ini bertujuan untuk mengklasifikasikan sentimen (positif atau negatif) dari ulasan film dalam dataset IMDB menggunakan model AI IBM Granite 3.3-8B Instruct, sebuah Large Language Model (LLM). Hasil klasifikasi dibandingkan dengan label asli untuk mengukur akurasi dan performa model.

---

## Analysis Process

### 1. Pengambilan dan Pemrosesan Data
- Dataset dimuat menggunakan `pandas`.
- Sampel acak sebanyak 100 ulasan diambil dari total 50.000 data untuk evaluasi.

### 2. Penggunaan IBM Granite LLM
- Model diakses melalui LangChain yang memungkinkan integrasi langsung dengan LLM.
- Setiap ulasan diklasifikasikan menggunakan prompt eksplisit berbasis teks.
  Prompt yang digunakan:
  ```
  You are a sentiment classifier.
  
  Classify the sentiment of the following movie review as either:
  - positive
  - negative
  
  Respond with ONLY one word: either "positive" or "negative". No explanation. No punctuation.
  ```


### 3. Pembersihan Output
- Output model disaring agar hanya menyisakan hasil "positive" atau "negative".
- Pembersihan dilakukan menggunakan aturan sederhana berbasis pencocokan kata kunci ('positive' dan 'negative') pada string.

### 4. Evaluasi Akurasi
- Perbandingan antara label `sentiment` (asli) dan `sentiment_ibm` (hasil prediksi).
- Akurasi model pada sampel data mencapai 93%.

### 5. Visualisasi
Visualisasi data dilakukan dengan bantuan LangChain `pandas_dataframe_agent`, yaitu agent berbasis LLM yang dapat menjalankan instruksi analitik langsung terhadap `DataFrame`. Visualisasi yang dilakukan:
- Bar chart distribusi sentimen.
- Confusion matrix untuk mengevaluasi performa klasifikasi.
- Perbandingan visual sentimen asli dan hasil model.

---

## Insight & Findings

- Distribusi Seimbang: Dataset asli memiliki distribusi seimbang antara sentimen positif dan negatif, cocok untuk evaluasi objektif.
- Akurasi Tinggi: Model IBM Granite berhasil mengklasifikasikan sentimen dengan akurasi 93% pada sampel data.
- Presisi dan Recall Tinggi: Model menunjukkan presisi dan recall tinggi untuk kedua label.
- Prediksi Positif Lebih Hati-hati: Model cenderung sedikit lebih hati-hati dalam memprediksi positif dibanding negatif (Recall positif = 0.90 vs negatif = 0.96).
- Performa Stabil: Model cenderung stabil dan tidak terlalu agresif, terbukti dari F1-score yang seimbang (0.93 untuk kedua kelas).
- Output Perlu Pembersihan: Meskipun prompt disusun dengan spesifik, model kadang tetap menghasilkan format seperti <positive> atau kalimat tambahan. Oleh karena itu, perlu proses pembersihan tambahan.
- Tidak Ada Bias Ekstrem: Tidak ditemukan kecenderungan bias ekstrem terhadap salah satu kelas.

---

## Conclusion & Recommendation

### Conclusion

Model IBM Granite menunjukkan performa yang sangat baik dalam tugas klasifikasi sentimen terhadap dataset IMDB pada 100 sampel acak. Dengan akurasi 93%, serta presisi dan recall yang tinggi pada kedua label (positif dan negatif), model ini terbukti mampu melakukan analisis sentimen secara andal. Hasil evaluasi menunjukkan bahwa model bersifat seimbang dan tidak bias terhadap salah satu kelas, dengan F1-score yang merata. Namun, masih ditemukan beberapa output yang memerlukan proses pembersihan tambahan akibat ketidakkonsistenan format hasil dari model.

### Recommendation

- Model IBM Granite cocok digunakan untuk analisis ulasan pelanggan dalam industri film, e-commerce, dan layanan konsumen.
- Karena hasil klasifikasi kadang tidak konsisten secara format, disarankan untuk menambahkan tahap *post-processing* untuk membersihkan output model sebelum dianalisis lebih lanjut.
- Untuk mendapatkan gambaran performa yang lebih representatif, evaluasi sebaiknya diperluas pada sampel yang lebih besar dan lebih bervariasi, termasuk data dari sumber lain seperti media sosial.
- Model ini dapat diintegrasikan ke dalam pipeline analisis opini secara otomatis untuk membantu pengambilan keputusan berbasis sentimen pelanggan.

---

## AI Support Explanation

Dalam proyek ini, Artificial Intelligence (AI) digunakan untuk melakukan klasifikasi sentimen menggunakan model IBM Granite 3.3-8B Instruct melalui integrasi LangChain.

### Langkah-langkah Penggunaan:

1. Penyusunan Prompt Klasifikasi
   - Setiap ulasan dikirim ke model dengan instruksi eksplisit untuk mengklasifikasikan sebagai “positive” atau “negative”.
   - Prompt disusun agar model hanya menghasilkan satu kata sebagai output.

2. Eksekusi dengan LangChain Agent
   - Digunakan `create_pandas_dataframe_agent()` untuk membuat agen yang dapat berinteraksi langsung dengan DataFrame.
   - Agen digunakan untuk menjalankan analisis seperti visualisasi, evaluasi akurasi, pembuatan confusion matrix, hingga insight otomatis.

---

## AI Benefits

- Akurasi tinggi: Model mampu mencapai akurasi 93% pada sampel data.
- Efisiensi waktu: Proses klasifikasi dan analisis dilakukan secara otomatis dan cepat.
- Fleksibilitas: Model dapat dijalankan melalui perintah natural language untuk tugas-tugas analitik seperti klasifikasi, visualisasi, dan rekomendasi.
- Lebih sederhana dibanding pendekatan NLP tradisional: Dengan menggunakan LLM seperti IBM Granite, proses klasifikasi tidak memerlukan tahapan-tahapan manual seperti preprocessing teks, tokenisasi, ekstraksi fitur, dan pelatihan model secara eksplisit. Cukup dengan menyusun prompt yang tepat, hasil klasifikasi bisa langsung diperoleh dari model, sehingga mempermudah dan mempercepat workflow analisis.
---

Kesimpulannya, AI—khususnya IBM Granite LLM—membuktikan kemampuannya untuk menyederhanakan dan mengotomatisasi proses klasifikasi sentimen secara efisien, tanpa mengorbankan akurasi.
