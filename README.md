### Sel Pertama
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
- **cv2**: Pustaka OpenCV untuk pemrosesan gambar.
- **numpy (np)**: Pustaka untuk operasi numerik dan manipulasi array.
- **matplotlib.pyplot (plt)**: Pustaka untuk visualisasi data, khususnya plotting gambar.

### Sel Kedua
```python
def show_image(image, title='Image'):
    plt.figure(figsize=(5, 5))
    plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    plt.title(title)
    plt.axis('off')
    plt.show()
```
- **show_image(image, title='Image')**: Fungsi untuk menampilkan gambar.
  - **cv2.cvtColor(image, cv2.COLOR_BGR2RGB)**: Mengonversi gambar dari format BGR (Blue-Green-Red) ke RGB (Red-Green-Blue), karena OpenCV menggunakan BGR sedangkan Matplotlib menggunakan RGB.
  - **plt.imshow()**: Menampilkan gambar.
  - **plt.title()**: Memberi judul pada gambar.
  - **plt.axis('off')**: Menghilangkan sumbu pada plot.
  - **plt.show()**: Menampilkan plot.

### Sel Ketiga
```python
image_path = 'image.jpg'
original_image = cv2.imread(image_path)
show_image(original_image, 'Original Image')
```
- **cv2.imread(image_path)**: Membaca gambar dari path yang diberikan (`image.jpg`).
- **show_image(original_image, 'Original Image')**: Menampilkan gambar asli dengan judul "Original Image".

### Sel Keempat
```python
gray_image = cv2.cvtColor(original_image, cv2.COLOR_BGR2GRAY)
show_image(gray_image, 'Grayscale Image')
```
- **cv2.cvtColor(original_image, cv2.COLOR_BGR2GRAY)**: Mengonversi gambar dari format BGR ke skala abu-abu.
- **show_image(gray_image, 'Grayscale Image')**: Menampilkan gambar skala abu-abu dengan judul "Grayscale Image".

### Sel Kelima
```python
blurred_image = cv2.GaussianBlur(gray_image, (5, 5), 0)
show_image(blurred_image, 'Blurred Image')
```
- **cv2.GaussianBlur(gray_image, (5, 5), 0)**: Menerapkan Gaussian Blur pada gambar skala abu-abu.
  - **(5, 5)**: Ukuran kernel Gaussian.
  - **0**: Standar deviasi di kedua arah (x dan y).
- **show_image(blurred_image, 'Blurred Image')**: Menampilkan gambar yang telah di-blur dengan judul "Blurred Image".

### Sel Keenam
```python
edge_image = cv2.Canny(blurred_image, 50, 150)
show_image(edge_image, 'Edge Image')
```
- **cv2.Canny(blurred_image, 50, 150)**: Menerapkan algoritma Canny Edge Detection pada gambar yang telah di-blur.
  - **50**: Batas bawah untuk histeresis.
  - **150**: Batas atas untuk histeresis.
- **show_image(edge_image, 'Edge Image')**: Menampilkan gambar hasil deteksi tepi dengan judul "Edge Image".

### Sel Ketujuh
```python
h, w = original_image.shape[:2]
M = np.float32([[1, 0, 60], [0, 1, 40]])
translated_image = cv2.warpAffine(original_image, M, (w, h))
show_image(translated_image, 'Translated Image')
```
- **original_image.shape[:2]**: Mendapatkan tinggi (h) dan lebar (w) gambar asli.
- **np.float32([[1, 0, 60], [0, 1, 40]])**: Membuat matriks transformasi untuk translasi.
  - **[[1, 0, 60], [0, 1, 40]]**: Mentranslasi gambar 60 piksel ke kanan dan 40 piksel ke bawah.
- **cv2.warpAffine(original_image, M, (w, h))**: Menerapkan transformasi afine (translasi) pada gambar asli.
- **show_image(translated_image, 'Translated Image')**: Menampilkan gambar yang telah ditranslasi dengan judul "Translated Image".
