
# NAMA : SALSABILLAH
# NIM : 202231033
# KELAS : D


## PENJELASAN

## MEDIAN FILTERING
### 1. Import Library
import cv2 

import numpy as np

import matplotlib.pyplot as plt perbaris

### 2. Membaca gambar
#### #Masukan foto kita
image = cv2.imread('salsa.jpg')


### 3. Untuk menampilkan gambar asli 
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)

plt.title('Citra Asli')

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))

plt.axis('on') #Menampilkan sumbu

### 4. Median filtering menggunakan OpenCV
median_filtered = cv2.medianBlur(image, 5) 

### 5. Untuk menampilkan hasil median filtering
plt.subplot(1, 2, 2)

plt.title('After Filter Median')

plt.imshow(cv2.cvtColor(median_filtered, cv2.COLOR_BGR2RGB))

plt.axis('on') #Menampilkan sumbu


plt.show()

## MEAN FILTERING

### 1. Definisi mean filtering manual 

 def mean_filter_manual(image, kernel_size): 
 
 m, n = image.shape
 
 pad_size = kernel_size // 2
 
 padded_image = np.pad(image, pad_size, mode='constant', constant_values=0)
 
 mean_filtered_image = np.zeros_like(image)
 
for i in range(m):

for j in range(n):

region = padded_image[i:i + kernel_size, j:j + kernel_size]

mean_value = np.mean(region)

mean_filtered_image[i, j] = mean_value

return mean_filtered_image

### 2.  Membaca gambar dalam mode grayscale 
image = cv2.imread('salsa.jpg', cv2.IMREAD_GRAYSCALE)

### 3. Menentukan ukuran kernel 
kernel_size = 3

### 4. Mean filtering menggunakan fungsi manual
mean_filtered = mean_filter_manual(image, kernel_size)

### 5. Tampilkan hasil mean filtering 
plt.figure(figsize=(10, 5))

### 6. Menampilkan gambar asli 
plt.subplot(1, 2, 1)

plt.title('Original Image')

plt.imshow(image, cmap='gray')

plt.axis('on') #Menampilkan sumbu

### 7. Menampilakan Mean filtering
plt.subplot(1, 2, 2)

plt.title('Mean Filtered Image')

plt.imshow(mean_filtered, cmap='gray')

plt.axis('on') #Menampilkan sumbu

plt.show()




# TEORI : FILTERING CITRA

Filtering citra adalah proses yang digunakan untuk mengubah atau memodifikasi gambar digital dengan tujuan tertentu, seperti meningkatkan kualitas gambar, menghilangkan noise, atau mengekstraksi fitur penting yang ada dalam gambar. Filter dapat diterapkan di domain spasial (langsung pada piksel gambar) atau di domain frekuensi (menggunakan transformasi seperti Fourier).

Jenis-Jenis Filter yang Digunakan
Pada proyek ini, dua jenis teknik filtering yang digunakan adalah Median Filtering dan Mean Filtering. 

Berikut penjelasan lebih detail tentang masing-masing teknik:

#### 1. Median Filtering
Median filtering adalah teknik non-linear yang mengganti nilai setiap piksel dalam gambar dengan nilai median dari piksel-piksel di sekitarnya. Median filtering sangat efektif untuk menghilangkan noise impulsif, seperti salt-and-pepper noise, yang sering muncul sebagai titik-titik putih dan hitam yang tersebar secara acak dalam gambar.

Langkah-langkah Median Filtering:

1. Tentukan ukuran jendela atau kernel (biasanya berukuran 3x3, 5x5, dll.).
2. Pindahkan kernel tersebut ke seluruh piksel dalam gambar.
3. Untuk setiap posisi kernel, ambil nilai piksel dalam jendela tersebut.
4. Hitung nilai median dari piksel-piksel tersebut.
5. Ganti nilai piksel tengah di jendela dengan nilai median yang telah dihitung.
6. Lanjutkan proses ini untuk semua piksel dalam gambar.

####
Median filtering tidak hanya menghilangkan noise tetapi juga menjaga tepi-tepi objek dalam gambar, yang sering kali menjadi masalah dengan filter linear.


#### 2. Mean filtering
Mean filtering, juga dikenal sebagai average filtering, adalah teknik smoothing yang mengganti setiap piksel dalam gambar dengan nilai rata-rata dari piksel-piksel di sekitarnya. Mean filtering digunakan untuk mengurangi noise dengan membuat gambar lebih halus. Meskipun efektif dalam menghilangkan noise acak, mean filtering cenderung mengaburkan tepi-tepi objek dalam gambar.

####
#### Langkah-langkah Mean Filtering:

1. Tentukan ukuran jendela atau kernel (biasanya berukuran 3x3, 5x5, dll.).

2. Pindahkan kernel tersebut ke seluruh piksel dalam gambar.
3. Untuk setiap posisi kernel, ambil nilai piksel dalam jendela tersebut.
4. Hitung nilai rata-rata dari piksel-piksel tersebut.
5. Ganti nilai piksel tengah di jendela dengan nilai rata-rata yang telah dihitung.
6. Lanjutkan proses ini untuk semua piksel dalam gambar.

Mean filtering melakukan smoothing dengan cara mengurangi variasi antara piksel-piksel, sehingga noise acak dalam gambar berkurang. Namun, karena nilai rata-rata dipengaruhi oleh semua piksel dalam jendela, tepi-tepi yang tajam juga bisa menjadi kabur.






