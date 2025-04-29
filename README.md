# UTS-VISI-KOMPUTER
Segmentasi Citra pada Citra Asli Buah Jeruk Berdasarkan Nilai Thresholding.

codingannya :
```python
# Import library yang diperlukan
import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab import files

# Upload file gambar
print("Silakan upload gambar buah jeruk...")
uploaded = files.upload()

# Ambil nama file gambar
image_filename = list(uploaded.keys())[0]

# Membaca gambar asli
image = cv2.imread(image_filename)
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Menampilkan gambar asli
plt.figure(figsize=(6,6))
plt.imshow(image_rgb)
plt.title('Gambar Asli Buah Jeruk')
plt.axis('off')
plt.show()

# Konversi ke grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Menampilkan gambar grayscale
plt.figure(figsize=(6,6))
plt.imshow(gray_image, cmap='gray')
plt.title('Gambar Grayscale Buah Jeruk')
plt.axis('off')
plt.show()

# Membuat histogram grayscale
plt.figure(figsize=(8,4))
plt.hist(gray_image.ravel(), 256, [0,256])
plt.title('Histogram Grayscale')
plt.xlabel('Intensitas Pixel')
plt.ylabel('Jumlah Pixel')
plt.show()

# Thresholding Manual (threshold = 127)
threshold_value = 127
ret, thresh_manual = cv2.threshold(gray_image, threshold_value, 255, cv2.THRESH_BINARY)

# Thresholding Otomatis (Metode Otsu)
ret2, thresh_otsu = cv2.threshold(gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Menampilkan hasil threshold manual dan Otsu
plt.figure(figsize=(12,6))

plt.subplot(1,2,1)
plt.imshow(thresh_manual, cmap='gray')
plt.title(f'Threshold Manual (T={threshold_value})')
plt.axis('off')

plt.subplot(1,2,2)
plt.imshow(thresh_otsu, cmap='gray')
plt.title(f'Threshold Otsu (T={int(ret2)})')
plt.axis('off')

plt.show()

# Menyimpan hasil ke file
cv2.imwrite('hasil_threshold_manual.jpg', thresh_manual)
cv2.imwrite('hasil_threshold_otsu.jpg', thresh_otsu)

print("Selesai! Hasil threshold telah disimpan sebagai 'hasil_threshold_manual.jpg' dan 'hasil_threshold_otsu.jpg'")
```

Hasil keluaran (Output)
![image](https://github.com/user-attachments/assets/3f3db904-521e-4950-84d4-5103fdba2e16)
![image](https://github.com/user-attachments/assets/136884fb-d9f8-4870-b610-bbabfd4745a7)
![image](https://github.com/user-attachments/assets/a70808ee-cf1c-457d-8fdc-6e7ed0e37d63)



