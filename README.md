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

Berdasarkan EDA dan ringkasan dari AI, ditemukan beberapa profil segmen yang unik:

* **Segmen A:** Cenderung diisi oleh profesional dari bidang **Healthcare** dan **Engineer** dengan skor belanja **Rata-rata (Average)**. Mereka umumnya sudah menikah dan memiliki pengalaman kerja yang signifikan.
* **Segmen B:** Didominasi oleh profesional di bidang **Artist** dan **Engineer**, namun dengan skor belanja **Rendah (Low)**. Segmen ini memiliki rentang usia yang luas.
* **Segmen C:** Merupakan segmen dengan proporsi skor belanja **Tinggi (High)** yang paling signifikan. Banyak di antara mereka adalah **Eksekutif (Executive)** atau **Dokter (Doctor)**, seringkali dengan ukuran keluarga yang lebih besar.
* **Segmen D:** Mayoritas adalah profesional **Artist** dengan skor belanja **Rendah (Low)**. Ini adalah segmen dengan usia rata-rata tertinggi dan banyak anggotanya sudah tidak bekerja atau pensiun.

## 🎯 Kesimpulan & Rekomendasi

**Kesimpulan:**
Setiap segmen pelanggan memiliki karakteristik demografis dan perilaku yang berbeda secara signifikan. Pendekatan pemasaran "satu untuk semua" tidak akan efektif. Pemanfaatan AI seperti IBM Granite dapat mempercepat proses penerjemahan data mentah menjadi wawasan naratif yang dapat digunakan oleh tim bisnis.

**Rekomendasi:**
1.  **Untuk Segmen C (High Spenders):** Targetkan dengan produk premium (misalnya, mobil P4 atau P5) dan tawarkan layanan eksklusif. Kampanye pemasaran harus menonjolkan kemewahan, status, dan fitur-fitur canggih.
2.  **Untuk Segmen D (Low Spenders, Older):** Fokus pada produk yang ekonomis dan andal (misalnya, mobil P1). Komunikasi pemasaran harus menekankan nilai, keamanan, dan kemudahan penggunaan, cocok untuk keluarga atau individu yang lebih tua.
3.  **Untuk Segmen A & B (Mixed Professionals):** Tawarkan produk yang fleksibel dan seimbang dari segi harga dan fitur (misalnya, mobil P2 dan P3). Iklan bisa menyoroti efisiensi bahan bakar untuk profesional yang sering bepergian (Segmen A) dan desain/gaya untuk para seniman (Segmen B).
4.  **Strategi Pasar Baru:** Gunakan model klasifikasi ini (baik LLM untuk sampel cepat atau model ML tradisional untuk skala besar) untuk memprediksi segmen calon pelanggan di pasar baru dan langsung terapkan strategi komunikasi yang relevan sejak awal.

## 🤖 Penjelasan Dukungan AI (AI Support Explanation)

**IBM Granite** digunakan dalam dua peran utama dalam proyek ini:

1.  **Data Summarization:** Model ini digunakan untuk mengubah data statistik yang kering (seperti modus profesi, rentang usia) menjadi ringkasan naratif yang kaya. *Prompt* dirancang untuk meminta AI bertindak sebagai analis bisnis dan menjelaskan profil pelanggan kepada tim pemasaran. Ini membantu menjembatani kesenjangan antara data teknis dan pemahaman bisnis.
2.  **Data Classification:** Model ini diuji untuk tugas klasifikasi *few-shot*. Dengan memberinya beberapa contoh data pelanggan dan segmen yang benar, AI diminta untuk mengklasifikasikan data baru. Meskipun bukan pengganti model ML tradisional untuk akurasi skala besar, ini menunjukkan kemampuan LLM untuk melakukan tugas analitis kompleks dengan instruksi minimal, yang berguna untuk prototyping cepat atau analisis sampel kecil.
