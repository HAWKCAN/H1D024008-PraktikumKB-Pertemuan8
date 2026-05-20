Nama: FARIZ RAHMAN SYAHIDA  
NIM: H1D024008  
Shift: Shift Awal : C - Shift Akhir : G  

---

## Tugas 8: Klasifikasi Gambar Rock-Paper-Scissors menggunakan CNN

Repository ini berisi skrip Python untuk melakukan klasifikasi gambar permainan tangan (Batu, Gunting, Kertas) menggunakan algoritma Deep Learning berbasis Convolutional Neural Network (CNN) dengan framework TensorFlow dan Keras.

### Deskripsi Dataset
Program ini membaca dataset gambar dari folder lokal bernama `archive`. Dataset ini diproses untuk mengidentifikasi 3 kelas klasifikasi utama, yaitu:
* `rock` (Batu)
* `paper` (Kertas)
* `scissors` (Gunting)

Gambar diproses, dinormalisasi nilainya, dan dibagi secara otomatis oleh program menjadi 80% data latih (training) dan 20% data validasi (validation).

### Pembaruan Terkini pada Kode
* **Pemilihan Kelas Eksplisit**: Generator data telah disesuaikan menggunakan parameter `classes=['rock', 'paper', 'scissors']`. Hal ini mencegah Keras membaca folder tambahan (seperti `rps-cv-images`) sebagai kategori kelas baru yang menyebabkan error perbedaan dimensi target dan output.
* **Penambahan Kompilasi Model**: Model sekarang memuat tahap `model.compile()` menggunakan optimizer `adam` dan fungsi loss `categorical_crossentropy` sebelum proses pelatihan dijalankan.

### Struktur Kode Program
Alur kerja program terdiri dari beberapa tahapan utama:
1. **Prapemrosesan Data**: `ImageDataGenerator` digunakan untuk memuat gambar, menyeragamkan ukuran menjadi 150x150 piksel, melakukan normalisasi rentang piksel (1./255), serta menyaring direktori agar hanya mengambil 3 folder kelas utama.
2. **Arsitektur Model**: Menggunakan model CNN sekuensial yang terdiri dari ekstraksi fitur melalui tiga pasang layer `Conv2D` dan `MaxPooling2D`. Data kemudian diratakan dengan layer `Flatten` menuju layer `Dense` berukuran 512 neuron, lalu ditutup dengan output layer berukuran 3 neuron (aktivasi Softmax) untuk penentuan kelas.
3. **Pelatihan Model**: Model dilatih selama 10 epoch menggunakan aliran data gambar dari generator latih.
4. **Evaluasi dan Prediksi**: Program menghitung dan mencetak nilai loss serta akurasi pada data validasi, diakhiri dengan mencetak matriks probabilitas hasil prediksi untuk kelas-kelas tersebut.

### Ketergantungan (Prasyarat)
Pastikan pustaka Python berikut sudah terpasang pada lingkungan kerja Anda:
* tensorflow
* pandas
* numpy

### Cara Menjalankan Program
1. Pastikan skrip diletakkan sejajar dengan folder direktori bernama `archive/`.
2. Di dalam folder `archive/` tersebut, pastikan terdapat direktori `rock`, `paper`, dan `scissors` yang berisi gambar.
3. Buka terminal atau command prompt, lalu jalankan program dengan perintah:
   python Percobaan.py