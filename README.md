# RestoApp

Sistem manajemen restoran lengkap yang terdiri dari **aplikasi mobile** untuk customer dan **Web API** sebagai backend. Projek ini menggunakan **Git Submodule** untuk menghubungkan kedua repository.

## Struktur Projek

```
RestoApp/
├── mobile/    → Aplikasi Android (Kotlin + Jetpack Compose)
├── web-api/   → REST API Backend (.NET 8 + SQL Server)
└── README.md
```

| Komponen | Tech Stack                                | Repository                                                  |
| -------- | ----------------------------------------- | ----------------------------------------------------------- |
| Mobile   | Kotlin, Jetpack Compose, Material 3       | [resto-mobile](https://github.com/M1kha-san/resto-mobile)   |
| Web API  | .NET 8, Entity Framework Core, SQL Server | [resto-backend](https://github.com/M1kha-san/resto-backend) |

## Fitur

- **Pemesanan** — Dine-In & Take-Away
- **Manajemen Menu** — CRUD menu dan kategori
- **Manajemen Meja** — Pengaturan meja restoran
- **Manajemen Pegawai & User** — Role-based access
- **Laporan Transaksi** — History harian & per rentang tanggal
- **Multi-platform** — Mobile (Customer) & Desktop (Kasir, Manajer, Owner)

## Prasyarat

| Tool           | Versi Minimum |
| -------------- | ------------- |
| Git            | 2.x           |
| Android Studio | Hedgehog+     |
| JDK            | 11            |
| .NET SDK       | 8.0           |
| SQL Server     | 2019+         |

## Instalasi

### 1. Clone Repository (beserta Submodule)

```bash
git clone --recurse-submodules https://github.com/M1kha-san/RestoApp.git
cd RestoApp
```

> Jika sudah clone tanpa `--recurse-submodules`, jalankan:
>
> ```bash
> git submodule update --init --recursive
> ```

### 2. Setup Web API (Backend)

```bash
cd web-api/RestoAPI
```

1. **Konfigurasi database** — Edit `appsettings.json`, sesuaikan connection string:

   ```json
   {
     "ConnectionStrings": {
       "DefaultConnection": "Server=YOUR_SERVER;Database=resto_db;Trusted_Connection=True;TrustServerCertificate=True"
     }
   }
   ```

2. **Jalankan migration** untuk membuat tabel di database:

   ```bash
   dotnet ef database update
   ```

3. **Jalankan API**:

   ```bash
   dotnet run
   ```

4. **Verifikasi** — Buka Swagger UI di `https://localhost:7154/swagger` untuk memastikan API berjalan.

### 3. Setup Mobile App

1. Buka folder `mobile/` menggunakan **Android Studio**.
2. Tunggu Gradle sync selesai.
3. Pastikan base URL API di kode sudah mengarah ke alamat backend (misalnya `http://10.0.2.2:7154` untuk emulator atau IP lokal untuk device fisik).
4. Run aplikasi ke emulator atau device fisik (min SDK 27 / Android 8.1).

## Menjalankan Projek

1. **Jalankan Web API terlebih dahulu** agar endpoint tersedia.
2. **Jalankan Mobile App** dari Android Studio.
3. Aplikasi mobile akan berkomunikasi dengan backend melalui REST API.

## Update Submodule

Untuk menarik perubahan terbaru dari masing-masing sub-repository:

```bash
git submodule update --remote --merge
```

## Lisensi

Lihat file [LICENSE](LICENSE) untuk detail.
