# 🏠 Homelab Docs

Personal homelab documentation — architecture, incident reports, and operational runbooks.

Built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and self-hosted on a Ninkear M6 mini PC.

🌐 **Live site**: [docs.chya43.it](https://docs.chya43.it)

## 📖 Contents

- **Architecture** — hardware specs, full service list, networking setup (Caddy, AdGuard, WireGuard)
- **Incidents** — real problems I've debugged and solved, with root cause and lessons learned
- **Runbooks** — operational guides for common tasks

## 🛠️ Stack

| Layer | Tool |
|---|---|
| OS | Ubuntu 24.04 |
| Containers | Docker Compose |
| Reverse Proxy | Caddy |
| DNS | AdGuard Home |
| VPN | WireGuard (wg-easy) |
| Docs | MkDocs Material |

## 🚀 Run locally

```bash
git clone https://github.com/chi04fern/homelab-docs
cd homelab-docs
docker compose up
```

Then open [http://localhost:8000](http://localhost:8000)

## 📁 Structure

```
docs/
├── index.md
├── architecture/
│   ├── overview.md
│   ├── hardware.md
│   ├── services.md
│   └── networking.md
├── incidents/
│   └── backlog.md
└── runbooks/
    └── index.md
```

---

*Part of my learning journey through a one-year networking & cloud computing course in Bologna.*
