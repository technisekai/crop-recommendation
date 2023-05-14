# Laporan Proyek Machine Learning - Widi Afandi

## Domain Proyek

Indonesia merupakan negara agraris yang sebagian besar penduduknya bekerja di sektor pertanian. Dilansir dari [Kementrian Pertanian](https://z-p42.www.instagram.com/p/CooZNrgpjE_/) sektor pertanian menjadi kontributor sebesar **13%** bagi PDB Nasional dan menjadi penghasil devisa bagi negara yang terus meningkat jumlahnya dari tahun 2020 dan 2021. Kementrian Pertanian juga menyebutkan bahwa mayoritas masyarakat Indonesia bekerja sebagai petani dan menggantungkan ekonominya di sektor tersebut.

![Data dari Kementrian Pertanian](https://github.com/technisekai/crop-recommendation/assets/54144923/7558e719-85cf-4f2c-9ea6-1dbb039d84e0)


Kesuksesan sektor pertanian dalam menyumbang pendapatan masyarakat ataupun negara tentunya tidak lepas dari produksi panen yang dihasilkan. Hasil panen ini dipengaruhi dari beberapa faktor salah satunya adalah kesesuaian antara jenis tanaman yang ditanam dengan tanahnya. Tanah yang tidak sesuai dengan tanaman yang ditanam akan menyebabkan hasil panen tidak optimal dan bahkan dapat mengalami gagal panen. Dikutip dari penelitian yang dilakukan oleh [Alfian Nur Budiarto](http://repository.uin-suska.ac.id/27846/), dengan penelitian membahas kesesuaian antara tanaman orka dengan jenis tanah dengan indikator tertentu menyimpulkan bahwa tanaman orka mengalami peningkatan produksi jumlah buah, bobot basah buah, dan panjang buah pada tanah dengan indikator tertentu.

Dengan demikian, untuk mendapatkan hasil panen yang lebih optimal dan sebagai salah satu usaha untuk meningkatkan kualitas dari hasil panen maka pemilihan jenis tanaman untuk indikator tanah tertentu menjadi penting untuk dilakukan. Dengan jenis tanah yang tepat produksi panen berpotensi lebih maksimal dan dapat meningkatkan ekonomi masyarakat ataupun negara dan kualitas panen yang dihasilkan pun lebih baik.

![Workflow Pengerjaan Proyek](https://github.com/technisekai/crop-recommendation/assets/54144923/f3ff5b0a-eb57-474f-bd51-e10cff18e861)

## Business Understanding

### Problem Statements

- Indikator apa saja pada tanah yang dapat dijadikan sebagai acuan untuk menentukan jenis tanaman yang sesuai?
- Bagaimana menerapkan algoritma Machine Learning untuk memprediksi jenis tanaman yang sesuai untuk ditanam pada tanah dengan indikator tertentu?

### Goals

- Memahami indikator pada tanah yang dapat dijadikan sebagai acuan untuk menanam jenis tanaman yang sesuai.
- Menerapkan algortima machine learning untuk memprediksi jenis tanaman yang sesuai dengan tanah.

### Solution statements
- Melakukan analsis data pada indikator data dengan melakukan visualisasi pada indikator tanah untuk menemukan korelasi antar variable.
- Menerapkan algoritma SVM dan Random Forest yang mana cocok dengan studi kasus yang diangkat dimana kedua algoritma tersebut dapat mengurangi efek yang ditimbulkan jika outlier tidak dihilangkan.

## Data Understanding
Dataset yang digunakan didapatkan dari sumber terbuka [kaggle](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset?resource=download).
![image](https://github.com/technisekai/crop-recommendation/assets/54144923/8fce2c67-4752-4428-a997-0c935b1e4cdd)

### Variabel-variabel pada Crop Recommendation dataset adalah sebagai berikut:
- N : rasio Nitrogen yang terkandung dalam tanah. Unsur nitrogen ini berguna untuk merangsang pertumbuhan tanaman secara keseluruhan, khususnya batang, cabang dan daun
- P : rasio fosfor pada tanah yang memiliki manfaat untuk merangsang pertumbuhan akar, terutama akar lateral dan akar rambut
- K : rasio potasium atau disebut juga kalium pada tanah. Dengan adanya kalium ini menyebabkan terjaminnya ketegaran tanaman, merangsang pertumbuhan akar, mencegah serangan hama dan penyakit, memperbaiki kualitas bulir, serta mengatasi kekurangan air
- temperature : temperatur lingkungan pada sekitar tanah dalam satuan C.
- humidity : kelembaban pada tanah.
- ph : nilai pH pada tanah
- rainfall : curah hujan di sekitar tanah dalam satuan mm
- label : jenis tanaman yang mana terdapat 22 jenis tanaman

## Data Preparation
![Data Preparation Workflow](https://github.com/technisekai/crop-recommendation/assets/54144923/94ea246a-170f-424a-9102-7417ab116fde)

Pada tahap ini dilakukan pengecekkan _missing value_ pada dataset. Hal ini dilakukan untuk meningkatkan performa dari algoritma machine learning. Selain itu _missing value_ akan menyebabkan algoritma eror ketika proses pelatihan.

| No | Column      | Non-Null Count | Dtype   |
|----|-------------|----------------|---------|
| 0  | N           | 2200 non-null  | int64   |
| 1  | P           | 2200 non-null  | int64   |
| 2  | K           | 2200 non-null  | int64   |
| 3  | temperature | 2200 non-null  | float64 |
| 4  | humidity    | 2200 non-null  | float64 |
| 5  | ph          | 2200 non-null  | float64 |
| 6  | rainfall    | 2200 non-null  | float64 |
| 7  | label       | 2200 non-null  | object  |

Dari gambar di atas, dataset tidak memiliki _missing value_ di kolom manapun sehingga bisa berlanjut ke tahap selanjutnya yaitu pengecekkan _outliers_.

![Boxplot](https://github.com/technisekai/crop-recommendation/assets/54144923/b3f95bf6-a9f3-477f-b7c0-4ab93d2cf4d8)

Kemudian banyaknya data pada masing-masing label juga sudah seimbang. Hal ini dibuktikan dengan visualisasi di bawah yang mana besaran data masing-masing label bernilai sama:

![Jumlah Data pada Label](https://github.com/technisekai/crop-recommendation/assets/54144923/53f82139-31b4-42ea-84f2-7042cc0ab428)


Selain fitur N, fitur lain memiliki nilai _outliers_ di dalamnya. Pada kasus ini, dicoba untuk menghilangkan/menghapus _outliers tersebut_ menggunakan metode IQR:

```Data yang hilang setelah menghilangkan outlier adalah 0,196 atau 19% dari keseuluruhan data```

Namun, jumlah data yang dihapus terlalu banyak yaitu 19% dari keseluruhan data. Dengan jumlah data yang hilang sebanyak ini maka informasi pada dataset akan berkurang banyak sehingga diputuskan untuk mempertahankan nilai _outlier_ dan mencari algoritma machine learning yang sesuai yang dapat bertahan dari _outliers_. Namun penulis tetap menyediakan data yang sudah dihapus outliersnya yang digunakan sebagai pembanding di tahap evaluasi nanti.

## Modeling
Pada tahapan modeling, dipilih algoritma random forest dan support vector machine. Karena kedua algoritma ini berdasarkan penelitian dapat bertahan dari efek adanya _outlier_ pada data.

### How Random Forest Work
Random forest merupakan teknik _ensemble learning_ untuk klasfikasi. Random forest bekerja dengan memilih sample secara acak kemudian membuah _decision tree_ dari dari setiap sampel yang dipilih dan hasil prediksinya dilakukan voting. Algorita random forest akan memilih hasil prediksi yang paling banyak dipilih.

### How SVM Work
SVM merupakan teknik untuk tugas klasifikasi yang bekerja dengan mengidentifikasi _support vector_ dari data kemudian memisahkan data dengan _hyperplane_ dan _support vector_ sebagai acuannya pada masing-masing data.

## Evaluation
Evaluasi model dilakukan dengan menggunakan metrik _accuracy, precision, recall, f1-score_ untuk mengevaluasi kemampuan model.

### _accuracy_
Metric accuracy menggambarkan bagaimana model memprediksi True Positive (TP) dan True Negative (TN). Akurasi menjadi pengukuran seberapa baik suatu model dalam melakukan klasifikasi sentimen dilihat dari seberapa banyak peringkat sentimen benar dalam klasifikasi.

![formula accuracy](https://github.com/technisekai/crop-recommendation/assets/54144923/3b704b58-6872-471d-af38-06be0c0425ff)


### _precision_
Metric precision adalah rasio model memprediksi True Positive (TP) terhadap seluruh hasil prediksi positif yang tujuannya untuk mengukur ketepatan suatu model klasifikasi dimana semakin besar nilai precisionnya maka semakin baik ketepatan model dalam memprediksi kelas suatu data.

![formula precision](https://github.com/technisekai/crop-recommendation/assets/54144923/6f0102ed-c7d7-4d89-a228-1fcaa310c443)


### _recall_
Metric recall adalah rasio model memprediksi True Positive (TP) terhadap seluruh data benar. Fungsi dari recall yaitu untuk mengukur kelengkapan atau sensitifitas model klasifikasi. Peningkatan nilai recall berarti model menemukan kembali pada sebuah informasi yang relevan dari keseluruhan dataset.

![formula recall](https://github.com/technisekai/crop-recommendation/assets/54144923/7c0cebe5-ef6a-4733-adf3-e7f68ce2a506)


### _f1-score_
Metric F1-measure merupakan penggabungan nilai precision dan recall untuk menghitung keseimbangan.

![formula f1-score](https://github.com/technisekai/crop-recommendation/assets/54144923/b8a729ba-60f7-40c1-bf25-4e183cffb8cb)


Adapun hasilnya adalah sebagai berikut:
| No | algorithm                                | accuracy | precision | recall | f1-score |
|----|------------------------------------------|----------|-----------|--------|----------|
| 1  | Random Forest                            | 99%      | 99%       | 99%    | 99%      |
| 2  | Support Vector Machine                   | 98%      | 98%       | 97%    | 97%      |
| 3  | Random Forest + Outlier Removal          | 98%      | 99%       | 97%    | 98%      |
| 4  | Support Vector Machine + Outlier Removal | 97%      | 93%       | 94%    | 93%      |

Model Random Forest dan SVM berhasil mencapai akurasi yang sangat baik di atas 95%. Namun yang terbaik diperoleh oleh model Random Forest dengan akurasi 99%. Disini dilakukan juga eksperimen dengan melatih algoritma Random Forest dan SVM dengan data yang sudah dihilangkan _outliersnya_. Namun, model Random Forest dan SVM yang sudah dihilangkan _outliersnya_ mengalami penurunan performa sebesar 1% pada 4 metrik yang digunakan sehingga dapat disimpulkan bahwa menghilangkan _outliers_ sebesar 19% dari keseluruhan data memiliki dampak pada performa model sebesar 1% yang mana berarti penghilangan _outliers_ tidak selalu menghasilkan hasil yang baik bagi performa model.

## Referensi
[1] Ditjenbun, “Kementerian Pertanian Direktorat Jenderal Perkebunan » Tak Heran, Komoditas Perkebunan Selalu Berhasil Dongkrak Devisa Negara & Terbukti Solusi Tepat Hadapi Krisis Pangan Global,” Nov. 24, 2022. https://ditjenbun.pertanian.go.id/tak-heran-komoditas-perkebunan-selalu-berhasil-dongkrak-devisa-negara-terbukti-solusi-tepat-hadapi-krisis-pangan-global/ (accessed May 13, 2023).

[2] ditjenbun, “Kementerian Pertanian Direktorat Jenderal Perkebunan » Tak Heran, Komoditas Perkebunan Selalu Berhasil Dongkrak Devisa Negara & Terbukti Solusi Tepat Hadapi Krisis Pangan Global,” Nov. 24, 2022. https://ditjenbun.pertanian.go.id/tak-heran-komoditas-perkebunan-selalu-berhasil-dongkrak-devisa-negara-terbukti-solusi-tepat-hadapi-krisis-pangan-global/ (accessed May 13, 2023).

[3] A. Ingle, “Crop Recommendation Dataset | Kaggle,” May 13, 2022. https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset?resource=download (accessed May 13, 2023).

[4] J. Frost, “Guidelines for Removing and Handling Outliers in Data - Statistics By Jim,” Apr. 11, 2023. https://statisticsbyjim.com/basics/remove-outliers/ (accessed May 13, 2023).

[5] A. Srivastava, “Let’s Talk about Random Forests!. In my previous article, we discussed… | by Arpan Srivastava | Analytics Vidhya | Medium,” Apr. 19, 2021. https://medium.com/analytics-vidhya/lets-talk-about-random-forests-524ae1138d8b (accessed May 13, 2023).

[6] H. Ali Ismail, “Learning Data Science: Day 11 - Support Vector Machine | by Haydar Ali Ismail | Medium,” Jan. 10, 2017. https://haydar-ai.medium.com/learning-data-science-day-11-support-vector-machine-8ef06da91bfc (accessed May 13, 2023).

[7] S. K. Dirjen, P. Riset, D. Pengembangan, R. Dikti, S. Khomsah, and A. S. Aribowo, “Text-Preprocessing Model Youtube Comments in Indonesian,” J. RESTI (Rekayasa Sist. dan Teknol. Informasi), vol. 4, no. 4, pp. 648–654, Aug. 2020, doi: 10.29207/RESTI.V4I4.2035.
