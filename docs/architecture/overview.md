# Overview
 
The homelab runs entirely on a **Ninkear M6** mini PC, with Ubuntu 24.04 and Docker Compose as the orchestrator.
 
## Network Flow
 
```mermaid
graph TD
    Internet --> Cloudflare
    Cloudflare -->|"*.chya43.it"| Router
    Router -->|"192.168.0.11"| Ninkear
 
    Ninkear --> Caddy
    Ninkear --> AdGuard
    Ninkear --> WireGuard
 
    Caddy -->|":8096"| Jellyfin
    Caddy -->|":4533"| Navidrome
    Caddy -->|":80"| Nextcloud
    Caddy -->|":5055"| Jellyseerr
    Caddy -->|":3010"| OpenWebUI["Open WebUI"]
    Caddy -->|":5678"| n8n
    Caddy -->|":3000"| Homepage
    Caddy -->|":3001"| UptimeKuma["Uptime Kuma"]
 
    WireGuard -->|"remote clients"| Ninkear
    AdGuard -->|".home domains"| Caddy
```
 
## Services by Category
 
```mermaid
graph LR
    subgraph Ninkear M6
        subgraph Media
            Jellyfin
            Sonarr
            Radarr
            Bazarr
            Prowlarr
            Jellyseerr
            qBittorrent
            FlareSolverr
        end
 
        subgraph Music
            Navidrome
            Tidaloader
            AudioMuse["AudioMuse AI"]
            OctoFiesta["Octo-Fiesta"]
            Slskd
            Beets
        end
 
        subgraph Cloud
            Nextcloud
            MariaDB
        end
 
        subgraph AI & Automation
            OpenWebUI["Open WebUI"]
            n8n
            Postgres["Postgres\n(AudioMuse)"]
            Redis["Redis\n(AudioMuse)"]
        end
 
        subgraph Networking
            Caddy
            AdGuard["AdGuard Home"]
            WireGuard["WireGuard\n(wg-easy)"]
        end
 
        subgraph Management
            Homepage
            UptimeKuma["Uptime Kuma"]
            Portainer
        end
    end
```
 
## Docker Network Layout
 
```mermaid
graph TD
    subgraph proxy network
        Caddy
        Jellyfin
        Navidrome
        Nextcloud
        Jellyseerr
        OpenWebUI["Open WebUI"]
        n8n
        Homepage
        UptimeKuma["Uptime Kuma"]
        AdGuard["AdGuard Home"]
    end
 
    subgraph media-stack network
        Sonarr
        Radarr
        Bazarr
        Prowlarr
        qBittorrent
        FlareSolverr
    end
 
    subgraph audiomuse network
        AudioMuse["AudioMuse AI"]
        Postgres
        Redis
    end
 
    Caddy -->|"reverse proxy"| Jellyfin
    Caddy -->|"reverse proxy"| Navidrome
    Caddy -->|"reverse proxy"| Nextcloud
    Jellyseerr -->|"API"| Jellyfin
    Sonarr -->|"indexer"| Prowlarr
    Radarr -->|"indexer"| Prowlarr
```
 
## Sections
 
- [Hardware](hardware.md) — server and workstation specs
- [Services](services.md) — full list of all containers with ports and descriptions
- [Networking](networking.md) — Caddy, AdGuard, WireGuard, Docker networks
