1. Apa perbedaan hasil kedua perintah tersebut?
Perbedaan hasil kedua perintah tersebut adalah curl -s hanya menampilkan response body tanpa menampilkan informasi tambahan, sedangkan curl -i menampilkan response body sekaligus HTTP response header.

2. Apa fungsi opsi -s?
Opsi -s (silent) berfungsi menjalankan curl tanpa menampilkan progress meter atau pesan tambahan.

3. Apa fungsi opsi -i?
Opsi -i (include) berfungsi menyertakan HTTP response header, seperti status 200 OK dan Content-Type, bersama dengan response body.

4. Kapan Anda menggunakan masing-masing opsi?
Gunakan -s ketika ingin melihat data response dengan tampilan yang lebih bersih, sedangkan -i digunakan ketika ingin memeriksa status code dan header HTTP dari response.