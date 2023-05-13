# Laporan Proyek Machine Learning - Widi Afandi

## Domain Proyek

Indonesia merupakan negara agraris yang sebagian besar penduduknya bekerja di sektor pertanian. Dilansir dari [Kementriab Pertanian](https://z-p42.www.instagram.com/p/CooZNrgpjE_/) sektor pertanian menjadi kontributor sebesar **13%** bagi PDB Nasional dan menjadi penghasil devisa bagi negara yang terus meningkat jumlahnya dari tahun 2020 dan 2021.

Kesuksesan sektor pertanian ini tentunya tidak lepas dari hasil panen yang terus meningkat yang mana hasil panen ini dipengaruhi dari beberapa faktor dari mulai musim, serangan hama, dan kesesuaian antara jenis tanaman yang ditanam dengan jenis tanahnya. Jenis tanah yang tidak sesuai akan menyebabkan hasil panen tidak optimal dan bahkan mengalami gagal panen. Dikutip dari penelitian [Alfian Nur Budiarto](http://repository.uin-suska.ac.id/27846/) yang melakukan penelitian tentang kesesuaian tanaman orka pada jenis tanah menyimpulkan bahwa tanaman orka pada tanah PMK mengalami peningkatan produksi jumlah buah, bobot basah buah, dan panjang buah dibadingkan jenis tanah yang lain.

Dengan demikian, untuk mendapatkan hasil yang lebih optimal dan sebagai salah satu usaha untuk meningkatkan kualitas dari hasil panen maka pemilihan jenis tanah yang tepat untuk tanaman menjadi penting. Dengan jenis tanah yang tepat produksi panen berpotensi lebih maksimal dan dapat meningkatkan ekonomi masyarakat ataupun negara dan kualitas panen yang dihasilkan pun lebih baik.

## Business Understanding

### Problem Statements

- Indikator apa saja pada tanah yang dapat dijadikan sebagai penentu kesesuaian antara tanah dan jenis tanaman yang akan ditanam?
- Bagaimana menerapkan algoritma Machine Learning untuk memprediksi jenis tanaman yang sesuai untuk ditanam pada jenis tanah?

### Goals

- Memahami indikator pada tanah yang dapat dijadikan sebagai acuan untuk menanam jenis tanaman yang sesuai
- Menerapkan algortima machine learning untuk memprediksi jenis tanaman yang sesuai pada indikator tanah

### Solution statements
- Melakukan Exploratory Data Analysis untuk memahami indikator yang ada pada tanah dengan melakukan visualisasi pada data.
- Menerapkan algoritma yang sesuai dengan jenis data yang digunakan dan melakukan hyperparameter tuning untuk mendapatkan hasil yang lebih optimal.

## Data Understanding
Dataset yang digunakan didapatkan dari sumber terbuka [kaggle](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset?resource=download).

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- N : rasio Nitrogen yang terdapat pada tanah.
- P : rasio fosfor pada tanah.
- K : rasio potasium pada tanah
- temperature : temperatur dalam satuan C.
- humidity : kelembaban.
- ph : nilai pH pada tanah
- rainfall : curah dalam satuan mm
- label : jenis tanaman

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
