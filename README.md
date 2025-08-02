# Analyzing-Data-with-IBM-Granite-Model

# Proyek Capstone: Analisis Segmentasi Pelanggan Menggunakan IBM Granite

## 📜 Gambaran Umum Proyek (Project Overview)

Proyek ini bertujuan untuk menganalisis data pelanggan sebuah perusahaan otomotif untuk mengklasifikasikan mereka ke dalam segmen yang telah ditentukan (A, B, C, D). Latar belakangnya adalah perusahaan ingin memasuki pasar baru dan berencana menggunakan strategi segmentasi yang sama seperti di pasar yang ada. Analisis ini memanfaatkan **IBM Granite**, sebuah Large Language Model (LLM), untuk mendapatkan wawasan mendalam, meringkas karakteristik setiap segmen, dan menguji kemampuan klasifikasi AI pada data pelanggan baru.

**Tujuan:**
1.  Melakukan analisis data eksplorasi (EDA) untuk memahami karakteristik dari setiap segmen pelanggan.
2.  Menggunakan IBM Granite untuk membuat **ringkasan naratif (summarization)** dari profil setiap segmen.
3.  Menguji kemampuan IBM Granite dalam melakukan **klasifikasi *few-shot*** untuk memprediksi segmen pelanggan baru.
4.  Memberikan rekomendasi bisnis yang dapat ditindaklanjuti berdasarkan hasil analisis.

## 📊 Dataset

