# Networking

## General Diagram

```
Internet
    │
    ▼
Cloudflare (DNS + proxy for public domains *.chya43.it)
    │
    ▼
Home Router
    │
    ├── LAN (192.168.0.x)
    │       │
    │       ▼
    │   Ninkear M6 (192.168.0.11)
    │       │
    │       ├── Caddy :80/:443  ← reverse proxy
    │       ├── AdGuard Home :53 ← DNS
    │       └── wg-easy ← WireGuard VPN
    │
    └── WireGuard clients (encrypted tunnel to Ninkear)
```

## Reverse Proxy — Caddy

Caddy handles all incoming HTTP/HTTPS traffic. It runs as a Docker container in `~/docker/proxy`.

**Domain types managed:**

| Type | Example | TLS |
|---|---|---|
| Public | `music.chya43.it` | Automatic Let's Encrypt |
| Internal LAN | `navidrome.home` | `tls internal` (self-signed) |

```caddyfile
# Internal domain
navidrome.home {
    tls internal
    reverse_proxy navidrome:4533
}

# Public domain
music.chya43.it {
    reverse_proxy navidrome:4533
}
```

!!! warning "Important"
    Never mix `tls internal` with public domains, and never leave Caddy without a TLS directive on `.home` domains.

**Useful commands:**

```bash
# Reload config without restarting
docker compose exec caddy caddy reload --config /etc/caddy/Caddyfile

# Full restart
docker restart caddy

# Live logs
docker logs -f caddy
```

## DNS — AdGuard Home

AdGuard Home acts as the DNS server for the entire LAN, providing:

- **Ad-blocking** via filter lists
- **DNS rewrites** for `.home` domains → `192.168.0.11`
- **Upstream DNS**: configurable (e.g. `1.1.1.1`, `8.8.8.8`)

Web UI port: `8082` → `http://192.168.0.11:8082`

!!! note
    If AdGuard goes down, the entire LAN loses DNS resolution. It is a single point of failure and should be monitored closely.

## VPN — WireGuard (wg-easy)

WireGuard provides secure remote access to internal services without exposing them publicly.

- Web UI managed by `wg-easy`
- Useful for reaching LAN-only services from outside (e.g. from school)

!!! warning "Deprecated image"
    Currently using: `weejewel/wg-easy` (no longer maintained).  
    Migrate to: `ghcr.io/wg-easy/wg-easy`

## Docker Networks

Containers communicate through internal Docker networks. A container cannot reach another unless they share the same network.

```bash
# List existing networks
docker network ls

# Inspect which containers are on a network
docker network inspect <network_name>
```

!!! tip "Practical rule"
    Inside Caddy (running in Docker), always use the container name as the hostname:
    ```
    reverse_proxy navidrome:4533   ✅
    reverse_proxy localhost:4533   ❌  (localhost = the Caddy container itself)
    ```

## Ports Exposed on Host

| Port | Protocol | Service |
|---|---|---|
| 80 | TCP | Caddy (HTTP) |
| 443 | TCP | Caddy (HTTPS) |
| 53 | TCP/UDP | AdGuard Home (DNS) |
| 8082 | TCP | AdGuard Home (UI) |
| 3000 | TCP | Homepage |
| 3001 | TCP | Uptime Kuma |
| 3010 | TCP | Open WebUI |
| 4533 | TCP | Navidrome |
| 5055 | TCP | Jellyseerr |
| 5678 | TCP | n8n |
| 6767 | TCP | Bazarr |
| 6881 | TCP/UDP | qBittorrent P2P |
| 7878 | TCP | Radarr |
| 8081 | TCP | qBittorrent UI |
| 8096 | TCP | Jellyfin |
| 8191 | TCP | FlareSolverr |
| 8989 | TCP | Sonarr |
| 9000 | TCP | Portainer (localhost only) |
| 9696 | TCP | Prowlarr |
