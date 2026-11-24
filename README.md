register:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/493793ae-7e92-480b-8629-1ace8932d146" />

login:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b3c556ae-0b3f-47c0-a6d0-9ce6571a5c1c" />


post:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9970bc38-c6ca-47ff-9c4e-b149c08b01bf" />


get All:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fcf318a1-a055-4548-8bc7-772dd0b06b21" />

get ID:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5a3fc48f-ed53-4693-a880-c704227885a1" />

put:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4f77c04b-0fae-4168-81c3-ea4a975e5a3c" />

delete:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41d44825-bd32-4b03-9171-e6be841462ac" />


1. Persiapan Lingkungan & Koneksi DatabaseInisialisasi & Konfigurasi: Proyek diinisialisasi dengan npm init -y dan dependensi (express, pg, sequelize, sequelize-cli, dotenv, nodemon, jsonwebtoken, bcrypt) dipasang. File konfigurasi .gitignore, .sequelizerc, .env, config/config.js, config/db.js, serta model Komik dan User dibuat sesuai panduan.   Kendala Koneksi PostgreSQL: Saat pertama menjalankan server (npm start), muncul error connect ECONNREFUSED 127.0.0.1:5432, dan pada pgAdmin 4 muncul connection timeout expired untuk PostgreSQL 18.   Penyelesaian: Service postgresql-x64-18 yang berstatus Stopped dijalankan melalui Windows PowerShell Run as administrator menggunakan Start-Service -Name "postgresql-x64-18" hingga berstatus Running, lalu database perpustakaan disesuaikan dengan .env.

2. Kendala & Perbaikan Saat Pengujian Endpoint di PostmanError Cannot read properties of undefined (reading 'findOne') (500): Terjadi saat POST /api/register karena models/user.js masih berisi definisi model Komik. Setelah isi models/user.js diperbaiki menjadi definisi model User, POST http://localhost:3000/api/register berhasil mengembalikan status 201 Created ("Registrasi berhasil.").   Error Invalid protocol: post http: pada URL: Terjadi saat POST http://localhost:3000/api/komik karena awalan POST  ikut tertulis di kolom URL. Setelah awalan POST  dihapus dan Bearer Token dipasang di tab Authorization, request dapat dikirim dengan benar.   Error Cannot destructure property 'email' of 'req.body' as it is undefined. (500): Terjadi saat POST /api/register dikirim tanpa body JSON yang sesuai. Pengisian body JSON (email dan password dengan format raw > JSON) menyelesaikan masalah tersebut.

3. Cakupan Endpoint yang Diuji & Tercatat di README.mdPada README.md di repository ahmadmiftianur-byte/117_JWT, dokumentasi pengujian Postman mencakup 7 alur utama berikut:register (POST /api/register): Registrasi akun pengguna baru.   login (POST /api/login): Autentikasi pengguna dan penerbitan token JWT.   post (POST /api/komik): Menambahkan data komik baru menggunakan autentikasi Bearer Token.   get All (GET /api/komik): Mengambil seluruh daftar data komik.   get ID (GET /api/komik/:id): Mengambil detail data komik berdasarkan parameter id.   put (PUT /api/komik/:id): Memperbarui data komik berdasarkan id dengan Bearer Token.   delete (DELETE /api/komik/:id): Menghapus data komik berdasarkan id dengan Bearer Token.   
