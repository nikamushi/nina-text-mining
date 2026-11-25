# Analisis Frekuensi Kata Komentar YouTube Lagu "Nina" - .Feast

## 1. Deskripsi Proyek

Proyek ini merupakan implementasi Text Mining untuk menganalisis frekuensi kata pada komentar YouTube di video Official Lyric lagu **"Nina" oleh .Feast**.

Penelitian ini bertujuan mengidentifikasi kata-kata yang paling sering muncul dalam komentar menggunakan metode **Term Frequency (TF)**.

Hasil analisis disajikan dalam bentuk tabel frekuensi kata, diagram batang Top 20, dan Word Cloud sebelum serta sesudah preprocessing.

Penelitian ini berfokus pada analisis frekuensi kata, bukan analisis sentimen, emosi, maupun topic modeling.

## 2. Sumber Data

Data penelitian diperoleh dari komentar YouTube pada video berikut:

| Keterangan           | Informasi            |
| -------------------- | -------------------- |
| Platform             | YouTube              |
| Artis                | .Feast               |
| Judul lagu           | Nina                 |
| Jenis video          | Official Lyric Video |
| Jumlah komentar awal | 2.000 komentar       |
| Bahasa target        | Bahasa Indonesia     |

**URL video:** https://www.youtube.com/watch?v=iQo-8wx0l0Y

Pengumpulan komentar dilakukan menggunakan library `youtube-comment-downloader` dengan urutan komentar terbaru.

Oleh karena itu, data yang diperoleh merupakan kumpulan komentar terbaru pada saat pengambilan data dan bukan sampel acak dari seluruh komentar video.

## 3. Metode Penelitian

Penelitian dilakukan melalui beberapa tahapan Text Mining sebagai berikut.

### 3.1 Pengumpulan Data

Mengumpulkan 2.000 komentar YouTube dari video Official Lyric lagu "Nina" menggunakan Python.

### 3.2 Exploratory Data Analysis (EDA)

Melakukan pemeriksaan awal terhadap dataset untuk memahami karakteristik data, meliputi:

- Informasi dataset.
- Pemeriksaan missing values.
- Pemeriksaan komentar duplikat.
- Distribusi panjang komentar.
- Statistik jumlah kata.
- Pemeriksaan sampel komentar.

### 3.3 Preprocessing

Tahapan preprocessing dilakukan untuk membersihkan dan mempersiapkan teks sebelum analisis frekuensi kata.

Tahapan yang digunakan:

1. **Cleaning:** Menghapus URL, mention, emoji, simbol, tanda baca, serta komentar yang tidak memiliki teks bermakna.
2. **Case Folding:** Mengubah seluruh teks menjadi huruf kecil.
3. **Normalisasi:** Mengubah kata tidak baku dan singkatan menjadi bentuk kata yang telah ditentukan.
4. **Tokenisasi:** Memecah komentar menjadi token kata.
5. **Stopword Removal:** Menghapus kata-kata yang dianggap kurang informatif menggunakan daftar stopword NLTK dan Sastrawi yang telah dievaluasi.
6. **Stemming:** Mengubah kata berimbuhan menjadi kata dasar menggunakan library Sastrawi.
7. **Penyaringan Ulang:** Menghapus token hasil stemming yang termasuk dalam daftar stopword.

### 3.4 Term Frequency (TF)

Menghitung jumlah kemunculan setiap kata dalam keseluruhan dokumen setelah preprocessing.

Hasil analisis meliputi:

- Top 10 kata paling sering muncul.
- Top 20 kata paling sering muncul.
- Diagram batang Top 20.
- Word Cloud sebelum preprocessing lanjutan.
- Word Cloud setelah preprocessing.
- Perbandingan Word Cloud.

## 4. Hasil Pengolahan Data

Berikut ringkasan hasil pengolahan dataset:

| Keterangan                                | Jumlah |
| ----------------------------------------- | -----: |
| Komentar awal                             |  2.000 |
| Komentar setelah cleaning                 |  1.890 |
| Komentar setelah penghapusan duplikat     |  1.826 |
| Komentar setelah pemeriksaan token kosong |  1.819 |
| Total token akhir                         | 40.166 |
| Jumlah kata unik                          |  5.145 |

### 4.1 Top 10 Kata

Berikut 10 kata dengan frekuensi kemunculan tertinggi setelah preprocessing:

| No. | Kata   | Frekuensi |
| --: | ------ | --------: |
|   1 | aku    |     2.067 |
|   2 | tidak  |       695 |
|   3 | ku     |       547 |
|   4 | bisa   |       538 |
|   5 | kalian |       528 |
|   6 | anak   |       524 |
|   7 | jadi   |       487 |
|   8 | baik   |       487 |
|   9 | sudah  |       483 |
|  10 | ayah   |       482 |

