# Practical Statistics for Data Scientists

Reproduksi kode dan ringkasan teori dari buku **Practical Statistics for Data Scientists: 50+ Essential Concepts Using R and Python (2nd Edition)** karya Peter Bruce, Andrew Bruce, dan Peter Gedeck (O'Reilly, 2020).

---

## Daftar Isi

| Bab | Judul | Notebook |
|---|---|---|
| 1 | Exploratory Data Analysis | [`PracticalStatisticsChapter1_ID.ipynb`](PracticalStatisticsChapter1_ID.ipynb) |
| 2 | Data and Sampling Distributions | [`PracticalStatisticsChapter2_ID.ipynb`](PracticalStatisticsChapter2_ID.ipynb) |
| 3 | Statistical Experiments and Significance Testing | [`PracticalStatisticsChapter3_ID.ipynb`](PracticalStatisticsChapter3_ID.ipynb) |
| 4 | Regression and Prediction | [`PracticalStatisticsChapter4_ID.ipynb`](PracticalStatisticsChapter4_ID.ipynb) |
| 5 | Classification | *menyusul* |
| 6 | Statistical Machine Learning | *menyusul* |
| 7 | Unsupervised Learning | *menyusul* |

---

### Bab 1 — Exploratory Data Analysis (EDA)

Langkah pertama setiap proyek data: memahami data sebelum memodelkannya. EDA dipopulerkan oleh John Tukey (1977) dan berfokus pada ringkasan sederhana dan visualisasi.

**Konsep utama:**
- **Tipe data terstruktur.** Numerik (kontinu, diskrit) dan kategorikal (nominal, biner, ordinal). Tipe data menentukan analisis dan visualisasi yang tepat.
- **Rectangular data.** Tabel dengan baris sebagai observasi dan kolom sebagai fitur (`pandas.DataFrame`).
- **Estimasi lokasi.** Mean, trimmed mean, weighted mean, median, dan weighted median. Mean sensitif terhadap outlier, sedangkan median dan trimmed mean lebih **robust**.
- **Estimasi variabilitas.** Varians, standar deviasi, mean absolute deviation, MAD (median absolute deviation), persentil, dan IQR.
- **Distribusi data.** Persentil, boxplot, tabel frekuensi, histogram, dan density plot (KDE).
- **Data kategorikal.** Proporsi, mode, expected value, dan bar chart.
- **Korelasi.** Koefisien Pearson (linear), Spearman dan Kendall (berbasis ranking), matriks korelasi, dan scatterplot.
- **Analisis multivariat.** Hexagonal binning, contour plot, contingency table, boxplot/violin plot per kelompok, dan conditioning (faceting).

**Contoh hasil:** pada data populasi negara bagian AS, mean (6,16 juta) > trimmed mean (4,78 juta) > median (4,44 juta), yang menandakan distribusi miring ke kanan.

---

### Bab 2 — Data and Sampling Distributions

Membahas cara mengambil sampel yang baik dan cara mengukur ketidakpastian estimasi yang dihitung dari sampel.

**Konsep utama:**
- **Random sampling dan sample bias.** Kualitas sampel lebih penting daripada ukurannya. Contohnya survei *Literary Digest* 1936 yang salah memprediksi pemilu meskipun respondennya lebih dari 10 juta orang.
- **Selection bias.** Data snooping, vast search effect, dan **regression to the mean**.
- **Sampling distribution.** Distribusi statistik sampel jika sampel diambil berulang kali. **Central Limit Theorem**: mean sampel cenderung berdistribusi normal untuk sampel besar.
- **Standard error.** SE = s / √n. Untuk memperkecil SE setengahnya, ukuran sampel perlu dinaikkan 4 kali lipat.
- **Bootstrap.** Resampling dengan pengembalian untuk mengestimasi SE dan confidence interval tanpa asumsi distribusi.
- **Confidence interval.** Cara membuat dan menafsirkannya dengan benar.
- **Distribusi probabilitas.** Normal (dan QQ-plot), long-tailed, t, binomial, chi-square, F, Poisson, eksponensial, dan Weibull.

**Contoh hasil:** bootstrap memberi standard error median pendapatan peminjam sekitar $222. Return harian saham Netflix melewati 3 standar deviasi sekitar 4,6× lebih sering daripada prediksi distribusi normal (*fat tails*).

---

### Bab 3 — Statistical Experiments and Significance Testing

Membahas desain eksperimen dan cara memastikan bahwa efek yang terlihat bukan sekadar kebetulan.

**Konsep utama:**
- **A/B testing.** Kelompok treatment vs kontrol, randomisasi, dan penentuan metrik sebelum eksperimen.
- **Uji hipotesis.** Null dan alternative hypothesis, one-way vs two-way test.
- **Permutation test.** Gabungkan data, acak, bagi ulang, lalu bandingkan dengan statistik asli. Pendekatan serbaguna tanpa asumsi distribusi.
- **p-value dan alpha.** Error tipe I (false positive) dan tipe II (false negative), serta pernyataan American Statistical Association (2016) tentang keterbatasan p-value.
- **Uji klasik.** t-test (dua mean), ANOVA dan F-statistic (banyak kelompok), chi-square test dan Fisher's exact test (data hitungan).
- **Multiple testing.** Alpha inflation, koreksi Bonferroni, dan false discovery rate (FDR).
- **Degrees of freedom.** Hubungannya dengan encoding variabel kategorikal.
- **Multi-arm bandit.** Epsilon-greedy dan Thompson sampling untuk menyeimbangkan eksplorasi dan eksploitasi.
- **Power dan ukuran sampel.** Menghitung sampel yang dibutuhkan berdasarkan effect size, alpha, dan power.

**Contoh hasil:** perbedaan durasi sesi dua halaman web tidak signifikan (p ≈ 0,14). Untuk mendeteksi kenaikan klik 10% dari baseline 1,1%, dibutuhkan sekitar 116 ribu sampel per kelompok, sedangkan kenaikan 50% hanya butuh sekitar 5.500.

---

### Bab 4 — Regression and Prediction

Membahas regresi linear sebagai alat untuk memprediksi outcome dan memahami hubungan antar variabel.

**Konsep utama:**
- **Simple linear regression.** Intercept, slope, fitted values, residuals, dan least squares.
- **Multiple linear regression.** Interpretasi koefisien ketika prediktor lain dianggap tetap.
- **Evaluasi model.** RMSE, RSE, R², t-statistic, dan p-value.
- **Cross-validation.** Menguji model pada data yang tidak dipakai untuk melatih.
- **Pemilihan model.** Adjusted R², AIC, BIC, dan stepwise regression (Occam's razor).
- **Weighted regression.** Bobot berbeda untuk tiap record.
- **Prediksi.** Confidence interval vs prediction interval, serta bahaya ekstrapolasi.
- **Variabel faktor.** Dummy variables, reference coding vs one-hot encoding, dan pengelompokan faktor dengan banyak level.
- **Interpretasi.** Prediktor yang berkorelasi, multikolinearitas, confounding variable, dan interaksi.
- **Diagnostik regresi.** Outlier, influential values (leverage, Cook's distance), heteroskedastisitas, dan partial residual plot.
- **Regresi non-linear.** Regresi polinomial, spline, dan Generalized Additive Models (GAM).

**Contoh hasil:** pada data fungsi paru, PEFR = 424,58 − 4,185 × Exposure. Model harga rumah King County menjelaskan sekitar 54% variasi harga (RMSE ≈ $261 ribu). Setelah ditambah interaksi dengan lokasi, nilai tiap sq ft luas bangunan berkisar dari sekitar $115 di wilayah murah sampai sekitar $340 di wilayah mahal.

---

## Cara Menjalankan

**Google Colab:** upload notebook ke Colab, lalu jalankan *Runtime → Run all*. Dataset dimuat langsung dari GitHub, jadi tidak perlu mengunduh file CSV.

**Lokal:**
```bash
git clone https://github.com/xcoook1es/Practical-Statistics-for-Data-Scientists.git
cd Practical-Statistics-for-Data-Scientists
pip install -r requirements.txt
jupyter notebook
```

## Requirements

Notebook diuji dengan Python 3.11 dan library berikut:

```
pandas
numpy
scipy
statsmodels
scikit-learn
matplotlib
seaborn
wquantiles
pygam
```

## Referensi

- Bruce, P., Bruce, A., & Gedeck, P. (2020). *Practical Statistics for Data Scientists: 50+ Essential Concepts Using R and Python* (2nd ed.). O'Reilly Media.
- Kode resmi buku: [github.com/gedeck/practical-statistics-for-data-scientists](https://github.com/gedeck/practical-statistics-for-data-scientists)

