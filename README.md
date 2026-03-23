Sabrina Aska Amalina - A11.2023.15264

# Dockerize WordPress dengan MySQL dan Redis

Stack yang digunakan:

- WordPress
- MySQL 5.7
- Redis
- Docker Compose

## Langkah-langkah Menjalankan Stack

### 1. Pastikan Docker sudah terpasang

Cek instalasi Docker dan Docker Compose:

```bash
docker --version
docker compose version
```

### 2. Masuk ke folder project

### 3. Jalankan semua container

```bash
docker compose up -d
```

### 4. Cek comtainer yang berjalan

```bash
docker ps
```

//image

## Wordpress Installation Page

//image

## Wordpress Dashboard

//image

## Menampilkan Container yang Running

//image

## Redis CLI Ping Test

//image

## Jawaban dari Soal

### 1. Kenapa perlu volume untuk MySQL?

Volume diperlukan agar data MySQL tetap tersimpan walaupun container dihentikan, direstart, atau dibuat ulang. Tanpa volume, data database akan hilang saat container dihapus. Karena itu, volume sangat penting untuk menjaga data WordPress seperti postingan, user, dan konfigurasi tetap aman.

### 2. Apa fungsi `depends_on`?

`depends_on` digunakan untuk mengatur urutan startup antar service. Yang dimaksud pada project kali ini, WordPress membutuhkan MySQL dan Redis agar bisa berjalan dengan baik. Dengan `depends_on`, WordPress akan menunggu service yang dibutuhkan dijalankan lebih dulu.

### 3. Bagaimana cara WordPress container connect ke MySQL?

WordPress terhubung ke MySQL melalui Docker network internal. Pada file `docker-compose.yml`, WordPress menggunakan hostname mysql, yaitu nama service MySQL. Karena semua container berada dalam network yang sama, WordPress bisa mengakses MySQL dengan konfigurasi seperti:

```bash
WORDPRESS_DB_HOST: mysql:3306
```

berarti WordPress tidak memakai `localhost`, tetapi memakai nama service MySQL di dalam jaringan Docker.

### 4. Apa keuntungan pakai Redis untuk WordPress?

Redis membantu WordPress dengan menyimpan cache di memory. Ini membuat proses akses data menjadi lebih cepat karena WordPress tidak selalu perlu mengambil data berulang kali dari database MySQL. Hasilnya, performa website bisa menjadi lebih ringan, lebih cepat, dan lebih efisien.
