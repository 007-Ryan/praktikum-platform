1. Apa perbedaan 400 dan 404?
400 Bad Request: Server menerima request, tetapi request yang dikirim tidak valid atau salah format. Contohnya data JSON yang dikirim tidak sesuai format.
404 Not Found: Server dapat menerima request, tetapi resource atau URL yang diminta tidak ditemukan. Contohnya mengakses /users/9999 ketika data tersebut tidak ada.
Singkatnya:
400 = request-nya bermasalah, sedangkan 404 = resource yang diminta tidak ditemukan.

2. Apa perbedaan 401 dan 403?
401 Unauthorized: Client belum terautentikasi atau kredensialnya tidak valid. Biasanya terjadi karena token atau username/password belum diberikan atau salah.
403 Forbidden: Client sudah dikenali/terautentikasi, tetapi tidak memiliki izin untuk mengakses resource tersebut.
Singkatnya:
401 = belum berhasil login/identifikasi, sedangkan 403 = sudah dikenali tetapi tidak punya hak akses.

3. Mengapa 500 menunjukkan masalah pada sisi server?
500 Internal Server Error termasuk status 5xx, yaitu kesalahan yang terjadi ketika server mengalami kondisi tidak terduga saat memproses request. Misalnya terdapat bug pada program, kesalahan konfigurasi, atau kegagalan proses di server.
Jadi, server menerima request dari client, tetapi gagal menyelesaikan prosesnya dengan benar.

4. Apakah semua error HTTP berarti server mengalami kerusakan?
idak. Error HTTP tidak selalu berarti server rusak.
Contohnya:
400 → kesalahan pada request dari client.
401 → masalah autentikasi.
403 → masalah hak akses.
404 → resource tidak ditemukan.
500 → masalah internal pada server.
503 → server sedang tidak tersedia atau terlalu sibuk.
Jadi, error HTTP menunjukkan bahwa request tidak dapat