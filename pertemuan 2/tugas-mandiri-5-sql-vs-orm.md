A. SQL Mentah
Dengan menggunakan Node.js dan library mysql2, operasi mengambil data berdasarkan ID dapat ditulis sebagai berikut:
const mysql = require('mysql2/promise');
async function getJadwal() {
    const connection = await mysql.createConnection({
        host: 'localhost',
        user: 'root',
        password: '',
        database: 'kampus'
    });
    const [rows] = await connection.execute(
        'SELECT * FROM jadwal WHERE id = ?',
        [1]
    );
    console.log(rows);
    await connection.end();
}
getJadwal();

Pada kode tersebut, SQL ditulis secara langsung menggunakan:
SELECT * FROM jadwal WHERE id = ?

Tanda ? digunakan sebagai placeholder untuk nilai ID sehingga nilai dapat dikirim melalui parameter [1].

B. ORM Prisma
Operasi yang sama dapat dilakukan menggunakan Prisma ORM:
const { PrismaClient } = require('@prisma/client');
const prisma = new PrismaClient();
async function getJadwal() {
    const jadwal = await prisma.jadwal.findUnique({
        where: {
            id: 1
        }
    });
    console.log(jadwal);
}
getJadwal();

Pada pendekatan ini, kita tidak perlu menulis perintah SQL SELECT secara langsung. Prisma menyediakan method findUnique() untuk mengambil satu data berdasarkan nilai id.

C. Perbandingan
| Aspek | SQL Mentah | ORM Prisma |
|---|---|---|
| Cara penulisan | Menulis SQL secara langsung | Menggunakan method dan object |
| Contoh | `SELECT * FROM jadwal WHERE id = ?` | `prisma.jadwal.findUnique()` |
| Kemudahan | Perlu memahami SQL | Lebih sederhana untuk programmer aplikasi |
| Kontrol SQL | Lebih bebas dan detail | Sebagian dikendalikan oleh ORM |
| Penggunaan | Cocok untuk query kompleks dan kontrol database | Cocok untuk pengembangan aplikasi yang cepat dan terstruktur |


PENJELASAN :
1. Apa perbedaan SQL mentah dan ORM?
SQL mentah adalah pendekatan dengan menulis perintah SQL secara langsung, seperti SELECT, INSERT, atau UPDATE. Sedangkan ORM (Object-Relational Mapping) memungkinkan programmer mengakses

2. Apa kelebihan SQL mentah?
SQL mentah memberikan kontrol yang lebih besar terhadap query database karena programmer dapat menentukan query secara langsung. Pendekatan ini juga cocok digunakan untuk query yang kompleks dan membutuhkan optimasi khusus.

3. Apa kelebihan ORM?
ORM membuat kode akses database lebih sederhana dan mudah dibaca karena programmer tidak perlu selalu menulis SQL secara langsung. ORM juga membantu mengelola relasi antar tabel, menyediakan fitur keamanan, dan mempercepat proses pengembangan aplikasi.

4. Apa risiko SQL injection?
SQL injection adalah serangan ketika input dari pengguna dimasukkan ke dalam query SQL secara tidak aman sehingga penyerang dapat memanipulasi perintah database. Dampaknya dapat berupa membaca, mengubah, atau menghapus data yang seharusnya tidak dapat diakses.

5. Mengapa penggunaan parameter query dapat mengurangi risiko SQL injection?
Parameter query memisahkan perintah SQL dari data yang diberikan pengguna. Dengan menggunakan placeholder seperti ?, input pengguna diperlakukan sebagai data, bukan sebagai bagian dari perintah SQL, sehingga karakter atau perintah berbahaya tidak mudah dieksekusi sebagai SQL.

6. Bagaimana ORM membantu programmer dalam mengakses database?
ORM menyediakan method dan objek untuk melakukan operasi database tanpa harus menulis SQL secara manual untuk setiap operasi. Misalnya, Prisma menyediakan findUnique(), create(), update(), dan delete() sehingga programmer dapat melakukan CRUD dengan kode yang lebih terstruktur dan mudah dipelihara.