# Tugas Mandiri 3 — Analisis Authentication dan Authorization

## 1. Deskripsi Proyek

INFORHUB (Informatika Information Hub) merupakan aplikasi yang digunakan untuk memusatkan informasi kegiatan di lingkungan Fakultas Teknik, khususnya Program Studi Informatika. Aplikasi ini menyediakan informasi seminar, workshop, pelatihan, pendaftaran kegiatan, pengelolaan peserta, serta penerbitan sertifikat digital.

Dalam aplikasi INFORHUB terdapat tiga peran pengguna, yaitu Mahasiswa/Peserta, Penyelenggara, dan Administrator. Setiap peran memiliki hak akses yang berbeda sesuai dengan tugas dan tanggung jawabnya.

## 2. Peran Pengguna

1. **Mahasiswa/Peserta:** Pengguna yang dapat melihat informasi kegiatan, melakukan pendaftaran, melihat riwayat kegiatan, dan mengunduh sertifikat digital miliknya.
2. **Penyelenggara:** Pengguna yang bertugas membuat dan mengelola kegiatan, melihat daftar peserta, mengelola kehadiran, serta menerbitkan sertifikat.
3. **Administrator:** Pengguna yang bertugas mengelola akun dan hak akses pengguna, memverifikasi kegiatan, mengelola template sertifikat, serta mengawasi sistem INFORHUB.

## 3. Matriks Hak Akses

| Fitur | Mahasiswa/Peserta | Penyelenggara | Administrator | Endpoint |
|---|:---:|:---:|:---:|---|
| Melihat informasi kegiatan | ✅ | ✅ | ✅ | `GET /kegiatan` |
| Mendaftar kegiatan | ✅ | ❌ | ❌ | `POST /pendaftaran` |
| Melihat riwayat pendaftaran sendiri | ✅ | ❌ | ❌ | `GET /pendaftaran/riwayat` |
| Membuat kegiatan baru | ❌ | ✅ | ❌ | `POST /kegiatan` |
| Mengubah informasi kegiatan | ❌ | ✅ | ❌ | `PUT /kegiatan/:id` |
| Melihat daftar peserta kegiatan | ❌ | ✅ | ❌ | `GET /kegiatan/:id/peserta` |
| Mengelola kehadiran peserta | ❌ | ✅ | ❌ | `PUT /kegiatan/:id/kehadiran` |
| Menerbitkan sertifikat digital | ❌ | ✅ | ❌ | `POST /sertifikat/terbitkan` |
| Mengunduh sertifikat milik sendiri | ✅ | ❌ | ❌ | `GET /sertifikat/saya` |
| Mengelola akun dan peran pengguna | ❌ | ❌ | ✅ | `PUT /admin/pengguna/:id` |
| Memverifikasi kegiatan | ❌ | ❌ | ✅ | `PUT /admin/kegiatan/:id/verifikasi` |
| Mengelola template sertifikat | ❌ | ❌ | ✅ | `POST /admin/template-sertifikat` |

Keterangan:
- ✅ = Pengguna memiliki izin untuk mengakses fitur.
- ❌ = Pengguna tidak memiliki izin untuk mengakses fitur dan akan menerima kode `403` jika identitasnya sudah terverifikasi.
- Endpoint merupakan alamat API yang digunakan untuk mengakses fitur aplikasi.

## 4. Perbedaan Authentication dan Authorization

Authentication (autentikasi) merupakan proses pemeriksaan identitas pengguna untuk memastikan bahwa pengguna telah melakukan login dan memiliki token yang valid. Sementara itu, Authorization (otorisasi) merupakan proses pemeriksaan hak akses untuk memastikan bahwa pengguna memiliki peran yang sesuai dengan fitur yang ingin digunakan.

Contoh penerapan pada aplikasi INFORHUB:

- **Kode 401 (Unauthorized):** Diberikan ketika pengguna mengakses endpoint yang dilindungi tanpa menyertakan token atau menggunakan token yang tidak valid. Contohnya, pengguna mencoba mengakses `POST /kegiatan` tanpa melakukan login.
- **Kode 403 (Forbidden):** Diberikan ketika pengguna sudah login dan memiliki token yang valid, tetapi tidak mempunyai hak akses terhadap fitur tersebut. Contohnya, mahasiswa mencoba mengakses `POST /kegiatan` untuk membuat kegiatan baru.

## 5. Contoh Skenario Pemeriksaan Hak Akses

Misalnya, seorang mahasiswa bernama Andi sudah berhasil login ke aplikasi INFORHUB. Andi memiliki token yang valid dan dapat mengakses fitur pendaftaran kegiatan. Namun, ketika Andi mencoba membuat kegiatan baru melalui endpoint `POST /kegiatan`, sistem menolak permintaan tersebut karena fitur pembuatan kegiatan hanya diperuntukkan bagi penyelenggara.

| Keadaan | Pemeriksaan | Hasil yang Diharapkan |
|---|---|---|
| Andi mengakses `POST /kegiatan` tanpa token | Identitas belum terverifikasi | `401 Unauthorized` |
| Andi mengakses `POST /pendaftaran` dengan token valid | Identitas dan hak akses sesuai | Permintaan diizinkan |
| Andi mengakses `POST /kegiatan` dengan token valid | Identitas valid, tetapi tidak memiliki hak akses | `403 Forbidden` |

## 6. Risiko Jika Endpoint Hanya Menggunakan requireAuth

Jika endpoint penambahan kegiatan hanya menggunakan `requireAuth`, sistem hanya memeriksa apakah pengguna sudah login dan memiliki token yang valid. Akibatnya, mahasiswa yang sudah login dapat mencoba membuat kegiatan baru meskipun fitur tersebut seharusnya hanya dapat digunakan oleh penyelenggara. Oleh karena itu, endpoint tersebut juga harus menggunakan `requireRole` agar hanya pengguna dengan peran penyelenggara yang dapat menambahkan kegiatan.