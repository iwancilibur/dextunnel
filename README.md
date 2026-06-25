# DexTunnel — CloudTunnel Manager

<img width="1774" height="887" alt="Image" src="https://github.com/user-attachments/assets/492edf8b-23be-40ab-b30d-a374c32efa66" />
**Enterprise-grade desktop application for managing Cloudflare Tunnels, DNS, Reverse Proxy, Server Monitoring, and Local Application Deployment — all without command line.**

[![Python 3.12+](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://python.org)
[![PySide6](https://img.shields.io/badge/UI-PySide6%20Qt6-green.svg)](https://doc.qt.io/qtforpython/)
[![FastAPI](https://img.shields.io/badge/API-FastAPI-009688.svg)](https://fastapi.tiangolo.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010/11-lightgrey.svg)](https://www.microsoft.com/windows/)

---

## Fitur Utama

| Fitur | Deskripsi |
|-------|-----------|
| 🚀 Quick Tunnel | Expose local services secara instan (seperti Ngrok) |
| 🌐 Domain Manager | Lihat dan kelola semua Cloudflare zones |
| 🔤 DNS Manager | Full CRUD untuk DNS records (A, AAAA, CNAME, TXT, MX, SRV) |
| 🔗 Tunnel Manager | Buat, start, stop, restart Cloudflare tunnels |
| 🐳 Docker Manager | Kelola container dan expose ke internet |
| 📊 Real-time Monitoring | Chart CPU, RAM, Disk, Network (refresh 2 detik) |
| 🤖 AI Assistant | Perintah natural language via Google Gemini |
| 🔒 SSL Manager | Konfigurasi SSL/TLS mode per domain |
| 🛡️ Firewall Manager | Kelola Cloudflare firewall rules |
| 📋 Logs Center | Log viewer terpadu dengan filtering |
| 🔔 Notifications | Alert via Telegram, Discord, WhatsApp |
| 👥 User Management | RBAC dengan role Admin/Operator/Viewer |
| 💾 Backup & Restore | Backup dan restore dengan sekali klik |
| 🖥️ Multi Server Agent | Kelola beberapa server dari satu UI |
| 🔍 Service Discovery | Auto-detect service yang berjalan di localhost |
| 📁 One-Click Deployment | Deploy project HTML/PHP/FastAPI/Flask/Django/Node.js |
| 💻 Remote Terminal | SSH, PowerShell, CMD access |
| 🛒 App Market | One-click deploy Grafana, HomeAssistant, n8n, dll |

---

## Target Users

- **Developers** — Expose local dev servers secara instan
- **System Administrators** — Kelola konfigurasi Cloudflare secara visual
- **DevOps Engineers** — Monitor dan kelola infrastruktur
- **Schools & Universities** — Share proyek lokal ke luar
- **SMBs** — Self-host service tanpa networking kompleks
- **Home Server Users** — Kelola infrastruktur personal
- **Self-Hosting Enthusiasts** — Full control atas stack mereka

---

## Spesifikasi Sistem

| Komponen | Minimum | Recommended |
|----------|---------|-------------|
| **OS** | Windows 10 (64-bit) | Windows 11 |
| **RAM** | 4 GB | 8 GB |
| **Storage** | 200 MB | 500 MB |
| **Internet** | Diperlukan | Stable connection |
| **Python** | 3.12+ | 3.14+ (untuk development) |

---

# Panduan Instalasi

## Metode 1: Instalasi via Inno Setup Installer (Recommended)

### Langkah 1: Download Installer

Download file `DexTunnel-Setup-1.0.0.exe` dari distributor resmi atau build sendiri.

### Langkah 2: Jalankan Installer

1. **Klik kanan** pada `DexTunnel-Setup-1.0.0.exe` → **Run as Administrator**
2. Jika muncul UAC (User Account Control), klik **Yes**
3. Wizard instalasi akan terbuka

### Langkah 3: Ikuti Wizard Instalasi

1. **Welcome Screen** → Klik **Next**
2. **License Agreement** → Pilih "I accept the agreement" → Klik **Next**
3. **Select Destination Location**
   - Default: `C:\Program Files\DexTunnel`
   - Atau pilih lokasi lain → Klik **Next**
4. **Select Additional Tasks**
   - ☑ Create a desktop shortcut (opsional)
   - ☑ Run DexTunnel on startup (opsional)
   - Klik **Next**
5. **Ready to Install** → Klik **Install**
6. **Completing the DexTunnel Setup Wizard**
   - ☑ Run DexTunnel now (opsional)
   - Klik **Finish**

### Langkah 4: Jalankan DexTunnel

- **Dari Desktop**: Klik shortcut "DexTunnel"
- **Dari Start Menu**: Cari "DexTunnel" di Start Menu
- **Otomatis**: Jika centang "Run on startup", aplikasi otomatis jalan saat Windows menyala

### Default Login

| Field | Value |
|-------|-------|
| **Username** | `admin` |
| **Password** | `admin123` |

> ⚠️ **Penting**: Segera ganti password default setelah login pertama kali via menu **User Management**.

---

## Metode 2: Instalasi Manual (Development)

### Langkah 1: Persiapan

Pastikan terinstall:
- **Python 3.12+** → Download dari [python.org](https://python.org)
- **Git** (opsional) → Download dari [git-scm.com](https://git-scm.com)

### Langkah 2: Clone atau Extract Project

```bash
# Via Git
git clone https://github.com/iwancilibur/dextunnel.git
cd dextunnel

# Atau extract manual
cd D:\YourPath\dex_tunnel
```

### Langkah 3: Buat Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate
```

### Langkah 4: Install Dependencies

```bash
pip install -r requirements.txt
```

### Langkah 5: Jalankan Aplikasi

```bash
python main.py
```

---

## Konfigurasi Cloudflare API

### Langkah 1: Buat API Token di Cloudflare

1. Buka **[dash.cloudflare.com](https://dash.cloudflare.com)**
2. Login ke akun Cloudflare Anda
3. Klik **ikon profil** (pojok kanan atas) → **My Profile**
4. Pilih tab **API Tokens**
5. Klik tombol **Create Token**

### Langkah 2: Pilih Custom Token

- Scroll ke bawah, cari baris **Custom token**
- Klik **"Get started"** di sebelah kanan

> ❌ **Jangan** gunakan template "Edit zone DNS" secara langsung — template itu tidak menyertakan semua permission yang diperlukan DexTunnel.

### Langkah 3: Isi Token Name

```
Token name: DexTunnel
```

### Langkah 4: Tambahkan Permissions (WAJIB SEMUA)

Klik **"Add more"** berulang hingga semua baris berikut terisi:

| Category | Subcategory | Permission |
|----------|-------------|------------|
| **Zone** | Zone | **Read** |
| **Zone** | DNS | **Edit** |
| **Zone** | SSL and Certificates | **Edit** |
| **Zone** | Firewall Services | **Edit** |
| **Account** | Cloudflare Tunnel | **Edit** |
| **Account** | Account Settings | **Read** |

### Langkah 5: Zone Resources (PALING SERING SALAH)

Di bagian **Zone Resources**:

| Field | Nilai Yang Benar |
|-------|-----------------|
| Include | **All zones** ✅ |

> ❌ **Jangan** pilih `Specific zone` kecuali Anda hanya ingin satu domain saja.
> ✅ Pilih **All zones** agar semua domain Cloudflare Anda muncul di DexTunnel.

### Langkah 6: Account Resources

Di bagian **Account Resources**:

| Field | Nilai Yang Benar |
|-------|-----------------|
| Include | **All accounts** ✅ |

### Langkah 7: Client IP Address Filtering (Opsional)

- Biarkan kosong untuk akses dari IP manapun
- Atau isi dengan IP server/komputer Anda untuk keamanan ekstra

### Langkah 8: TTL (Token Expiry)

- **Recommended:** Set expiry 1 tahun atau **No expiry** untuk penggunaan jangka panjang
- Token yang expired akan menyebabkan error `Invalid API Token`

### Langkah 9: Buat dan Copy Token

1. Klik **Continue to summary**
2. Review semua permission
3. Klik **Create Token**
4. **COPY TOKEN SEKARANG** — token hanya ditampilkan sekali!
5. Simpan di tempat aman

### Langkah 10: Masukkan Token ke DexTunnel

1. Buka DexTunnel → **Settings** → tab **Cloudflare**
2. Isi **Email**: email akun Cloudflare Anda
3. Isi **API Token**: paste token yang baru dibuat
4. Isi **Account ID**: (lihat cara mendapatkan di bawah)
5. Klik **✓ Verify & Save**

### Cara Mendapatkan Account ID

1. Buka **[dash.cloudflare.com](https://dash.cloudflare.com)**
2. Klik salah satu domain Anda
3. Scroll ke bawah di sidebar kanan → lihat bagian **Account ID**
4. Copy dan paste ke kolom Account ID di DexTunnel

### Troubleshooting Token

| Error | Penyebab | Solusi |
|-------|----------|--------|
| `Invalid API Token` (code 1000) | Token salah / expired | Buat token baru |
| `0 zones found` | Zone Resources = Specific zone | Edit token → ubah ke **All zones** |
| `Unauthorized` (code 9109) | Permission kurang | Tambah permission yang kurang |
| `No accounts found` | Account Resources salah | Ubah ke **All accounts** |
| Token valid tapi tunnel gagal | Permission Tunnel kurang | Tambah: Account → Cloudflare Tunnel → Edit |

### Contoh Token yang Sudah Benar

```
Token Name     : DexTunnel
Permissions    :
  Zone - Zone                   - Read
  Zone - DNS                    - Edit
  Zone - SSL and Certificates   - Edit
  Zone - Firewall Services      - Edit
  Account - Cloudflare Tunnel   - Edit
  Account - Account Settings    - Read
Zone Resources : All zones
Account Res.   : All accounts
TTL            : No expiry (atau 1 tahun)
```

---

## Konfigurasi Cloudflared Binary

Cloudflared adalah binary resmi dari Cloudflare untuk menjalankan tunnel. DexTunnel akan mendownload otomatis dari GitHub Releases.

### Auto-Download (Recommended)

1. Buka DexTunnel → **Settings** → tab **Cloudflare**
2. Di bagian **Cloudflared Binary**, klik **Download cloudflared**
3. Tunggu proses download selesai
4. Status akan berubah menjadi "✅ Installed"

### Manual Download

1. Download dari: https://github.com/cloudflare/cloudflared/releases/latest
2. Pilih file: `cloudflared-windows-amd64.exe`
3. Rename menjadi `cloudflared.exe`
4. Simpan di folder `bin/` dalam direktori aplikasi

### Install sebagai Windows Service (Opsional)

1. Buka DexTunnel → **Settings** → tab **Cloudflare**
2. Klik **Install as Service**
3. Service akan otomatis berjalan saat Windows startup

---

## Konfigurasi AI Assistant (Opsional)

DexTunnel terintegrasi dengan Google Gemini AI untuk mengelola tunnel menggunakan perintah natural language.

### Langkah 1: Dapatkan API Key

1. Buka **[aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)**
2. Login dengan akun Google
3. Klik **Create API Key**
4. Copy API Key yang dibuat

### Langkah 2: Konfigurasi di DexTunnel

1. Buka DexTunnel → **Settings** → tab **AI**
2. Isi **API Key**: paste API Key yang didapat
3. Pilih **Model**: `gemini-2.5-flash` (recommended) atau `gemini-2.5-pro`
4. Centang **Enable AI Assistant**
5. Klik **Save AI Config**

### Contoh Perintah AI

- "Buat tunnel untuk port 3000 di domain app.example.com"
- "List semua tunnel yang aktif"
- "Stop tunnel bernama myapp"
- "Buat DNS record CNAME untuk blog.example.com"

---

## Konfigurasi Notifikasi (Opsional)

### Telegram

1. Chat dengan **@BotFather** di Telegram
2. Ketik `/newbot` → ikuti instruksi → copy **Bot Token**
3. Chat dengan bot Anda, lalu dapatkan **Chat ID** via @userinfobot
4. Buka DexTunnel → **Settings** → tab **Notifications** → tab **Telegram**
5. Isi **Bot Token** dan **Chat ID**
6. Centang **Enable Telegram Notifications**
7. Klik **Test Telegram** untuk memverifikasi
8. Klik **Save All Notifications**

### Discord

1. Buka Server Settings → Integrations → Webhooks
2. Klik **New Webhook** → copy **Webhook URL**
3. Buka DexTunnel → **Notifications** → tab **Discord**
4. Isi **Webhook URL**
5. Centang **Enable Discord Notifications**
6. Klik **Test Discord**
7. Klik **Save All Notifications**

### WhatsApp (Fonnte)

1. Daftar di [fonnte.com](https://fonnte.com)
2. Dapatkan **API Token**
3. Buka DexTunnel → **Notifications** → tab **WhatsApp**
4. Isi **API Token** dan **Phone Number**
5. Centang **Enable WhatsApp Notifications**
6. Klik **Test WhatsApp**
7. Klik **Save All Notifications**

---

## Fitur Lainnya

### Dashboard

- Monitor real-time CPU, RAM, Disk, Network
- Lihat ringkasan tunnel aktif/offline
- Chart dengan refresh interval 2 detik

### Tunnel Manager

- Buat tunnel baru dengan sekali klik
- Start/Stop/Restart/Delete tunnel
- Lihat status real-time dan live logs

### DNS Manager

- Tambah/Edit/Hapus DNS records
- Support A, AAAA, CNAME, TXT, MX, SRV records
- Sinkronisasi otomatis dengan Cloudflare

### Docker Manager

- Lihat semua container Docker
- Start/Stop/Restart/Delete container
- Lihat resource usage per container

### One-Click Deployment

- Auto-detect framework (HTML, PHP, FastAPI, Flask, Django, Node.js, dll)
- Start development server otomatis
- Buat tunnel + DNS record otomatis

### Remote Terminal

- Akses SSH ke server remote
- Jalankan PowerShell/CMD lokal
- SFTP file manager

### Service Discovery

- Scan port di localhost
- Auto-detect service yang berjalan
- HTTP fingerprinting

### App Market

- One-click deploy: Grafana, HomeAssistant, n8n, Prometheus, UptimeKuma, Jellyfin, WAHA
- Kelola docker-compose stacks

### Backup & Restore

- Backup database ke file ZIP
- Restore dari file backup
- Scheduled backup (opsional)

### User Management

- Tambah/Edit/Hapus user
- Role: Admin, Operator, Viewer
- Audit logging

---

## Build EXE (untuk Developer)

### PyInstaller

```bash
# Activate venv
venv\Scripts\activate

# Build
pyinstaller installer/dextunnel.spec --clean --noconfirm

# Output: dist/DexTunnel.exe
```

### Build Installer dengan Inno Setup

```bash
# Pastikan Inno Setup terinstall
# Download dari: https://jrsoftware.org/isdl.php

# Build installer
iscc installer\setup.iss

# Output: dist/DexTunnel-Setup-1.0.0.exe
```

### Build Lengkap (EXE + Installer)

```bash
# Jalankan build script
build.bat

# Output:
# - dist/DexTunnel.exe (EXE)
# - dist/DexTunnel-Setup-1.0.0.exe (Installer)
```

---

## Arsitektur Sistem

```
PySide6 (Qt6)          ← Desktop UI (Blue→Red→Orange→Purple Theme)
    ↕
FastAPI + WebSocket    ← Internal REST API (localhost:8765)
    ↕
SQLAlchemy + SQLite    ← Local database (dex_tunnel.db)
    ↕
Cloudflare API         ← Zone/DNS/Tunnel management
cloudflared.exe        ← Tunnel process manager (auto-download)
Docker SDK             ← Container management
psutil                 ← System monitoring (2s interval)
Google Gemini          ← AI assistant (tool calling)
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **UI Framework** | PySide6 (Qt6) — Native Windows |
| **Backend API** | FastAPI + uvicorn + WebSocket |
| **Database** | SQLite + SQLAlchemy ORM + Alembic |
| **Security** | AES-256-GCM + bcrypt + JWT + Windows Keyring |
| **Monitoring** | psutil + pyqtgraph realtime charts |
| **Cloudflare** | httpx async client (full API coverage) |
| **Docker** | Docker SDK Python |
| **AI** | Google Gemini 1.5 Flash + tool calling |
| **Notifications** | Telegram Bot API + Discord Webhooks |

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| cloudflared not found | Settings → Cloudflared → Download |
| Docker unavailable | Start Docker Desktop |
| CF API error 401 | Check token permissions |
| High memory usage | Normal — pyqtgraph charts use GPU |
| Tunnel gagal dibuat | Pastikan permission: Account → Cloudflare Tunnel → Edit |
| Zone / DNS tidak muncul | Pastikan: Zone → Zone → Read dan Zone Resources → All zones |
| Event loop error | Sudah diperbaiki di v1.1.0 dengan persistent async event loop |

---

## File Structure

```
DexTunnel/
├── DexTunnel.exe              # Aplikasi utama
├── Logo.png                   # Logo aplikasi
├── avatar.png                 # Default avatar
├── resources/                 # Icons dan resource
│   └── icons/
│       ├── app.ico
│       └── app.png
├── bin/                       # Cloudflared binary (auto-download)
│   └── cloudflared.exe
├── tunnel_configs/            # Config tunnel (otomatis)
├── logs/                      # Log files
├── backups/                   # Backup files
└── dex_tunnel.db              # Database SQLite
```

---

## Lingkungan

### Variabel Environment (Opsional)

Buat file `.env` di direktori aplikasi:

```env
# Override Windows Keyring master key
DEXTUNNEL_MASTER_KEY=

# Custom JWT secret
DEXTUNNEL_JWT_SECRET=

# Backend bind address
DEXTUNNEL_API_HOST=127.0.0.1
DEXTUNNEL_API_PORT=8765

# Log level (DEBUG/INFO/WARNING/ERROR)
LOG_LEVEL=INFO
```

---

## Lokasi Data Aplikasi

| Data | Lokasi |
|------|--------|
| **Database** | `%APPDATA%\DexTunnel\dex_tunnel.db` |
| **Logs** | `%APPDATA%\DexTunnel\logs\` |
| **Tunnel Configs** | `%APPDATA%\DexTunnel\tunnel_configs\` |
| **Backups** | `%APPDATA%\DexTunnel\backups\` |
| **Cloudflared Binary** | `[Install Dir]\bin\cloudflared.exe` |

---

## Lisensi

MIT License - Gratis untuk penggunaan personal dan komersial.

---

## Informasi Pembuat

### Iwan Cilibur

**Full-Stack Developer & Self-Hoster**

DexTunnel dibuat oleh Iwan Cilibur, seorang developer yang passionate tentang self-hosting dan infrastruktur Cloudflare.

### Social Media & Kontak

| Platform | Link |
|----------|------|
| 🌐 Website | [iwancilibur.my.id](https://iwancilibur.my.id) |
| 📘 Facebook | [facebook.com/iwan.cilibur](https://facebook.com/iwan.cilibur) |
| 💼 LinkedIn | [linkedin.com/in/iwan-cilibur](https://linkedin.com/in/iwan-cilibur) |
| 📺 YouTube | [youtube.com/@iwancilibur](https://youtube.com/@iwancilibur) |
| ⭐ GitHub | [github.com/iwancilibur/dextunnel](https://github.com/iwancilibur/dextunnel) |

---

## Traktir Kopi

Jika DexTunnel membantu pekerjaanmu, pertimbangkan untuk support pengembangannya!

### ☕ Trakteer.id

**[trakteer.id/iwancilibur/tip](https://trakteer.id/iwancilibur/tip)**

Belikan developer secangkir kopi sebagai apresiasi atas kerja kerasnya.

### 💳 PayPal

**[paypal.me/iwancilibur](https://paypal.me/iwancilibur)**

Donasi via PayPal untuk support proyek ini.

### ⭐ GitHub Star

Beri bintang di GitHub untuk menunjukkan apresiasi:

**[github.com/iwancilibur/dextunnel](https://github.com/iwancilibur/dextunnel)**

### 📢 Share

Bagikan DexTunnel kepada teman-teman yang membutuhkan:

**[iwancilibur.my.id](https://iwancilibur.my.id)**

---

## Credits

Made with ❤️ for developers, sysadmins, and self-hosting enthusiasts.

**DexTunnel v1.0.0** — © 2026 Iwan Cilibur

---

<div align="center">

**[Documentation](docs/) · [Report Bug](https://github.com/iwancilibur/dextunnel/issues) · [Request Feature](https://github.com/iwancilibur/dextunnel/issues)**

</div>
