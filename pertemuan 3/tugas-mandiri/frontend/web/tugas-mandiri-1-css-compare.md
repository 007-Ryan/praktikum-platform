Tugas Mandiri 1 — Perbandingan Component-Based dan Utility-First

1. Tujuan
Tugas ini bertujuan membandingkan pendekatan CSS berbasis komponen (*component-based*) dan pendekatan berbasis class utility (*utility-first*) dalam pembuatan kartu profil.
Kedua halaman menggunakan konten yang sama, yaitu foto profil, nama Citra, NIM 2026002, dan tombol Lihat Profil.

2. Pendekatan Component-Based
Pada pendekatan component-based, aturan tampilan ditulis menggunakan CSS di dalam tag `<style>`. Setiap bagian tampilan memiliki class khusus, seperti `.card`, `.profile-image`, `.profile-name`, dan `.btn`.
Pendekatan ini memudahkan pengelolaan tampilan melalui aturan CSS yang terpusat. Jika warna tombol ingin diubah, saya cukup mengubah properti `background-color` pada class `.btn`.

3. Pendekatan Utility-First
Pada pendekatan utility-first, saya menggunakan Tailwind CSS melalui CDN. Tampilan setiap elemen diatur dengan menggabungkan class utility secara langsung di atribut `class`.
Contohnya, class `rounded-2xl` digunakan untuk sudut membulat, `bg-white` untuk latar putih, `p-4` untuk padding, dan `shadow-md` untuk bayangan.
Pendekatan ini mengurangi kebutuhan menulis aturan CSS sendiri, tetapi atribut class dapat menjadi panjang karena berisi banyak utility.

4. Perbandingan
| Aspek | Component-Based | Utility-First |
|---|---|---|
| Teknologi | HTML dan CSS biasa | HTML dan Tailwind CSS |
| Pengaturan tampilan | Class komponen dan aturan CSS | Gabungan class utility |
| Lokasi pengaturan warna | Aturan CSS `.card` atau `.btn` | Class seperti `bg-white` atau `bg-blue-600` |
| Penggunaan ulang | Class CSS dapat digunakan pada banyak elemen | Kombinasi utility dapat digunakan kembali |
| Perubahan tema | Mengubah aturan CSS terpusat | Mengubah class utility pada elemen terkait |
| Kerapian HTML | Class komponen relatif singkat | Atribut class bisa panjang |
| Ketergantungan internet | Tidak untuk CSS internal | CDN memerlukan internet |

5. Jumlah Baris CSS dan Class Utility
Jumlah baris CSS versi component-based dihitung berdasarkan isi tag `<style>` pada file HTML, termasuk baris kosong dan komentar jika ada. Jumlah class utility dihitung berdasarkan seluruh pemakaian class Tailwind pada file utility-first, dengan setiap token class dihitung satu kali pemakaian.

Jumlah baris CSS versi component-based: 75 baris.
Jumlah pemakaian class utility versi utility-first: 36 class.
Waktu pengerjaan versi component-based: 20 menit.
Waktu pengerjaan versi utility-first: 15 menit. 

6. Pengujian Responsif
Kedua halaman diuji pada tampilan laptop dan lebar layar 360 piksel. Pada layar kecil, ukuran gambar, jarak antar elemen, padding, dan ukuran teks disesuaikan agar kartu tetap terbaca.
Hasil akhir pengujian perlu memastikan bahwa kedua halaman tidak menimbulkan gulir horizontal pada lebar layar 360 piksel.
Dokumentasi Screenshot
1. `component-laptop.png` — tampilan component-based pada laptop.
2. `component-360px.png` — tampilan component-based pada lebar 360 piksel.
3. `utility-laptop.png` — tampilan utility-first pada laptop.
4. `utility-360px.png` — tampilan utility-first pada lebar 360 piksel.


7. Kesimpulan
Berdasarkan percobaan ini, component-based sesuai ketika proyek membutuhkan aturan tampilan yang terpusat dan konsisten untuk banyak komponen. Utility-first sesuai ketika saya ingin menyusun dan menyesuaikan tampilan langsung pada elemen HTML dengan bantuan class yang telah tersedia.
Untuk proyek akhir, saya akan memilih component-based apabila banyak halaman memakai komponen dengan desain yang sama dan membutuhkan pengelolaan CSS terpusat. Saya akan memilih utility-first apabila proyek membutuhkan pengembangan antarmuka yang cepat dan penyesuaian tata letak langsung pada elemen.

8. Kesimpulan akhir ini akan disesuaikan dengan hasil pengujian dan waktu pengerjaan yang benar-benar saya alami.
