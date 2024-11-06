# Tugas Pertemuan 8 

**Nama** : Yacobus Daeli

**NIM** : H1D022024

**Shift** : E

# Proses Login untuk file PHP Native

1. File koneksi.php:

 - File ini digunakan untuk menghubungkan aplikasi dengan database MySQL.

 - Mengonfigurasi pengaturan CORS (Cross-Origin Resource Sharing), agar API dapat diakses oleh aplikasi Ionic.

2. File login.php:

 - Berfungsi memproses data login yang dikirim oleh pengguna.

 - Menerima username dan password dari aplikasi Ionic.

 - Mengonversi password ke format MD5 agar cocok dengan yang tersimpan di database.

 - Mengecek database menggunakan query SELECT untuk memverifikasi keabsahan data pengguna.

3. Proses Verifikasi:

  Jika data pengguna ditemukan, sistem akan melakukan langkah-langkah berikut:
  -Membuat token dari kombinasi waktu dan password.
 
  - Mengirim respons berisi username, token, dan status login berhasil.

  - Jika data pengguna tidak ditemukan, sistem akan mengirim respons yang menunjukkan status login gagal.

# Keammanan
1. Validasi pengguna menggunakan Token
 - Sistem menggunakan token sebagai metode validasi untuk memastikan bahwa pengguna yang mengakses aplikasi adalah pengguna yang sah.
2. Keamanan Password
 - Password yang disimpan di database telah dienkripsi menggunakan MD5 untuk melindungi keamanan data.
3. Proteksi dengan Guard
 - Semua route dilindungi dengan Guard untuk memastikan hanya pengguna yang sudah login yang dapat mengakses halaman-halaman tertentu.
4. Validasi Input pada Form Login
 - Form login dilengkapi dengan validasi input. Jika pengguna mencoba login tanpa mengisi salah satu atau kedua field (username atau password), sistem akan menampilkan pesan error "Username atau Password Tidak Boleh Kosong".
5. Perlindungan API dengan CORS
 - CORS (Cross-Origin Resource Sharing) diaktifkan untuk melindungi API, sehingga hanya aplikasi yang diizinkan yang dapat mengakses data melalui API.


# Proses untuk Login
 - Sebelum mengakses aplikasi, pengguna harus login terlebih dahulu.

 - Pengguna mengisi username dan password pada form login yang tersedia.

 - Sistem akan memverifikasi data dengan memeriksa database untuk memastikan bahwa username dan password yang dimasukkan valid.

 - Keamanan password dalam database dilindungi dengan enkripsi menggunakan metode MD5.

 - Jika username dan password benar, pengguna akan berhasil masuk ke dalam aplikasi.

 - Jika username atau password salah, pengguna tidak dapat masuk dan harus mengulangi proses login.

# Mengatur Login di Ionic
1. Service (authentication.service.ts):
   
* File ini bertanggung jawab untuk mengelola proses login ke API PHP.
+ Menyediakan fungsi untuk menyimpan token dan username ke penyimpanan lokal menggunakan Preferences.
- Mengelola status login pengguna dan menangani pesan error yang mungkin terjadi selama proses login.

2. Guard:

Terdapat dua file utama untuk menjaga keamanan akses pengguna:

> 1. auth.guard.ts:
 - Bertindak sebagai pengaman yang memverifikasi apakah pengguna sudah login atau belum.
 - Jika belum login, pengguna akan diarahkan ke halaman login; jika sudah login, mereka dapat mengakses halaman home.

> 2. auto-login.guard.ts: 
 - Memeriksa status login saat aplikasi dibuka pertama kali.
 - Jika pengguna telah login sebelumnya, mereka langsung diarahkan ke halaman home; jika belum, tetap berada di halaman login.

> 3. Halaman Login (login.page.ts):
 - Pada halaman login, proses dimulai saat pengguna menekan tombol login.
 - Sistem akan memeriksa apakah username dan password telah diisi. Jika belum, muncul pesan error.
 - Jika data sudah lengkap, informasi dikirim ke API PHP.

Setelah menerima respons dari API:
 - Jika login berhasil, token dan username disimpan, form login dikosongkan, dan pengguna diarahkan ke halaman home.
 - Jika login gagal, muncul pesan "Username atau Password Salah".
 - Jika terjadi masalah koneksi, seperti server tidak aktif, muncul pesan "Login Gagal, Periksa Koneksi Internet".

4. Halaman Home (home.page.ts):
 - Menampilkan nama pengguna yang sedang login.
 - Memiliki tombol logout untuk keluar dari aplikasi.
 - Saat tombol logout ditekan, sistem akan:
 - Menghapus token dan username dari penyimpanan.
 - Mengatur status login menjadi false.
 - Mengarahkan pengguna kembali ke halaman login.

## Tampilan Halaman Login 

![Tampilan Halaman Login](https://github.com/user-attachments/assets/e6893d82-46ca-492b-bbb5-3f8b2ff97256)


## Tampilan Login jika password / username salah 

![Tampilan Halaman Login(False)](https://github.com/user-attachments/assets/8798d850-31c8-406e-9671-47556b86b3ad)


## Tampilan Login jika password benar
![Tampilan Halaman (True)](https://github.com/user-attachments/assets/b7be1f02-6152-4498-abc8-58e0e6176c29)








