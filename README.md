# Laporan Proyek Machine Learning - Widi Afandi

## Domain Proyek

Indonesia merupakan negara agraris yang sebagian besar penduduknya bekerja di sektor pertanian. Dilansir dari [Kementrian Pertanian](https://z-p42.www.instagram.com/p/CooZNrgpjE_/) sektor pertanian menjadi kontributor sebesar **13%** bagi PDB Nasional dan menjadi penghasil devisa bagi negara yang terus meningkat jumlahnya dari tahun 2020 dan 2021. Kementrian Pertanian juga menyebutkan bahwa mayoritas masyarakat Indonesia bekerja sebagai petani dan menggantungkan ekonominya di sektor tersebut.

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

![Cek Missing Value](https://github.com/technisekai/crop-recommendation/assets/54144923/bfb277eb-058b-44fa-8952-f64b5396dedd)

Dari gambar di atas, dataset tidak memiliki _missing value_ di kolom manapun sehingga bisa berlanjut ke tahap selanjutnya yaitu pengecekkan _outliers_.

![Boxplot](https://github.com/technisekai/crop-recommendation/assets/54144923/b3f95bf6-a9f3-477f-b7c0-4ab93d2cf4d8)

Kemudian banyaknya data pada masing-masing label juga sudah seimbang. Hal ini dibuktikan dengan visualisasi di bawah yang mana besaran data masing-masing label bernilai sama:

![Jumlah Data pada Label](https://github.com/technisekai/crop-recommendation/assets/54144923/53f82139-31b4-42ea-84f2-7042cc0ab428)


Selain fitur N, fitur lain memiliki nilai _outliers_ di dalamnya. Pada kasus ini, dicoba untuk menghilangkan/menghapus _outliers tersebut_ menggunakan metode IQR:

![Data yang hilang setelah outlier removal](https://github.com/technisekai/crop-recommendation/assets/54144923/053649b7-ce12-459d-bb06-0cb24798b609)

Namun, jumlah data yang dihapus terlalu banyak yaitu 19% dari keseluruhan data. Dengan jumlah data yang hilang sebanyak ini maka informasi pada dataset akan berkurang banyak sehingga diputuskan untuk mempertahankan nilai _outlier_ dan mencari algoritma machine learning yang sesuai yang dapat bertahan dari _outliers_. Namun penulis tetap menyediakan data yang sudah dihapus outliersnya yang digunakan sebagai pembanding di tahap evaluasi nanti.

## Modeling
Pada tahapan modeling, dipilih algoritma random forest dan support vector machine. Karena kedua algoritma ini berdasarkan penelitian dapat bertahan dari efek adanya _outlier_ pada data.

### How Random Forest Work
belum...........
### How SVM Work
belum...........

## Evaluation
Evaluasi model dilakukan dengan menggunakan metrik _accuracy, precision, recall, f1-score_ untuk mengevaluasi kemampuan model. 
### _accuracy_
belum...........

### _precision_
belum...........

### _recall_
belum...........

### _f1-score_
belum...........

Adapun hasilnya adalah sebagai berikut:
![Hasil Metrik](https://github.com/technisekai/crop-recommendation/assets/54144923/a879a3db-b954-462f-bb9c-202f4e869fb6)

Model Random Forest dan SVM berhasil mencapai akurasi yang sangat baik di atas 95%. Namun yang terbaik diperoleh oleh model Random Forest dengan akurasi 99%. Disini dilakukan juga eksperimen dengan melatih algoritma Random Forest dan SVM dengan data yang sudah dihilangkan _outliersnya_. Namun, model Random Forest dan SVM yang sudah dihilangkan _outliersnya_ mengalami penurunan performa sebesar 1% sehingga dapat disimpulkan bahwa menghilangkan _outliers_ sebesar 19% dari keseluruhan data memiliki dampak pada performa model sebesar 1%.

## Referensi
[1] ig kementrian
[2] negara agraris
[3] penelitian tanaman orka
[4] data kaggle
[5] jumlah maksimum data yang dapat dihilangkan
[6] kenapa random forest dan svm tahan outlier dan cara kerja
[7] metrik
