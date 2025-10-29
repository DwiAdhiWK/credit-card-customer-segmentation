# Judul Project
Credit Card Customer Segmentation

## Repository Outline
- dateset-description.png - deskripsi dataset yang akan digunakan 
- model.pkl - model KMeans 
- P1G6_dwi_adhi.csv - dataset yang diambil dari Google BigQuery
- P1G6_dwi_adhi.ipynb - Notebook projek
- notebook_inference.ipynb - inference untuk data baru

## Problem Background
Anda adalah seorang Data Scientist disebuah perusahaan bernama Bank Berlian. Tim marketing meminta anda untuk melakukan Customer Segmentation dari data kartu kredit yang sudah Anda peroleh sebelumnya. Data ini merupakan data informasi penggunaan kartu kredit selama 6 bulan terakhir. 

Atas permintaan tersebut, Anda akan membuat proses Clustering dan memberikan rekomendasi bisnis dari setiap Customer Cluster yang terbentuk. Selain itu, tim marketing juga meminta insight bisnis lain dari data yang Anda gunakan yang akan Anda jawab pada bagian Exploratory Data Analysis (EDA).

## Project Output
Output dari projek ini adalah insight mengenai Customer Segmentation serta insight binsis lain nya data sebuah model yang dapat memprediksi data baru masuk kedalam segmentasi yang mana.

## Data
Data ini diambil dari data credit-card-information 

## Method
Projek ini menerapkan Clustering dengan Algoritma KMeans bedasarkan data customer yang disiapkan oleh tim mareketing. Banyak nya kluster optimal ditentukan bedasarkan analisis nilai K menggunakan metode Elbow dan Silhouette

## Exploratory Data Analysis 1
Insight 1
  Berdasarkan heatmap, kolom PURCHASES, BALANCE, dan PAYMENTS memiliki nilai korelasi terhadap TENURE masing-masing sebesar 0.13, 0.062, dan 0.20.
Kolom PURCHASES dan PAYMENTS menunjukkan korelasi positif yang lemah (di atas 0.1) dengan TENURE, sedangkan BALANCE memiliki nilai mendekati nol, menandakan tidak ada hubungan yang signifikan dengan TENURE.

Insight 2
Dari bar chart terlihat bahwa pelanggan dengan TENURE = 12 bulan memiliki nilai PURCHASES dan PAYMENTS tertinggi.
Hal ini logis karena semakin lama penggunaan kartu kredit, semakin besar total pembelian dan pembayaran yang dilakukan.

Insight 3
Scatter plot menunjukkan adanya hubungan positif antara TENURE dan CREDIT_LIMIT, di mana semakin lama pelanggan menggunakan kartu, semakin tinggi batas kredit yang dimiliki.
Namun, CREDIT_LIMIT juga dipengaruhi oleh PAYMENTS dan PURCHASES, sehingga tidak bisa dijadikan rekomendasi bisnis secara terpisah.
Pelanggan dengan TENURE = 12 bulan memiliki batas kredit tertinggi, yang memungkinkan mereka melakukan pembelian lebih besar.

## K Analysis
Metode Elbow digunakan dengan melihat nilai Within-Cluster Sum of Squares (WCSS) atau k_inertia.
WCSS mengukur total variasi dalam setiap kluster — semakin kecil nilainya, semakin baik tingkat kedekatan antar data di dalam kluster.
Berdasarkan grafik Elbow, penurunan tajam terjadi pada K = 3 dan penurunan kedua pada K = 4. Setelah K = 4, penurunan tidak lagi signifikan, sehingga kluster ideal kemungkinan berada di K = 3 atau 4.

Selanjutnya, metode Silhouette digunakan untuk validasi. Nilai Silhouette berkisar antara -1 hingga 1, dengan arti:

1: kluster sangat baik dan terpisah jelas,

0: terdapat tumpang tindih antar kluster,

-1: titik data salah dikluster.

Dari hasil analisis, K = 3 memiliki nilai Silhouette Score sebesar 0.2498, yang merupakan nilai tertinggi kedua dan menunjukkan pemisahan kluster yang cukup jelas dengan tumpang tindih minimal.
Berdasarkan kedua metode ini, jumlah kluster yang digunakan adalah K = 3.

## Exploratory Data Analysis 2
Cluster 0 — Pembeli Aktif dengan Cicilan
Pelanggan dalam cluster ini memiliki nilai PURCHASES_TRX dan INSTALLMENTS_PURCHASES yang cukup tinggi, menandakan mereka sering melakukan pembelian dan kerap menggunakan sistem cicilan.
Mereka menunjukkan perilaku belanja yang konsisten dan cocok untuk direkomendasikan kartu kredit, karena sudah terbiasa dengan transaksi berbasis kredit.

Cluster 1 — Pengguna Rendah
Kelompok ini memiliki nilai PURCHASES_TRX dan INSTALLMENTS_PURCHASES yang rendah, artinya jarang bertransaksi menggunakan kartu kredit.
Mereka kurang bergantung pada kartu kredit dan kemungkinan lebih memilih metode pembayaran lain. Oleh karena itu, mereka tidak menjadi target utama rekomendasi kartu kredit.

Cluster 2 — Pembelanja Aktif dan Sering Cicilan
Cluster ini memiliki nilai PURCHASES_TRX dan INSTALLMENTS_PURCHASES yang tinggi, menandakan aktivitas belanja yang sangat intens.
Mereka adalah pembeli aktif dan sangat cocok untuk direkomendasikan kartu kredit karena berpotensi memberikan keuntungan tinggi.

## Conclusion and Recommendation
Berdasarkan hasil analisis Customer Segmentation menggunakan algoritma K-Means, pelanggan Bank Berlian dapat dikelompokkan menjadi tiga cluster utama:

Cluster 0: Pelanggan yang cukup sering melakukan pembelian, meskipun saldo mereka tidak terlalu tinggi.

Cluster 1: Pelanggan yang jarang bertransaksi dan memiliki aktivitas kartu kredit rendah.

Cluster 2: Pelanggan yang sangat aktif bertransaksi dan sering melakukan pembelian.

Secara keseluruhan, model K-Means berhasil membedakan pola perilaku pelanggan dengan baik.
Cluster 0 dan Cluster 2 merupakan segmen yang paling potensial untuk direkomendasikan kartu kredit, terutama Cluster 2, karena kelompok ini menunjukkan tingkat keterlibatan dan potensi keuntungan yang lebih tinggi.
