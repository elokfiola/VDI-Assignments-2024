# Tugas 1 VDI

**Nama**: Elok Fiola  
**NIM**: 122450051  
**Kelas**: RC
-----
## Resume Artikel 
**Judul:** [Making data visualization more efficient and effective: a survey](https://sci-hub.se/https://link.springer.com/article/10.1007/s00778-019-00588-3)  
**Jurnal:** The VLDB Journal  
**Penulis:** Xuedi Qin, Yuyu Luo, Nan Tang, Guoliang Li  
**Penerbit:** Springer-Verlag GmbH Germany, part of Springer Nature 2019

-------
## I. Pendahuluan
Visualisasi data adalah proses mengubah data menjadi representasi visual, seperti grafik, diagram, atau peta, untuk memudahkan pemahaman informasi. Dengan visualisasi, data yang kompleks atau abstrak dapat disajikan dalam bentuk yang lebih intuitif dan mudah dipahami oleh manusia. Ini sangat berguna untuk memberikan gambaran umum data seperti tren, pola, atau hubungan dalam data, sehingga memudahkan pengambilan keputusan dan analisis terutama dalam dunia bisnis.

### 1.1 Alur Visualisasi Data
![Alur visualisasi data](https://raw.githubusercontent.com/elokfiola/Kuliah/c6e139d7b85dffaf74fdad2b18ff7493229a8faf/Screenshot%202024-08-31%20190022.png)
*Gambar 1. Alur visualisasi data*
 
1. Impor data adalah untuk mengambil data yang diperlukan dari sumber data yang diinginkan.
2. Persiapan data adalah untuk mempersiapkan data yang diimpor untuk visualisasi, misalnya, dengan menormalkan nilai, mengoreksi entri yang salah, dan menginterpolasi nilai yang hilang.
3. Manipulasi data adalah untuk memilih data yang akan divisualisasikan (alias memfilter dari komunitas visualisasi) dan mungkin dengan operasi umum lainnya seperti menggabungkan dan mengelompokkan.
4. Pemetaan adalah untuk memetakan data yang diperoleh dari proses di atas ke primitif geometris (misalnya, titik dan garis), bersama dengan atributnya (misalnya, warna, posisi, dan ukuran).
5. Rendering adalah mengubah data geometris di atas menjadi representasi visual

## II. Spesifikasi visualisasi
### 2.1 Spesifikasi visualisasi Data
Bahasa visualisasi data terdiri dari tiga bagian penting. **Pertama,** data yang perlu ditampilkan, seperti informasi yang akan kita lihat. Ini termasuk data yang ingin kita tunjukkan dan cara mengolahnya, seperti mengelompokkan atau menyaring data. **Kedua,** tanda (atau isyarat visual), yaitu cara menampilkan data dengan gambar, seperti batang, garis, atau titik. Ini juga mencakup ukuran gambar dan warna, serta informasi yang membantu menjelaskan gambar tersebut. **Ketiga,** pemetaan, yaitu cara menentukan bagaimana data ditempatkan ke dalam gambar yang sesuai. Biasanya, cara membuat gambar ini dari komputer diterjemahkan ke dalam bahasa visualisasi data.
### 2.2 Kategorisasi bahasa visualisasi data
![Spesifikasi Visualisasi Data](https://github.com/elokfiola/Kuliah/raw/0f28984d8118a954f4bd31da810abc0bf9201707/Spesifikasi%20visualisasi%20data.png)
*Gambar 2. Spesifikasi Visualisasi Data*

Bahasa visualisasi data dibagi menjadi tiga jenis berdasarkan kemudahannya. **Tingkat rendah** mengharuskan mengatur semua detail visualisasi sendiri, seperti memilih warna dan ukuran grafik, contohnya Prefuse dan Flare. **Tingkat tinggi** lebih mudah digunakan karena hanya perlu memilih jenis grafik yang diinginkan, seperti grafik batang, tanpa mengatur semua detailnya, contohnya ggplot2 dan Vega-Lite. **GUI (antarmuka grafis)** adalah yang paling mudah, dengan memilih template yang sudah ada dan hanya mengisi data, contohnya Tableau dan Echarts. Semakin tinggi tingkat bahasa visualisasi, semakin mudah penggunaannya, meskipun kontrol mungkin lebih terbatas.
### 2.3 Operasi visual berbasis GUI
Daripada menggunakan bahasa visualisasi yang kompleks, alat GUI seperti Tableau, Excel, atau Google Sheets membuat pembuatan grafik menjadi lebih sederhana. Misalnya, di Tableau, dapat memilih data dan jenis grafik, seperti grafik box-and-whisker untuk melihat rata-rata keterlambatan penerbangan. Alat GUI membuat proses ini lebih mudah dan langsung.

## III. Pendekatan Efisiensi untuk Visualisasi Data
### 3.1 Visualisasi data yang tepat
DBMS merupakan sistem basis data yang dapat membaca dan menampilkan visualisasi data.Caranya dapat dengan menerjemahkan kueri visualisasi ke kueri yang diterima oleh sistem tersebut. Sistem yang dapat digunakan seperti DeepEye, Polaris, SeeDB yang mendapat data dengan mengeluarkan kueri SQL ke basis data. Dengan begitu visualisasi data akan semakin mudah.

###  Mengintegrasikan sistem visualisasi dengan DBMS
Namun penggunaan DBMS tidak selalu baik, terdapat beberapa kekurangan seperti banyaknya fungsi yang diulang, sehingga menghasilkan teknik pengoptimalan yang tidak sama dengan server. Namun, terdapat solusi untuk menangani maslaah tersebut dengan menggabungkan pengambilan data dan rendering untuk mempercepat proses visualisasi.

Selain DBMS, ada juga Sistem Manajemen Visualisasi Data (DVMS) yang melibatkan **data** dan **skala**. Hal tersebut memua cangkupan data yang divisualisasikan dan direferensikan perbedaan pada elemen visual yang ditampilan, sedangkan skala hubungan menunjukkan pemetaan dari rentang data ke pengkodean visual rentang.

Visualisasi di Ermac direpresentasikan sebagai Rencana Visualisasi Logika (LVP) yang kemudian dikompilasi menjadi kueri mirip SQL untuk menangani data dan skala hubungan. Dimana kueri tersebut merupakan Fisik Rencana Visualisasi (PVP) yang dioptimalkan dengan teknik optimasi database tradisional.

Teknik optimasi visualisasi interaktif DVMS
- Penyimpanan kolom: penyimpann kolom dapat mencapai kinerja yang lebih baik, dibandingkan dengan penyimpanan baris, yang terlah diadopsi di SeeDB
- Indeks: indeks lebih banyak digunakan untuk meningkatkan kinerja pencarian dengan mengurangi jumlah baris

### 3.2 Teknologi visualisasi data
1. **XmdvTool**: pengelompokan tupel untuk mendukung navigasi hierarkis pengguna. Alat ini memungkinkan pengguna untuk terus mengeksplorasi data terstruktur. Menggunakan sistem catching LRU sebagai pengganti dan strategi prefetch berbasis visualisasi. 
2. **Historical data**: teknik memanfaatkan lintasan historis untuk prefetch-ing.Strategi XmdvTool dalam mengambil data berdasarkan historis adalah arah, fokus, dan vektor.
3. **Pembelajaran mesin**: Salah satu contohnya ialah ForeCache yang mempartisi data ke blok/ petak data di berbagai tingkatan dna memprediksi petak data kepada pengguna. Terdapat dua teknik prediksi yaitu **memprediksi fase analisis** melalui model Support Vector Machine (SVM), dan **memprediksi petak data** untuk merekomendasikan data yang telah diambil sebelumnya. Menurut eksperime yang sudah dilakukan, ForeCache menghasilkan nilai prediksi 25% lebih tinggi dibandingkan XmdvTool

### 3.3 Studi kasus
**Kyrix**    
kyrix merupakan sistem visualisasi data interaktif spesifikasi visualisasi deklaratif di front-end dan pemrosesan visualisasi yang efektif serta dapat diskalakan di back-end. Dengan kyrix, pengguna dapat memperbesar tampilan untuk melihat informasi lebih detail serta dapat memperkecil tampilan gambaran umum visualisasi.

**TDE**    
TDE merupakan mesin data untuk visualisasi data di Tableau. TDE lebih optimal dibagian penyimpanan dan kompresi berorientasi kolom, penataan ulang operator, pengurangan kardinalitas, dan dukungan visualisasi lainnya. TDE menyediakan domain informasi, seperti kardinalitas, nilai maksimum dan minimum yang berguna untuk memilih tingkat optimal suatu visualisasi

## IV. Rekomendasi berbasis spesifikasi
### 4.1 Spesifikasi yang Kurang Jelas
Untuk spesifikasi yang kurang spesifik pada visualisasi data, dapat memberikan petunjuk berupa 'referensi', dimana pengguna akan memberikan referensi visual kepada sistem dan sistem akan memberikan visualisasi yang sesuai tren. Jenis petunjuk lainnya berupa 'berbasis kata kunci', dapat menggunakan DeepEye yang merupakan sistem visualisasi yang dapat menerima kata kunci.

### 4.2 Solusi 
Eksplorasi data merupakan hal penting dalam memvisualisasi data untuk mendapatkan gambaran umum data. Penting untuk mempertimbangkan beberapa fator, seperti pemilihan klom yang akan divisualisasika, transformasi data, pemilihan penyandian visual (misalnya, batang, garis, titik), dan jenis penyandian untuk bagan tanda (misalnya, lebar batang, posisi titik).

## V.Ringkasan
Tabel 1 merangkum jenis visualisasi, input, dan metrik peringkat dari berbagai sistem rekomendasi visualisasi. Sistem seperti Draco, Data2Vis, dan Rank-by-feature memudahkan eksplorasi data tanpa memerlukan spesifikasi tertentu. Sebagian besar sistem lain membutuhkan input parsial dari pengguna, seperti kata kunci, untuk menyesuaikan visualisasi.

*Tabel 1.Ringkasan sistem rekomendasi visualisasi: jenis visualisasi, input, dan metrik peringkat utama*
![Jenis Visualisasi yang Direkomendasi](https://github.com/elokfiola/Kuliah/raw/890331c8f6ce2055278e35aa52fbb73b8f0b5705/Jenis%20visualisisi%20yang%20direkomendasi.png)

Pendekatan berbasis aturan lebih intuitif, tetapi hanya fokus pada beberapa metrik tertentu. Solusi berbasis machine learning, meskipun sulit diinterpretasikan, dapat lebih baik dalam memahami efektivitas visualisasi dan akan semakin cerdas dengan lebih banyak data. Sistem berbasis referensi memerlukan pengguna untuk menentukan pola atau data yang diinginkan, yang mungkin sulit jika mereka tidak familiar dengan data awal, tetapi cocok untuk pengguna yang tahu apa yang mereka cari. Rekomendasi berbasis perilaku terbatas pada pola perilaku yang telah ditentukan, sementara rekomendasi yang dipersonalisasi menyesuaikan dengan riwayat perilaku pengguna. Terakhir, ada kerangka kerja awal menggunakan CompassQL untuk menjelaskan metrik peringkat, meskipun belum diimplementasikan.

## VI. Arah Penelitian Lainnya
### 6.1 Persiapan data untuk visualisasi data
Sebelum membuat visualisasi data, penting untuk melakukan pembersihan data, seperti normalisasi, deduplikasi, imputasi nilai yang hilang, dan deteksi outlier.Selain itu dapat menghindari adanya bias. Namun, untuk efisiensi waktu dapat dilakukan pembersihan kumpulan data yang diperlukan saja.

------
## Kesimpulan
Visualisasi data merupakan salah satu bidang yang berkembang pesat mengikuti tren dan kebutuhan digital saat ini sehingga banyak sekali hasil penelitian dan sistem baru yang berkembang di masa sekarang. Artikel ini membahas visualisasi data yang efektif dan efisien, spesifikasi visualisasi, alat visualisasi data, teknologi inovasi visualisasi terkini, sampai solusi dalam memilih bentuk visualisasi yang tepat.