Kata **"aku"** merupakan kata dengan frekuensi tertinggi, yaitu sebanyak 2.067 kemunculan.

### 4.2 Visualisasi

Visualisasi hasil penelitian disimpan dalam folder `outputs/visualizations/`, meliputi:

- `top_20_kata.png`: Diagram batang 20 kata dengan frekuensi tertinggi.
- `wordcloud_sebelum.png`: Word Cloud sebelum preprocessing lanjutan.
- `wordcloud_sesudah.png`: Word Cloud setelah preprocessing.
- `perbandingan_wordcloud.png`: Perbandingan Word Cloud sebelum dan sesudah preprocessing.

## 5. Teknologi dan Library

Proyek ini menggunakan teknologi dan library berikut:

- **Python:** Bahasa pemrograman untuk pengolahan dan analisis data.
- **Jupyter Notebook:** Lingkungan untuk menjalankan kode dan mendokumentasikan proses analisis.
- **Pandas:** Pengolahan dataset.
- **NumPy:** Operasi numerik.
- **Matplotlib:** Pembuatan visualisasi.
- **Seaborn:** Visualisasi data.
- **WordCloud:** Pembuatan visualisasi Word Cloud.
- **NLTK:** Pengolahan teks dan penyediaan daftar stopword.
- **Sastrawi:** Stopword removal dan stemming bahasa Indonesia.
- **youtube-comment-downloader:** Pengumpulan komentar YouTube.

## 6. Struktur Proyek

```text
├── data/
│   ├── processed/
│   │   ├── komentar_nina_preprocessed_final.csv
│   │   └── komentar_nina_preprocessed.csv
│   └── raw/
│       └── komentar_nina.csv
├── notebooks/
│   └── analisis_nina.ipynb
├── outputs/
│   ├── results/
│   │   ├── term_frequency.csv
│   │   ├── top_10_kata.csv
│   │   └── top_20_kata.csv
│   └── visualizations/
│       ├── perbandingan_wordcloud.png
│       ├── top_20_kata.png
│       ├── wordcloud_sebelum.png
│       └── wordcloud_sesudah.png
└── README.md
```

### Penjelasan Direktori

| Direktori                 | Keterangan                                                     |
| ------------------------- | -------------------------------------------------------------- |
| `data/raw/`               | Menyimpan dataset komentar asli dari YouTube.                  |
| `data/processed/`         | Menyimpan dataset yang telah melalui proses preprocessing.     |
| `notebooks/`              | Menyimpan Jupyter Notebook untuk pengolahan dan analisis data. |
| `outputs/results/`        | Menyimpan hasil perhitungan frekuensi kata dalam format CSV.   |
| `outputs/visualizations/` | Menyimpan hasil visualisasi penelitian dalam format PNG.       |

## 7. Cara Menjalankan Proyek

### 7.1 Persiapan

Pastikan Python dan Jupyter Notebook sudah terpasang pada komputer.

### 7.2 Instalasi Library

Instal library yang dibutuhkan menggunakan perintah berikut:

```bash
pip install pandas numpy matplotlib seaborn wordcloud nltk Sastrawi youtube-comment-downloader
```

### 7.3 Menjalankan Notebook

Jalankan Jupyter Notebook melalui terminal:

```bash
jupyter notebook
```

Kemudian buka file:

```text
notebooks/analisis_nina.ipynb
```

Jalankan setiap cell secara berurutan untuk mengikuti proses pengolahan dan analisis data.

**Catatan:** Dataset komentar asli sudah tersedia di `data/raw/komentar_nina.csv`. Oleh karena itu, proses pengumpulan data tidak perlu diulang apabila hanya ingin menjalankan analisis menggunakan dataset yang tersedia.

## 8. Batasan Penelitian

Penelitian ini memiliki beberapa batasan:

1. Data hanya berasal dari satu video YouTube, yaitu Official Lyric lagu "Nina" oleh .Feast.
2. Jumlah komentar yang dikumpulkan dibatasi sebanyak 2.000 komentar.
3. Pengumpulan data menggunakan urutan komentar terbaru sehingga tidak merepresentasikan sampel acak seluruh komentar.
4. Analisis difokuskan pada frekuensi kemunculan kata dan tidak digunakan untuk menentukan sentimen atau emosi pengguna.
5. Hasil stemming bergantung pada aturan dan kemampuan library Sastrawi.
6. Normalisasi kata tidak baku dan evaluasi stopword dilakukan berdasarkan karakteristik dataset penelitian.

## 9. Tujuan Akhir

Proyek ini diharapkan dapat menunjukkan penerapan tahapan Text Mining dalam pengolahan komentar YouTube, mulai dari pengumpulan data, Exploratory Data Analysis (EDA), preprocessing, hingga analisis frekuensi kata menggunakan metode Term Frequency (TF).
