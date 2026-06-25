# DexTunnel — CloudTunnel Manager

<img width="1526" height="455" alt="Image" src="https://github.com/user-attachments/assets/080b2e37-e03c-4a51-b719-906a1f04a941" />
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

## Instalasi Setup Installer (Recommended)

### Langkah 1: Download Installer

Download file `DexTunnel-Setup-1.0.0.exe` dari distributor resmi.

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
