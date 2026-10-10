1. Apa yang dimaksud request?
Request adalah permintaan yang dikirim oleh client kepada server untuk meminta atau melakukan suatu proses. Request dapat berisi method HTTP, URL, query parameter, header, dan request body.
Contohnya:
GET https://httpbin.org/get?nama=Umar&kelas=TI
Pada contoh tersebut, browser atau aplikasi bertindak sebagai client yang mengirim request kepada server HTTPBin.

2. Apa yang dimaksud response?
Response adalah balasan yang diberikan oleh server kepada client setelah server menerima dan memproses request.
Response biasanya berisi:
Status code, misalnya 200 OK
Header response
Body, yaitu data yang dikembalikan server
Pada endpoint /get, HTTPBin akan mengembalikan informasi mengenai request yang diterimanya, termasuk query parameter.

3. Apa fungsi query parameter?
Query parameter digunakan untuk mengirimkan data tambahan melalui URL kepada server.
Contohnya:
https://httpbin.org/get?nama=Umar&kelas=TI
Pada URL tersebut:
nama=Umar adalah query parameter pertama.
kelas=TI adalah query parameter kedua.
Tanda ? menandai awal query parameter.
Tanda & digunakan untuk memisahkan beberapa parameter.
Query parameter biasanya digunakan untuk filter, pencarian, pengurutan, atau memberikan informasi tambahan kepada server.

4. Apa fungsi HTTP header?
HTTP header digunakan untuk mengirimkan informasi tambahan mengenai request atau response.
Contohnya header dapat memberikan informasi seperti:
Jenis browser atau aplikasi yang digunakan.
Jenis data yang diterima.
Jenis data yang dikirim.
Informasi autentikasi.
Informasi mengenai koneksi.
Pada:
GET https://httpbin.org/headers
HTTPBin akan menampilkan header yang diterima oleh server dari client.

5. Apa perbedaan data pada URL dengan data pada request body?
Perbedaannya terletak pada tempat data dikirimkan.
Aspek	Data pada URL	Data pada Request Body
Letak	Di URL	Di bagian body request
Contoh	?nama=Umar&kelas=TI	{"nama":"Umar","kelas":"TI"}
Umumnya digunakan	GET	POST, PUT, PATCH
Terlihat pada URL	Ya	Tidak terlihat pada URL
Cocok untuk	Filter, pencarian, parameter	Mengirim data yang lebih kompleks


Gambaran Sederhananya :
CLIENT
  │
  │ Request
  │ GET /get?nama=Umar&kelas=TI
  │ Header: ...
  ↓
SERVER HTTPBIN
  │
  │ Memproses request
  ↓
  │ Response
  │ Status: 200 OK
  │ Body: informasi request
  ↓
CLIENT