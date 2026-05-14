# Chirath's Homelab

Documentazione del mio homelab personale: architettura, incidenti risolti, e runbook operativi.

## Scopo

Il homelab nasce con più obiettivi:

- **Media server** — streaming locale di film, serie e musica senza dipendere da abbonamenti
- **Privacy** — dati personali (foto, file, contatti) su infrastruttura propria con Nextcloud
- **Apprendimento** — laboratorio pratico per studiare Docker, networking, Linux, DNS, VPN, reverse proxy
- **Portfolio** — dimostrazione concreta di competenze sistemistiche per stage e lavoro
- **Automazione** — workflow con n8n, playlist AI con AudioMuse, download automatici con Sonarr/Radarr

## Hardware

| Device | Ruolo |
|---|---|
| **Ninkear M6** (Ryzen 5 6600H, Ubuntu 24.04) | Server principale |
| **Acer Nitro 5** (Ryzen 9 6900HX, RTX 3070 Ti) | Workstation principale / dev |

## Stack principale

- **Reverse proxy**: Caddy
- **DNS interno**: AdGuard Home (dominio `.home`)
- **VPN**: WireGuard via wg-easy
- **Orchestrazione**: Docker Compose
- **Dashboard**: Homepage
- **Monitoring**: Uptime Kuma

## Navigazione

- [Architettura](architecture/overview.md) — schema completo dell'infrastruttura
- [Incidenti](incidents/backlog.md) — problemi reali risolti, con root cause e lesson learned
- [Runbook](runbooks/index.md) — guide operative per task comuni
