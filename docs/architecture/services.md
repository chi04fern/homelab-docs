# Servizi

Tutti i servizi girano come container Docker sul Ninkear M6.

## Media

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `jellyfin` | `jellyfin/jellyfin` | 8096 | Media server (film, serie, video) |
| `sonarr` | `linuxserver/sonarr` | 8989 | Gestione automatica serie TV |
| `radarr` | `linuxserver/radarr` | 7878 | Gestione automatica film |
| `prowlarr` | `linuxserver/prowlarr` | 9696 | Aggregatore indexer |
| `bazarr` | `linuxserver/bazarr` | 6767 | Gestione sottotitoli |
| `qbittorrent` | `linuxserver/qbittorrent` | 8081 (UI) / 6881 (P2P) | Client torrent |
| `jellyseerr` | `fallenbagel/jellyseerr` | 5055 | Richieste media |
| `flaresolverr` | `flaresolverr/flaresolverr` | 8191 | Bypass Cloudflare per indexer |

## Musica

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `navidrome` | `deluan/navidrome:0.61.0` | 4533 | Streaming musicale (API Subsonic) |
| `tidaloader` | `ghcr.io/rayz3r0/tidaloader` | 8001 (interno) | Download da Tidal |
| `audiomuse-ai` | `ghcr.io/neptunehub/audiomuse-ai` | 8000 | Playlist AI con Gemini |
| `octo-fiesta` | `ghcr.io/v1ck3s/octo-fiesta` | 5274 | Proxy Subsonic on-demand |
| `music-grabber` | `g33kphr33k/musicgrabber` | interno | — |
| `beets` | `linuxserver/beets` | interno | Organizzazione libreria musicale |
| `slskd` | `slskd/slskd` | 5030-5031 / 50300 | Client Soulseek |

## Cloud personale

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `nextcloud` | `nextcloud:apache` | interno (via Caddy) | Cloud personale |
| `nextcloud-db` | `mariadb:11` | interno | Database Nextcloud |

## AI / Automazione

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `open-webui` | `ghcr.io/open-webui/open-webui` | 3010 | UI per LLM locali/remoti |
| `n8n` | `docker.n8n.io/n8nio/n8n` | 5678 | Automazione workflow |
| `audiomuse-postgres` | `postgres:16` | interno | DB per AudioMuse |
| `audiomuse-redis` | `redis:7` | interno | Cache per AudioMuse |

## Networking

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `caddy` | `caddy:latest` | 80 / 443 | Reverse proxy + TLS automatico |
| `adguardhome` | `adguard/adguardhome` | 53 / 8082 (UI) | DNS con ad-blocking |
| `wg-easy` | `weejewel/wg-easy` | — | WireGuard VPN con UI web |

!!! warning "wg-easy immagine deprecata"
    L'immagine `weejewel/wg-easy` non è più mantenuta. Migrare a `ghcr.io/wg-easy/wg-easy`.

## Management

| Container | Immagine | Host Port | Descrizione |
|---|---|---|---|
| `homepage` | `gethomepage/homepage:v1.9.0` | 3000 | Dashboard servizi |
| `uptime-kuma` | `louislam/uptime-kuma:2.0.2` | 3001 | Monitoring uptime |
| `portainer` | `portainer/portainer-ce:2.38.0` | 9000 (localhost only) | Gestione container |

## Altro

| Container | Immagine | Descrizione |
|---|---|---|
| `bononi-wiki` | `nginx:alpine` | Sito del corso di networking/cloud (`reti.chya43.it`) |
