# 🌐 DexTunnel — CloudTunnel Manager

<div align="center">

<img width="1254" height="1254" alt="Image" src="https://github.com/user-attachments/assets/4d1ac9ab-8094-434c-854f-984b7d08dd36" />

**Enterprise-grade desktop application for managing Cloudflare Tunnels, DNS, Reverse Proxy, Server Monitoring, and Local Application Deployment — all without command line.**

[![Go Version](https://img.shields.io/badge/Go-1.22-blue)](https://go.dev)
[![Flutter Version](https://img.shields.io/badge/Flutter-3.22-blue)](https://flutter.dev)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows-blue)](https://microsoft.com/windows)

</div>

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🚀 **Quick Tunnel** | Expose local services instantly (like Ngrok) |
| 🌐 **Domain Manager** | View and manage Cloudflare zones |
| 🔤 **DNS Manager** | Full CRUD for DNS records (A, AAAA, CNAME, TXT, MX, SRV) |
| 🔗 **Tunnel Manager** | Create, start, stop, restart Cloudflare tunnels |
| 🐳 **Docker Manager** | Manage containers and expose them to internet |
| 📊 **Real-time Monitoring** | CPU, RAM, Disk, Network charts (2s refresh) |
| 🤖 **AI Assistant** | Natural language commands via Google Gemini |
| 🔒 **SSL Manager** | Configure SSL/TLS mode per domain |
| 🛡️ **Firewall Manager** | Cloudflare firewall rules management |
| 📋 **Logs Center** | Unified log viewer with filtering |
| 🔔 **Notifications** | Telegram, Discord, Email alerts |
| 👥 **User Management** | RBAC with Admin/Operator/Viewer roles |
| 💾 **Backup & Restore** | One-click backup and restore |
| 🖥️ **Multi Server Agent** | Manage multiple servers from one UI |

---

## 🎯 Target Users

- **Developers** — Expose local dev servers instantly
- **System Administrators** — Manage Cloudflare configurations visually
- **DevOps Engineers** — Monitor and manage infrastructure
- **Schools & Universities** — Share local projects externally
- **SMBs** — Self-host services without complex networking
- **Home Server Users** — Manage personal infrastructure
- **Self-Hosting Enthusiasts** — Full control over their stack

---

## 🛠️ Tech Stack

### Frontend
```
Flutter Desktop (Windows)  →  Material Design 3
Riverpod                   →  State Management
Go Router                  →  Navigation
fl_chart                   →  Real-time Charts
```

### Backend
```
Golang + Gin               →  REST API & WebSocket
SQLite (go-sqlite3)        →  Local Database
AES-256-GCM               →  Encryption
JWT HS256                  →  Authentication
gopsutil                   →  System Metrics
```

### Integrations
```
Cloudflare API             →  DNS, SSL, Firewall management
cloudflared CLI            →  Tunnel process management
Docker API                 →  Container management
Google Gemini              →  AI Assistant
Prometheus Metrics         →  Grafana compatible
```

---

## 🚀 Quick Start

### Prerequisites
- Windows 10/11 (64-bit)
- [Go 1.22+](https://go.dev/dl/)
- [Flutter 3.22+](https://flutter.dev)
- GCC for SQLite (`winlibs` or `tdm-gcc`)

### Build & Run

```cmd
# Clone
git clone https://github.com/dextunnel/dextunnel.git
cd dextunnel

# Build everything
make build

# Or run in development
make dev
```

### Using Makefile

```cmd
make build        # Build backend + frontend
make run-backend  # Run backend only
make test         # Run all tests
make clean        # Clean build artifacts
make release      # Build release package
```

---

## 📁 Project Structure

```
DexTunnel/
├── backend/                    # Golang backend
│   ├── cmd/server/main.go      # Entry point
│   ├── internal/
│   │   ├── domain/             # Business logic
│   │   │   ├── entities/       # Data models
│   │   │   ├── repositories/   # Repository interfaces
│   │   │   └── usecases/       # Business rules
│   │   ├── infrastructure/     # External integrations
│   │   │   ├── database/       # SQLite + migrations
│   │   │   ├── cloudflare/     # Cloudflare API client
│   │   │   ├── cloudflared/    # cloudflared process manager
│   │   │   ├── docker/         # Docker API client
│   │   │   ├── system/         # System metrics (gopsutil)
│   │   │   ├── encryption/     # AES-256-GCM
│   │   │   └── notification/   # Telegram, Discord, Email
│   │   └── application/        # HTTP layer
│   │       ├── handlers/       # Gin route handlers
│   │       ├── middleware/      # Auth, rate limit, CORS
│   │       ├── websocket/      # WebSocket hub
│   │       └── dto/            # Request/Response DTOs
│   ├── pkg/
│   │   ├── config/             # Configuration loader
│   │   ├── logger/             # Structured logging
│   │   ├── response/           # Standard API responses
│   │   └── validator/          # Input validation
│   ├── migrations/             # SQL migrations
│   └── test/                   # Unit + integration tests
│
├── frontend/                   # Flutter frontend
│   ├── lib/
│   │   ├── main.dart           # Entry point
│   │   ├── core/
│   │   │   ├── constants/      # App constants
│   │   │   ├── theme/          # Material Design 3 theme
│   │   │   ├── router/         # Go Router config
│   │   │   ├── network/        # Dio API client
│   │   │   ├── storage/        # Secure storage
│   │   │   └── widgets/        # AppShell, sidebar
│   │   └── features/           # Feature modules
│   │       ├── auth/           # Login, credentials
│   │       ├── dashboard/      # Stats + charts
│   │       ├── domains/        # Domain manager
│   │       ├── dns/            # DNS manager
│   │       ├── tunnels/        # Tunnel manager
│   │       ├── docker/         # Docker manager
│   │       ├── monitoring/     # System monitoring
│   │       ├── logs/           # Logs center
│   │       ├── ai_assistant/   # Gemini AI chat
│   │       ├── settings/       # App settings
│   │       ├── users/          # User management
│   │       └── notifications/  # Alert config
│   └── test/                   # Widget + integration tests
│
├── docs/
│   ├── architecture/           # System architecture docs
│   ├── api/                    # API reference
│   ├── user-guide/             # End user manual
│   ├── deployment/             # Installation guide
│   └── wireframes/             # UI wireframes
│
├── installer/                  # Windows installer (NSIS/Inno Setup)
├── .github/workflows/          # CI/CD pipelines
├── Makefile                    # Build automation
└── README.md
```

---

## 🗄️ Database Schema (ERD)

```
users ──────────────────────────────────────────────────────────────
  id, username, email, password_hash, role, is_active, last_login

cloudflare_credentials ─────────────────────────────────────────────
  id, user_id → users, email, api_token (encrypted), account_id

domains ─────────────────────────────────────────────────────────────
  id, zone_id (CF), name, status, nameservers, ssl_status

dns_records ─────────────────────────────────────────────────────────
  id, zone_id → domains, record_id (CF), name, type, content, ttl, proxied

tunnels ─────────────────────────────────────────────────────────────
  id, tunnel_id (CF), name, status, domain, local_port, service_type

tunnel_ingress ──────────────────────────────────────────────────────
  id, tunnel_id → tunnels, hostname, service, path_match

metrics_history ─────────────────────────────────────────────────────
  id, cpu_percent, memory_*, disk_*, network_*, recorded_at

log_entries ─────────────────────────────────────────────────────────
  id, source, severity, message, details, created_at

notification_configs ────────────────────────────────────────────────
  id, user_id → users, channel, config (encrypted), is_active

audit_logs ──────────────────────────────────────────────────────────
  id, user_id, action, resource, resource_id, old_value, new_value

server_agents ───────────────────────────────────────────────────────
  id, name, host, port, agent_token (encrypted), status, last_metrics
```

---

## 🔐 Security

- **JWT HS256** — Token-based authentication (24h expiry)
- **AES-256-GCM** — Encrypted storage for API tokens and credentials
- **RBAC** — Role-based access control (Admin/Operator/Viewer)
- **Rate Limiting** — Token bucket per IP (100 RPS default)
- **Audit Logging** — All write operations logged with user, IP, timestamp
- **localhost-only** — Backend binds to `127.0.0.1:8717` only
- **Input Validation** — All inputs validated before processing

---

## 📡 WebSocket Events

Connect to `ws://localhost:8717/ws` for real-time updates:

| Event | Frequency | Description |
|-------|-----------|-------------|
| `metrics` | Every 2s | CPU, RAM, Disk, Network |
| `tunnel_status` | On change | Tunnel up/down |
| `log_entry` | On event | New log lines |
| `notification` | On alert | System alerts |
| `docker_status` | On change | Container state changes |

---

## 🧪 Testing

```cmd
# Backend unit tests
cd backend && go test ./... -v

# Backend with coverage
cd backend && go test ./... -coverprofile=coverage.out
go tool cover -html=coverage.out

# Flutter tests
cd frontend && flutter test

# Integration tests
cd backend && go test ./test/integration/... -v
```

---

## 📦 Building Release

```cmd
make release
```

This creates `dist/DexTunnel-<version>-Windows.zip` containing:
- `dextunnel.exe` — Flutter Windows app
- `dextunnel-backend.exe` — Go backend
- `data/` — Database directory
- Runtime DLLs

---

## 🔧 Development

### Running in Dev Mode

```cmd
# Terminal 1: Start backend
cd backend
go run ./cmd/server

# Terminal 2: Start Flutter app
cd frontend
flutter run -d windows
```

### Environment Variables

Copy `.env.example` to `.env` and configure:

```env
APP_PORT=8717
APP_ENV=development
DATABASE_PATH=./data/dextunnel.db
ENCRYPTION_KEY=change-this-32-byte-key-in-prod!
JWT_SECRET=change-this-jwt-secret-in-production
LOG_LEVEL=debug
RATE_LIMIT_RPS=100
GEMINI_API_KEY=your_google_gemini_api_key
```

---

## 📖 Documentation

| Document | Location |
|----------|----------|
| System Architecture | [docs/architecture/SYSTEM_ARCHITECTURE.md](docs/architecture/SYSTEM_ARCHITECTURE.md) |
| API Reference | [docs/api/API_REFERENCE.md](docs/api/API_REFERENCE.md) |
| User Guide | [docs/user-guide/USER_GUIDE.md](docs/user-guide/USER_GUIDE.md) |
| Installation | [docs/deployment/INSTALLATION.md](docs/deployment/INSTALLATION.md) |

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'feat: add amazing feature'`
4. Push branch: `git push origin feature/amazing-feature`
5. Open Pull Request

### Commit Convention
```
feat:     New feature
fix:      Bug fix
docs:     Documentation
style:    Code style
refactor: Code refactoring
test:     Add tests
chore:    Build/CI changes
```

---

## 📄 License

MIT License — see [LICENSE](LICENSE) file.

---

## 🙏 Acknowledgments

- [Cloudflare](https://cloudflare.com) — Tunnel and DNS services
- [gin-gonic/gin](https://github.com/gin-gonic/gin) — Go web framework
- [Flutter](https://flutter.dev) — Cross-platform UI toolkit
- [gopsutil](https://github.com/shirou/gopsutil) — System metrics
- [Google Gemini](https://ai.google.dev) — AI assistant

---

<div align="center">
Made with ❤️ for developers, sysadmins, and self-hosting enthusiasts

[iwancilibur.my.id](https://iwancilibur.my.id) | [Facebook](https://www.facebook.com/iwan.cilibur) | [LinkedIn](https://id.linkedin.com/in/iwan-cilibur-57534699)

**[Documentation](docs/) · [Report Bug](issues/) · [Request Feature](issues/)**
</div>
