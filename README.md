# **Beyond the Click Trap: Evaluating Platform Optimization and Funnel Friction Using Two-Proportion Z-Test 🎯📊**

## 📌 Project Overview

Proyek ini bertujuan untuk mengevaluasi dampak eksperimen optimasi platform (Variant B) terhadap efisiensi conversion funnel perusahaan. Analisis difokuskan pada pengujian signifikansi statistik untuk mendeteksi apakah perubahan performa didorong oleh fitur baru atau sekadar variasi acak, sekaligus mendiagnosis titik friksi platform yang memicu penurunan konversi hilir.

## ⚠️ Problem Statement

Berdasarkan studi dari Harvard Business Review mengenai efisiensi platform, peningkatan pada indikator interaksi awal (seperti rasio klik) tidak selalu berkorelasi positif dengan konversi akhir. Superstore menghadapi fenomena "Click Trap" pada Variant B, di mana pembaruan platform berhasil memicu minat hulu (+0.04% CTR) namun performanya merosot tajam pada metrik transaksi lanjutan, mengindikasikan adanya friksi operasional yang mengancam stabilitas revenue platform.

## 📂 About Data

* Data File: AB-Testing-Analysis
* Format File: Comma-Separated Values (CSV)
* Baris: ~100,000 (Generated Dataset)
* Kolom: 10+ (User ID, Variant, CTR, Add to Cart, Purchase, Revenue, Age Group, dll)
* Tahun Publikasi (Last Update): 2026
* Sumber: Dibimbing.id Bootcamp Mini Project

## 🛠️ Tech Stack & Tools

* Language: Python
* Libraries: Pandas (Data Preprocessing), Statsmodels & SciPy (Two-Proportion Z-Test), Seaborn & Matplotlib (EDA)
* Environment: Jupyter Notebook

## 💡 Key Insights

1. Data Anomaly Detection (Integritas Log Sistem)
* Analisis distribusi Uniform dan korelasi antar-kolom yang mendekati nol mengonfirmasi bahwa dataset ini merupakan data sintetik (generated).
* Proses data scrubbing mendeteksi anomali kritis berupa 77.472 baris data logging eror di mana nilai revenue tetap tercatat meskipun status purchase bernilai nol.

2. Statistical Inference (Validasi Z-Test)
* Pengujian Two-Proportion Z-Test pada tingkat kepercayaan 95% menghasilkan p-value > 0.05 untuk seluruh metrik utama (CTR, ATCR, CR).
* Secara ilmiah terbukti bahwa seluruh variasi angka antar-varian tidak signifikan dan murni terjadi akibat faktor kebetulan atau variasi acak sampling (random noise).

3. Funnel Leakage (Friction Trap Platform)
* Variant B memicu bias interaksi di mana ketertarikan awal pengguna naik (+0.04% CTR), namun mengalami pembalikan performa di tahap lanjutan.
* Terjadi kebocoran alur konversi (funnel leakage) yang menurunkan Add to Cart Rate (ATCR) sebesar -0.03% dan Conversion Rate (CR) sebesar -0.16% akibat mismatch ekspektasi pasca-klik.

4. Demographic & Revenue Disconnect (Segmen Premium)
* Kelompok pengguna usia matang (Age Group 50+) memegang profil daya beli tertinggi dengan rata-rata nilai transaksi organik sebesar 9.184.
* Pada Variant B, segmen premium ini merespons positif di awal (CTR naik dari 1.95% ke 2.03%) namun mengalami penurunan spending riil yang sangat sensitif sebesar -6.2% (dari 9.189 menjadi 8.619).

## 🚀 Actionable Recommendations

* Pembatalan Implementasi Fitur (Do Not Deploy): Direkomendasikan untuk melakukan rollback dan tidak merilis Variant B ke lingkungan produksi karena terbukti tidak memberikan dampak positif yang signifikan secara statistik.
* Audit Arsitektur Data Logging: Menginstruksikan tim engineering untuk mengaudit infrastruktur pelacakan event guna memperbaiki galat logika antara pencatatan transaksi (purchase) dan nilai pendapatan (revenue).
* Review Preferensi Segmen & Platform: Melakukan investigasi mendalam terhadap perilaku belanja kelompok usia 50+ dibarengi dengan pelacakan perilaku berbasis Traffic Source, Device, dan Browser untuk mengisolasi titik hambatan platform.
