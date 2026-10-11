Tugas Mandiri 2 — Layout dengan Tailwind CSS

1. Tujuan
Tugas ini bertujuan untuk mempelajari penggunaan Tailwind CSS dalam membuat tata letak halaman web yang responsif. Halaman web yang dibuat berisi navbar, hero section, tiga kartu informasi, dan footer.

2. Implementasi Layout
File HTML yang digunakan adalah `tugas-mandiri-2-layout.html`. Tailwind CSS dipanggil melalui CDN sehingga class utility dapat langsung digunakan pada elemen HTML tanpa menulis CSS secara manual.

### A. Navbar
Navbar digunakan sebagai navigasi halaman dengan menu Beranda, Profil, dan Kontak.
Class yang digunakan:
- `flex`: mengatur elemen menggunakan Flexbox.
- `flex-col`: menyusun elemen secara vertikal pada layar kecil.
- `md:flex-row`: menyusun elemen secara horizontal pada layar berukuran medium ke atas.
- `gap-3` dan `gap-4`: memberikan jarak antar elemen.
- `md:justify-between`: memberikan jarak di antara elemen navbar pada layar medium ke atas.
- `hover:text-yellow-300`: mengubah warna teks ketika kursor diarahkan ke menu.

### B. Hero Section
Hero section berisi judul, deskripsi, tombol, dan ilustrasi profil mahasiswa.
Class yang digunakan:
- `grid`: mengatur tata letak menggunakan CSS Grid.
- `grid-cols-1`: menampilkan satu kolom pada layar kecil.
- `md:grid-cols-2`: menampilkan dua kolom pada layar medium ke atas.
- `items-center`: menyelaraskan elemen secara vertikal.
- `gap-6`: memberikan jarak antar kolom.
- `md:text-5xl`: memperbesar ukuran judul pada layar medium ke atas.
- `hover:bg-blue-800`: mengubah warna tombol ketika kursor diarahkan ke tombol.

### C. Kartu Informasi
Bagian ini berisi tiga kartu, yaitu Biodata, Jadwal Kuliah, dan Kegiatan.
Class yang digunakan:
- `grid grid-cols-1`: menampilkan kartu dalam satu kolom pada layar kecil.
- `md:grid-cols-3`: menampilkan tiga kolom pada layar medium ke atas.
- `gap-6`: memberikan jarak antar kartu.
- `rounded-xl`: membuat sudut kartu melengkung.
- `shadow-md`: memberikan bayangan pada kartu.
- `hover:-translate-y-1`: menggeser kartu sedikit ke atas ketika kursor diarahkan ke kartu.
- `hover:shadow-xl`: memperbesar bayangan kartu ketika kursor diarahkan ke kartu.

### D. Footer
Footer menampilkan nama halaman dan keterangan praktikum.
Class yang digunakan:
- `bg-slate-800`: memberikan warna latar belakang gelap.
- `px-4` dan `py-6`: memberikan ruang di sisi horizontal dan vertikal.
- `text-center`: meratakan teks ke tengah.
- `text-white`: mengubah warna teks menjadi putih.

3. Penerapan Responsive Design
Responsive design diterapkan menggunakan class breakpoint `md:`. Pada layar kecil, navbar disusun secara vertikal, hero section menggunakan satu kolom, dan kartu informasi ditampilkan dalam satu kolom. Pada layar medium ke atas, navbar disusun secara horizontal, hero section menjadi dua kolom, dan kartu informasi menjadi tiga kolom.
Class `hover:` digunakan untuk memberikan perubahan tampilan saat kursor diarahkan ke menu, tombol, dan kartu informasi.

4. Kesimpulan
Tailwind CSS memudahkan pembuatan layout web karena menyediakan class utility untuk mengatur warna, jarak, ukuran teks, Flexbox, Grid, dan efek interaksi secara langsung pada elemen HTML. Penggunaan class utility membuat pengaturan tampilan lebih praktis dan mengurangi kebutuhan menulis CSS secara manual. Namun, penggunaan class yang terlalu banyak dalam satu elemen dapat membuat HTML terlihat panjang sehingga penamaan dan pengelompokan class perlu diperhatikan.

5. Dokumentasi Screenshot
- `layout-laptop.png` — tampilan halaman pada layar laptop.
- `layout-360px.png` — tampilan halaman pada lebar layar 360 px.