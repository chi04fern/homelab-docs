# Incident Backlog

Registro degli incidenti risolti nel homelab. Ogni incidente documentato include sintomi, root cause, fix e lesson learned.

## Stato

| # | Titolo | Categoria | Confidence | Status |
|---|---|---|---|---|
| 01 | Pelican/Traefik hijack porta 443 | Docker / Networking | Alto | Draft |
| 02 | Caddy bloccato da Apache su porta 80 | Reverse Proxy | Alto | Draft |
| 03 | Cloudflare "Invalid SSL certificate" | TLS / DNS | Alto | Draft |
| 04 | Mixing domini `.home` e pubblici con TLS sbagliato | TLS / Caddy | Alto | Draft |
| 05 | systemctl reload caddy non funzionava | Docker / Systemd | Alto | Draft |
| 06 | Jellyseerr non raggiungeva Jellyfin | Docker Networking | Alto | Draft |
| 07 | Uptime Kuma non monitorava container su altre reti | Docker Networking | Alto | Draft |
| 08 | Nextcloud in conflitto con qBittorrent su porta 8081 | Porte | Alto | Draft |
| 09 | Homepage/qBittorrent: porta API sbagliata (6881 vs 8080) | Configurazione | Alto | Draft |
| 10 | Open WebUI in conflitto con Homepage su porta 3000 | Porte | Alto | Draft |
| 11 | Open WebUI non raggiungeva Ollama (Docker boundary) | Docker / Networking | Alto | Draft |
| 12 | n8n crashava per permessi sul volume | Permessi | Medio | Needs logs |
| 13 | WireGuard: client connesso ma internet non funzionava | VPN / NAT | Alto | Draft |
| 14 | wg-easy immagine vecchia / sysctl mancanti | VPN | Medio | Draft |
| 15 | UFW non installato / porte esposte su 0.0.0.0 | Firewall / Security | Alto | Draft |
| 16 | CGNAT con amico su Parsec | Networking / ISP | Alto | Draft |
| 17 | AdGuard rompeva alcuni siti | DNS | Alto | Draft |
| 18 | Prowlarr con errori DNS dentro container | DNS / Docker | Alto | Draft |
| 19 | Caddy non risolveva upstream hostname | Docker Networking | Alto | Draft |
| 20 | wstunnel: WireGuard over WebSockets (firewall scuola) | VPN / Firewall | Medio | Draft |
| 21 | Navidrome non raggiungibile via Tailscale | VPN / Firewall | Medio | Needs logs |
| 22 | "Unable to parse TLS packet header" su Navidrome | TLS | Alto | Draft |
| 23 | Jellyfin CPU spike alle 3 di notte | Media / Monitoring | Alto | Draft |
| 24 | Jellyfin VA-API hardware acceleration setup | Media / Hardware | Alto | Draft |
| 25 | Octo-Fiesta "Stream was not readable" | Musica | Basso | Needs logs |
| 26 | AudioMuse rate limit 429 da Gemini API | AI / Automazione | Medio | Draft |
| 27 | ONLYOFFICE / Nextcloud integrazione incompleta | Cloud | Basso | Needs logs |
| 28 | Jellyfin Discord RPC setup | Media | Medio | Draft |
| 29 | Feishin → Navidrome configurazione | Musica | Medio | Draft |

## Priorità documentazione

I più utili per portfolio (coprono Linux, Docker, Networking, TLS, VPN, DNS, Permessi):

1. Pelican/Traefik hijack porta 443
2. Caddy port 80 conflict with Apache
3. Docker network mismatch (Jellyseerr → Jellyfin)
4. WireGuard full tunnel NAT failure
5. Open WebUI → Ollama Docker boundary
6. AdGuard DNS instability
7. UFW / service exposure review
8. Cloudflare SSL error
9. n8n volume permission denied
10. Jellyfin CPU spike

---

> **Come contribuire**: per ogni incidente, creare una pagina in `incidents/<nome>.md` seguendo il [template](#template).

## Template

```markdown
# Incident: <Titolo>

## Summary
Breve descrizione dell'incidente.

## Impact
Cosa ha smesso di funzionare.

## Symptoms
- Sintomo 1
- Sintomo 2

## Root Cause
Causa principale del problema.

## Diagnosis
Comandi usati per diagnosticare:

\`\`\`bash
comando --esempio
\`\`\`

## Resolution
Passi per risolvere.

## Prevention
Come evitarlo in futuro.

## Lessons Learned
Cosa ho imparato tecnicamente.
```
