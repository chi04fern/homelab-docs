# Chirath's Homelab

Documentation of my personal homelab: architecture, resolved incidents, and operational runbooks.

## Purpose

The homelab was built with multiple goals in mind:

- **Media server** — local streaming of movies, series, and music without relying on subscriptions
- **Privacy** — personal data (photos, files, contacts) on self-hosted infrastructure with Nextcloud
- **Learning** — hands-on lab for studying Docker, networking, Linux, DNS, VPN, and reverse proxies
- **Portfolio** — concrete demonstration of sysadmin skills for internships and jobs
- **Automation** — workflows with n8n, AI playlists with AudioMuse, automatic downloads with Sonarr/Radarr

## Hardware

| Device | Role |
|---|---|
| **Ninkear M6** (Ryzen 5 6600H, Ubuntu 24.04) | Main server |
| **Acer Nitro 5** (Ryzen 9 6900HX, RTX 3070 Ti) | Main workstation / dev |

## Core Stack

- **Reverse proxy**: Caddy
- **Internal DNS**: AdGuard Home (`.home` domain)
- **VPN**: WireGuard via wg-easy
- **Orchestration**: Docker Compose
- **Dashboard**: Homepage
- **Monitoring**: Uptime Kuma

## Navigation

- [Architecture](architecture/overview.md) — full infrastructure diagram
- [Incidents](incidents/backlog.md) — real problems solved, with root cause and lessons learned
- [Runbooks](runbooks/index.md) — operational guides for common tasks
