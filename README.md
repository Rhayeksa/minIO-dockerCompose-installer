# 🚀 MinIO Server dengan Docker Compose

Repositori ini menyediakan konfigurasi `docker-compose.yml` sederhana untuk menjalankan **MinIO**, sistem penyimpanan objek open-source berperforma tinggi yang kompatibel dengan **Amazon S3 API**.

## 📦 Layanan

- **MinIO Server**
  - Menyediakan API kompatibel S3 di port `9000`
  - Menyediakan Console UI di port `9001`
  - Data disimpan di dalam volume Docker (atau path host)

---

## 🛠 Kebutuhan

- [Docker](https://docs.docker.com/get-docker/) (>= 20.x)
- [Docker Compose](https://docs.docker.com/compose/install/) (>= v2.x)

---

## ⚙️ Konfigurasi

Variabel lingkungan dapat disesuaikan menggunakan file `.env` atau langsung melalui shell.

| Variabel               | Nilai Default   | Deskripsi                              |
| ---------------------- | --------------- | -------------------------------------- |
| `MINIO_IMAGE_VERSION`  | `latest`        | Versi image MinIO                      |
| `MINIO_CONTAINER_NAME` | `minio_server`  | Nama container Docker                  |
| `MINIO_API_PORT`       | `9000`          | Port untuk API kompatibel S3           |
| `MINIO_CONSOLE_PORT`   | `9001`          | Port untuk Console UI berbasis web     |
| `MINIO_ROOT_USER`      | `minioadmin`    | Username root MinIO                    |
| `MINIO_ROOT_PASSWORD`  | `minioadmin123` | Password root MinIO (ubah di produksi) |
| `MINIO_DATA_PATH`      | `./.minio`      | Lokasi penyimpanan data di host        |

Contoh file `.env`:

```env
MINIO_IMAGE_VERSION=latest
MINIO_CONTAINER_NAME=minio_server
MINIO_API_PORT=9000
MINIO_CONSOLE_PORT=9001
MINIO_ROOT_USER=admin
MINIO_ROOT_PASSWORD=supersecret123
MINIO_DATA_PATH=./
```

---

## ▶️ Cara Menjalankan

1. Clone repositori ini atau salin file `docker-compose.yml`.
2. Buat file `.env` (opsional, untuk konfigurasi kustom).
3. Jalankan MinIO dengan perintah:

```bash
docker-compose up -d
```

4. Hentikan MinIO:

```bash
docker-compose down
```

---

## 🌐 Akses MinIO

- **API (Kompatibel S3):**  
  `http://localhost:9000`

- **Console UI:**  
  `http://localhost:9001`

Masuk menggunakan kredensial yang telah dikonfigurasi (`MINIO_ROOT_USER` / `MINIO_ROOT_PASSWORD`).

## 🛡 Catatan Keamanan

- Selalu **ubah kredensial default** (`minioadmin / minioadmin123`) sebelum digunakan di produksi.
- Gunakan password yang kuat dan kelola secret melalui environment variables.
- Untuk produksi, sebaiknya aktifkan **HTTPS** menggunakan reverse proxy (misalnya Traefik atau Nginx).

---

## 📚 Referensi

- [Dokumentasi Resmi MinIO](https://min.io/docs/minio/linux/index.html)
- [Docker Hub: MinIO](https://hub.docker.com/r/minio/minio)
