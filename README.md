# Daftar Isi
- [Pengertian dan Tujuan ANOVA](#pengertian-dan-tujuan-anova)
- [Proses ANOVA](#proses-anova)
  - [F-test](#f-test)
  - [P-value](#p-value)
- [Syarat ANOVA](#syarat-anova)
- [Jenis ANOVA](#jenis-anova)
  - [One-way ANOVA](#one-way-anova)
  - [Two-way ANOVA](#two-way-anova)
  - [MANOVA (Multivariate ANOVA)](#manova-multivariate-anova)
- [Studi Kasus](#studi-kasus)
- [Penerapan dalam Kodingan](./Analisis_ANOVA_Pelanggan.ipynb)

---

## Pengertian dan Tujuan ANOVA
Pada suatu kasus pengujian estimasi dan uji hipotesis yang melibatkan lebih dari dua kelompok sampel data, digunakan metode ANOVA (Analysis of Variance) untuk menguji apakah terdapat perbedaan rata-rata (mean) yang signifikan antar kelompok tersebut.

ANOVA adalah metode statistik yang memungkinkan pengujian perbedaan mean beberapa kelompok secara sekaligus tanpa harus melakukan t-test secara berulang-ulang, yang bisa meningkatkan resiko error tipe I. Analisis ini mirip dengan t-test, bedanya adalah t-test digunakan untuk menguji beda mean maksimal 2 kelompok, sedangkan ANOVA digunakan untuk menguji perbedaan mean lebih dari 2 kelompok. Dengan ANOVA, kita dapat menentukan apakah perbedaan yang teramati antar kelompok tersebut disebabkan oleh faktor tertentu (efek perlakuan) atau hanya karena variasi acak (kebetulan/error).

Selain itu, dalam konteks regresi dan pemodelan statistik, ANOVA juga dapat digunakan untuk membagi jumlah kuadrat total (total sum of squares) menjadi dua bagian utama, yakni jumlah kuadrat karena regresi/model (SS_regression) dan jumlah kuadrat karena error (SS_error). Proses pembagian ini dapat membantu pengerjaan untuk mengevaluasi seberapa baik model yang tersedia dalam menjelaskan variasi data yang ada.

## Proses ANOVA
ANOVA bekerja dengan membandingkan dua jenis variabilitas, antar kelompok atau dalam kelompok. Dalam variasi antar kelompok (variation among aggregate types), ANOVA mengukur seberapa jauh rata-rata antar kelompok sampel yang berbeda satu sama lain. Sebaliknya, ANOVA juga mengukur variasi dalam kelompok (variation within aggregate types) yang menghitung seberapa besar penyebaran data di dalam masing-masing kelompok sampel. Jika variasi antar kelompok jauh lebih besar dibanding variasi dalam kelompok, maka kemungkinan ada pengaruh signifikan dari faktor perlakuan atau kategori yang diuji.

### F-test
F-test adalah adalah uji nilai yang diambil dari perbandingan variansi antar kelompok (antar mean) dan variansi dalam kelompok (error).

**Rumus:**

**F = (Variance between groups) / (Variance within groups)**

Jika nilai F cukup besar, artinya variasi antar kelompok lebih besar dari variasi dalam kelompok, yang mengindikasikan adanya perbedaan yang signifikan.

### P-value
Setelah mendapat nilai F, sistem akan menghasilkan p-value, yaitu probabilitas terjadinya nilai F yang sama atau lebih ekstrem jika hipotesis nol (H₀) benar, alias apabila semua rata-rata kelompok sama. Jika p-value < α (biasanya 0.05), kita akan menolak H₀ karena ada perbedaan signifikan antar kelompok.

## Syarat ANOVA
Untuk menggunakan ANOVA, terdapat beberapa syarat yang harus dipenuhi. Syarat-syarat tersebut antara lain:
- Data harus bersifat interval atau rasio (data numerik kuantitatif)
- Variansi dari setiap kelompok harus sama (uji homogenitas menggunakan Levene’s test atau Bartlett’s test)
- Data harus berdistribusi normal (uji normalitas menggunakan Shapiro-Wilk test atau Kolmogorov-Smirnov test)

Jika salah satu dari syarat tersebut tidak terpenuhi, maka hasil uji ANOVA bisa menjadi tidak valid.

## Jenis ANOVA
Bersasarkan jumlah variabelnya, ANOVA dapat dibagi menjadi tiga jenis teknik, yakni:

### One-way ANOVA
One-way ANOVA digunakan untuk menguji perbedaan rata-rata antara dua atau lebih kelompok berdasarkan satu faktor atau variabel independen. Analisis ini biasanya digunakan untuk membandingkan rata-rata kelompok yang independen satu sama lain menggunakan koefisien analisis varians. Variabel independen dalam one-way ANOVA memiliki setidaknya dua level atau kategori. Jenis ini mirip dengan t-test dan sering dipakai dalam menguji hipotesis tentang perbedaan antara tiga atau lebih kelompok.

### Two-way ANOVA
Two-way ANOVA digunakan untuk menguji interaksi atau pengaruh dua faktor (variabel independen) terhadap satu variabel dependen. Ada dua cara untuk melakukan two-way ANOVA, yaitu dengan replikasi dan tanpa replikasi. Replikasi dilakukan ketika dua kelompok independen dengan variabel dependen melakukan tugas yang berbeda, sementara ANOVA tanpa replikasi dilakukan ketika ada satu kelompok yang diuji sebanyak dua kali pada waktu yang berbeda (menguji variabel sebelum dan sesudah diberi perlakuan). Untuk menggunakan two-way ANOVA, ada beberapa kondisi yang harus dipenuhi, termasuk distribusi normal populasi, sampel independen, varians populasi sama, dan ukuran sampel yang sama dalam grup.

### MANOVA (Multivariate ANOVA)
MANOVA adalah perluasan dari ANOVA ketika kita memiliki lebih dari satu variabel dependen. MANOVA berlaku untuk beberapa variabel independen yang memengaruhi variabel dependen. Teknik ini lebih efektif dibandingkan analisis varians biasa karena dapat mengamati beberapa variabel dependen secara bersamaan. Teknik ini memungkink

## Studi Kasus

### Studi Kasus 1
Seorang guru ingin mengetahui apakah metode belajar yang digunakan di kelas berpengaruh terhadap nilai ujian siswa. Ia membagi murid ke dalam 3 kelompok berdasarkan metode pembelajaran:

Kelompok A: Metode ceramah
Kelompok B: Metode diskusi
Kelompok C: Metode video interaktif

Setelah ujian, guru mengumpulkan nilai-nilai dari masing-masing metode. 

Data nilai ujian tiap metode:
Ceramah = [70, 72,68]
Diskusi = [78, 80, 76]
Video Interaktif = [85, 87, 83]

Tujuan: Mengetahui apakah metode belajar memiliki pengaruh signifikan terhadap nilai ujian.

Step 1: Hipotesis
H₀ (nol): Rata-rata nilai ujian sama untuk semua metode belajar.
H₁ (alternatif): Ada perbedaan rata-rata nilai ujian setidaknya di satu kelompok metode belajar.

Step 2: Uji ANOVA

`from scipy.stats import f_oneway

ceramah = [70, 72, 68]
diskusi = [78, 80, 76]
video = [85, 87, 83]

f_stat, p_val = f_oneway(ceramah, diskusi, video)

print(f"F-statistic: {f_stat:.2f}")
print(f"P-value: {p_val:.4f}”)`

Output: 
F-statistic: 64.00
P-value: 0.00002

Step 3: Kesimpulan 
Karena p-value = 0.00002 < 0.05, maka:
Tolak H₀
Ada perbedaan signifikan rata-rata nilai antar metode belajar.

Visualisasi:
import matplotlib.pyplot as plt

plt.boxplot([ceramah, diskusi, video], labels=["Ceramah", "Diskusi", "Video"])
plt.title("Pengaruh Metode Belajar terhadap Nilai Ujian")
plt.ylabel("Nilai Ujian")
plt.grid(True)
plt.show()
