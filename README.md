# n8n Docker Setup with PostgreSQL

Repository ini berisi konfigurasi Docker Compose untuk menjalankan n8n dengan database PostgreSQL.

## Persiapan

1. Salin file `.env.example` menjadi `.env`:
   ```bash
   cp .env.example .env
   ```
2. Pastikan Anda mengisi nilai-nilai di dalam `.env`, terutama kunci enkripsi.

## Konfigurasi .env

| Variabel | Deskripsi |
| :--- | :--- |
| `POSTGRES_USER` | Username admin untuk PostgreSQL. |
| `POSTGRES_PASSWORD` | Password admin untuk PostgreSQL. |
| `POSTGRES_DB` | Nama database yang akan dibuat. |
| `POSTGRES_NON_ROOT_USER` | Username yang digunakan n8n untuk akses database (disarankan sama dengan admin atau user terbatas). |
| `POSTGRES_NON_ROOT_PASSWORD` | Password untuk user non-root. |
| `N8N_ENCRYPTION_KEY` | Kunci unik untuk mengenkripsi kredensial di n8n. **Jangan sampai hilang!** |
| `N8N_USER_MANAGEMENT_JWT_SECRET` | Secret key untuk autentikasi user management n8n. |

### Menghasilkan Kunci Keamanan
Anda bisa menghasilkan string acak untuk kunci di atas menggunakan perintah:
```bash
openssl rand -hex 24
```

## Menjalankan n8n

Untuk menjalankan container di background:
```bash
docker-compose up -d
```

Akses n8n di: `http://localhost:5678`

## Perintah Berguna

- **Melihat log:** `docker-compose logs -f n8n`
- **Menghentikan:** `docker-compose down`
- **Update n8n:** `docker-compose pull && docker-compose up -d`
