# Overview

Il homelab gira interamente su un **Ninkear M6** (mini PC), con Ubuntu 24.04 e Docker Compose come orchestratore.

## Stack a colpo d'occhio

```
┌─────────────────────────────────────────────┐
│              Ninkear M6                      │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │  Media   │  │  Musica  │  │  Cloud   │  │
│  │ Jellyfin │  │Navidrome │  │Nextcloud │  │
│  │  Sonarr  │  │AudioMuse │  │          │  │
│  │  Radarr  │  │ Slskd    │  └──────────┘  │
│  └──────────┘  └──────────┘                │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │    AI    │  │ Network  │  │ Mgmt     │  │
│  │Open WebUI│  │  Caddy   │  │Homepage  │  │
│  │   n8n    │  │AdGuard   │  │Portainer │  │
│  │          │  │WireGuard │  │Uptime K. │  │
│  └──────────┘  └──────────┘  └──────────┘  │
└─────────────────────────────────────────────┘
```

## Sezioni

- [Hardware](hardware.md) — specifiche del server e della workstation
- [Servizi](services.md) — lista completa di tutti i container con porte e descrizioni
- [Networking](networking.md) — Caddy, AdGuard, WireGuard, reti Docker
