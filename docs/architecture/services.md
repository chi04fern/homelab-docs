# Services

All services run as Docker containers on the Ninkear M6.

## Media

| Container | Image | Host Port | Description |
|---|---|---|---|
| `jellyfin` | `jellyfin/jellyfin` | 8096 | Media server (movies, series, video) |
| `sonarr` | `linuxserver/sonarr` | 8989 | Automatic TV series management |
| `radarr` | `linuxserver/radarr` | 7878 | Automatic movie management |
| `prowlarr` | `linuxserver/prowlarr` | 9696 | Indexer aggregator |
| `bazarr` | `linuxserver/bazarr` | 6767 | Subtitle management |
| `qbittorrent` | `linuxserver/qbittorrent` | 8081 (UI) / 6881 (P2P) | Torrent client |
| `jellyseerr` | `fallenbagel/jellyseerr` | 5055 | Media requests |
| `flaresolverr` | `flaresolverr/flaresolverr` | 8191 | Cloudflare bypass for indexers |

## Music

| Container | Image | Host Port | Description |
|---|---|---|---|
| `navidrome` | `deluan/navidrome:0.61.0` | 4533 | Music streaming (Subsonic API) |
| `tidaloader` | `ghcr.io/rayz3r0/tidaloader` | 8001 (internal) | Download from Tidal |
| `audiomuse-ai` | `ghcr.io/neptunehub/audiomuse-ai` | 8000 | AI playlist generation with Gemini |
| `octo-fiesta` | `ghcr.io/v1ck3s/octo-fiesta` | 5274 | On-demand Subsonic proxy |
| `music-grabber` | `g33kphr33k/musicgrabber` | internal | — |
| `beets` | `linuxserver/beets` | internal | Music library organization |
| `slskd` | `slskd/slskd` | 5030-5031 / 50300 | Soulseek client |

## Personal Cloud

| Container | Image | Host Port | Description |
|---|---|---|---|
| `nextcloud` | `nextcloud:apache` | internal (via Caddy) | Personal cloud |
| `nextcloud-db` | `mariadb:11` | internal | Nextcloud database |

## AI / Automation

| Container | Image | Host Port | Description |
|---|---|---|---|
| `open-webui` | `ghcr.io/open-webui/open-webui` | 3010 | UI for local/remote LLMs |
| `n8n` | `docker.n8n.io/n8nio/n8n` | 5678 | Workflow automation |
| `audiomuse-postgres` | `postgres:16` | internal | AudioMuse database |
| `audiomuse-redis` | `redis:7` | internal | AudioMuse cache |

## Networking

| Container | Image | Host Port | Description |
|---|---|---|---|
| `caddy` | `caddy:latest` | 80 / 443 | Reverse proxy + automatic TLS |
| `adguardhome` | `adguard/adguardhome` | 53 / 8082 (UI) | DNS with ad-blocking |
| `wg-easy` | `weejewel/wg-easy` | — | WireGuard VPN with web UI |

!!! warning "Deprecated wg-easy image"
    Currently using `weejewel/wg-easy` which is no longer maintained. Migrate to `ghcr.io/wg-easy/wg-easy`.

## Management

| Container | Image | Host Port | Description |
|---|---|---|---|
| `homepage` | `gethomepage/homepage:v1.9.0` | 3000 | Service dashboard |
| `uptime-kuma` | `louislam/uptime-kuma:2.0.2` | 3001 | Uptime monitoring |
| `portainer` | `portainer/portainer-ce:2.38.0` | 9000 (localhost only) | Container management |

## Other

| Container | Image | Description |
|---|---|---|
| `bononi-wiki` | `nginx:alpine` | Networking/cloud course website (`reti.chya43.it`) |