Dataset yang digunakan adalah "Customer Segmentation" dari Analytics Vidhya, yang tersedia di Kaggle.
* **Link Dataset:** [Customer Segmentation Dataset](https://www.kaggle.com/datasets/kaushiksuresh147/customer-segmentation)
* **Deskripsi:** Dataset ini berisi informasi demografis dan perilaku pelanggan seperti `Gender`, `Age`, `Profession`, `Work_Experience`, `Spending_Score`, dan `Family_Size`. Variabel target adalah `Segmentation`.

## ⚙️ Proses Analisis

Proses analisis data dilakukan secara sistematis melalui beberapa tahapan:

1.  **Setup Lingkungan:** Menginstall semua *library* yang diperlukan (`pandas`, `seaborn`, `langchain_community`, `replicate`) di Google Colab.
2.  **Pemuatan & Pembersihan Data:** Memuat dataset, memeriksa tipe data, dan menangani nilai yang hilang (*missing values*) dengan metode imputasi (median untuk numerik, modus untuk kategorikal).
3.  **Analisis Data Eksplorasi (EDA):** Membuat visualisasi data (misalnya, *bar charts*) untuk membandingkan distribusi fitur-fitur seperti `Profession` dan `Spending_Score` di antara keempat segmen pelanggan.
4.  **Analisis Berbasis AI - Summarization:**
    * Data untuk setiap segmen diisolasi.
    * Statistik deskriptif sederhana (rentang usia, profesi umum) dari data tersebut diekstrak.
    * Informasi ini dimasukkan ke dalam *prompt* yang dirancang untuk **IBM Granite** agar menghasilkan ringkasan naratif yang mudah dipahami tentang profil tipikal pelanggan di segmen tersebut.
5.  **Analisis Berbasis AI - Classification:**
    * Sebuah *prompt* *few-shot* dibuat, yang berisi beberapa contoh pelanggan beserta segmennya yang benar.
    * Data pelanggan baru kemudian diberikan ke **IBM Granite** untuk diprediksi segmennya. Ini mendemonstrasikan kemampuan LLM untuk melakukan penalaran dan klasifikasi berdasarkan konteks yang diberikan.

## 💡 Insight & Temuan (Insight & Findings)

Analisis data yang diperkaya dan diringkas oleh IBM Granite mengungkapkan empat persona pelanggan yang sangat berbeda:

* **Segmen D: Generasi Muda & Profesional Kesehatan yang Hemat**
    Ini adalah segmen dengan **rata-rata usia termuda (38 tahun)**. Mereka didominasi oleh profesional **Kesehatan**, diikuti oleh Seniman. Perilaku belanja mereka sangat jelas: mayoritas absolut berada di kategori **Skor Belanja Rendah**. Status pernikahan mereka paling seimbang (hampir 50/50 menikah dan lajang), menunjukkan mereka berada di tahap awal kehidupan dewasa.

* **Segmen A: Profesional Kreatif & Kesehatan yang Fleksibel**
    Dengan rata-rata usia 43 tahun, segmen ini merupakan kelompok besar yang beragam. Profesi utamanya adalah **Seniman**, diikuti oleh profesional **Kesehatan** dan **Hiburan**. Meskipun mayoritas memiliki Skor Belanja Rendah, mereka memiliki proporsi Skor Belanja Rata-rata yang signifikan, menunjukkan fleksibilitas finansial yang lebih besar daripada Segmen D.

* **Segmen B: Para Seniman Mapan & Berorientasi Keluarga**
    Segmen ini memiliki rata-rata usia sedikit lebih tua (45 tahun) dan **persentase pernikahan yang lebih tinggi (66%)** dibandingkan Segmen A. Profesi mereka juga berpusat pada **Seni** dan **Hiburan**. Pola belanja mereka mirip dengan Segmen A, namun dengan basis pelanggan yang lebih mapan dan berorientasi keluarga.

* **Segmen C: Profesional Elit & Berdaya Beli Tinggi**
    Ini adalah segmen premium dengan **rata-rata usia tertua (49 tahun)** dan **persentase pernikahan tertinggi (72%)**. Profesi mereka unik, dengan **Pengacara (Lawyer/Advokat)** masuk dalam 3 besar bersama Seniman. Yang terpenting, mereka memiliki **distribusi skor belanja paling seimbang** dan proporsi pelanggan dengan **Skor Belanja Tinggi** yang paling signifikan.

## 🎯 Kesimpulan & Rekomendasi

**Kesimpulan:**
Segmentasi pelanggan tidak hanya valid, tetapi juga mengungkapkan perjalanan hidup pelanggan—dari profesional muda yang hemat (Segmen D) hingga kalangan elit yang mapan (Segmen C). Setiap segmen memerlukan produk dan pendekatan pemasaran yang sangat berbeda. Kesalahan terbesar adalah memperlakukan Segmen D sebagai segmen tua atau Segmen A dan B sebagai segmen yang identik.

**Rekomendasi Bisnis yang Telah Disesuaikan:**

1.  **Untuk Segmen C (Profesional Elit):**
    * **Produk:** Fokuskan pada mobil paling premium (**P4, P5**).
    * **Pemasaran:** Targetkan dengan pesan yang menonjolkan **kemewahan, status, pencapaian, dan keamanan** untuk keluarga yang mapan. Kampanye bisa menyasar kalangan profesional hukum dan eksekutif.

2.  **Untuk Segmen D (Generasi Muda Hemat):**
    * **Produk:** Tawarkan mobil paling ekonomis dan efisien (**P1**).
    * **Pemasaran:** Ini adalah target untuk "mobil pertama". Pesan harus menonjolkan **nilai, efisiensi bahan bakar, fitur teknologi modern, dan kemudahan cicilan**. Targetkan profesional muda di sektor kesehatan.

3.  **Untuk Segmen A (Kreatif & Fleksibel):**
    * **Produk:** Tawarkan mobil serbaguna yang menyeimbangkan gaya dan fungsi (**P2, P3**).
    * **Pemasaran:** Kampanye harus menyoroti **fleksibilitas, desain yang stylish** untuk para seniman, dan **kepraktisan** untuk rutinitas kerja profesional kesehatan.

4.  **Untuk Segmen B (Seniman Mapan):**
    * **Produk:** Tawarkan model yang sama dengan Segmen A (**P2, P3**), namun dengan penekanan pada paket aksesoris keluarga.
    * **Pemasaran:** Pesan dapat berfokus pada **keandalan, ruang kabin yang nyaman untuk keluarga**, tanpa meninggalkan unsur **gaya** yang dihargai oleh para seniman.


## 🤖 Penjelasan Dukungan AI (AI Support Explanation)

**IBM Granite** digunakan dalam dua peran utama dalam proyek ini:

1.  **Data Summarization:** Model ini digunakan untuk mengubah data statistik yang kering (seperti modus profesi, rentang usia) menjadi ringkasan naratif yang kaya. *Prompt* dirancang untuk meminta AI bertindak sebagai analis bisnis dan menjelaskan profil pelanggan kepada tim pemasaran. Ini membantu menjembatani kesenjangan antara data teknis dan pemahaman bisnis.
2.  **Data Classification:** Model ini diuji untuk tugas klasifikasi *few-shot*. Dengan memberinya beberapa contoh data pelanggan dan segmen yang benar, AI diminta untuk mengklasifikasikan data baru. Meskipun bukan pengganti model ML tradisional untuk akurasi skala besar, ini menunjukkan kemampuan LLM untuk melakukan tugas analitis kompleks dengan instruksi minimal, yang berguna untuk prototyping cepat atau analisis sampel kecil.
