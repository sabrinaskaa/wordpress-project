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

<img width="1920" height="1080" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/1d77dab2-7d57-4b44-918c-82160a858337" />

## Wordpress Installation Page

<img width="1920" height="1080" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/7ae62005-7d3c-44bc-a73d-1243f9a55438" />
<img width="1920" height="1080" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/15f5375e-5fdb-48ac-8ece-958a34edd502" />
<img width="1920" height="1080" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/7e14014a-955a-493c-8c86-44cf48f4bf81" />
<img width="1920" height="1080" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/03e5095d-0401-4034-8a71-d32fcaacc470" />

## Add Plugin: Redis

<img width="1920" height="1080" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/c9eff836-d85a-4b8b-8292-5260eada1854" />
<img width="1920" height="1080" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/6619dae2-e244-4fbb-a8a2-33e30fc69c0d" />
<img width="1920" height="1080" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/0704c6a0-fa45-4d46-990b-5960f8d28417" />

## Wordpress Dashboard

<img width="1920" height="1080" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/5082bbb8-bece-42c7-a82f-d95ba6419f05" />

## Menampilkan Container yang Running

<img width="1920" height="1080" alt="Screenshot (21)" src="https://github.com/user-attachments/assets/9c140d5d-90f0-4ff9-a34f-2eccd3056290" />
<img width="1920" height="1080" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/b670b2f0-4808-4d6e-a5a2-42d0a1ffef18" />

## Redis CLI Ping Test

<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/85cdeaa7-fa4c-45b3-9226-14bbed3a1a4c" />

## Add Post Test

<img width="1920" height="1080" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/788bfb79-4ed5-4e23-b6dc-4c3277f3fb6f" />
<img width="1920" height="1080" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/c90e696a-9c74-4098-9ba1-ff0e64226445" />

## Docker Compose Restart
<img width="1920" height="1080" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/0d8a7d7e-142e-4e39-bef9-7e8c77e5e35f" />
<img width="1920" height="1080" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/0bd07042-158a-4f39-a047-8a5150d4d884" />

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
