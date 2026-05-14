# Networking

## Schema generale

```
Internet
    │
    ▼
Cloudflare (DNS + proxy per domini pubblici *.chya43.it)
    │
    ▼
Router di casa
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
    └── WireGuard clients (tunnel cifrato verso Ninkear)
```

## Reverse Proxy — Caddy

Caddy gestisce tutto il traffico HTTP/HTTPS in ingresso. Gira come container Docker in `~/docker/proxy`.

**Tipi di dominio gestiti:**

| Tipo | Esempio | TLS |
|---|---|---|
| Pubblico | `music.chya43.it` | Let's Encrypt automatico |
| Interno LAN | `navidrome.home` | `tls internal` (self-signed) |

```caddyfile
# Dominio interno
navidrome.home {
    tls internal
    reverse_proxy navidrome:4533
}

# Dominio pubblico
music.chya43.it {
    reverse_proxy navidrome:4533
}
```

!!! warning "Attenzione"
    Non mischiare `tls internal` con domini pubblici, né lasciare Caddy senza direttiva TLS su domini `.home`.

**Comandi utili:**

```bash
# Reload configurazione senza restart
docker compose exec caddy caddy reload --config /etc/caddy/Caddyfile

# Restart completo
docker restart caddy

# Log in tempo reale
docker logs -f caddy
```

## DNS — AdGuard Home

AdGuard Home funge da DNS server per tutta la LAN, con:

- **Ad-blocking** tramite liste filtri
- **DNS rewrites** per i domini `.home` → `192.168.0.11`
- **Upstream DNS**: configurabili (es. `1.1.1.1`, `8.8.8.8`)

Porta UI: `8082` → `http://192.168.0.11:8082`

!!! note
    Se AdGuard va down, tutta la LAN perde risoluzione DNS. È un single point of failure da tenere monitorato.

## VPN — WireGuard (wg-easy)

WireGuard permette accesso remoto sicuro ai servizi interni senza esporli pubblicamente.

- UI web: gestita da `wg-easy`
- Utile per raggiungere servizi LAN-only dall'esterno (es. da scuola)

!!! warning "Immagine deprecata"
    In uso: `weejewel/wg-easy` (non più mantenuta).  
    Da migrare a: `ghcr.io/wg-easy/wg-easy`

## Reti Docker

I container comunicano tramite reti Docker interne. Un container non raggiunge un altro se non sono sulla stessa rete.

```bash
# Vedere le reti esistenti
docker network ls

# Ispezionare quali container sono su una rete
docker network inspect <nome_rete>
```

!!! tip "Regola pratica"
    In Caddy (dentro Docker), usare sempre il nome del container come hostname:
    ```
    reverse_proxy navidrome:4533   ✅
    reverse_proxy localhost:4533   ❌  (localhost = il container Caddy stesso)
    ```

## Porte esposte sull'host

| Porta | Protocollo | Servizio |
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
