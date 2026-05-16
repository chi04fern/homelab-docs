# Incident Backlog

Log of incidents resolved in the homelab. Each documented incident includes symptoms, root cause, fix, and lessons learned.

## Status

| # | Title | Category | Confidence | Status |
|---|---|---|---|---|
| 01 | Pelican/Traefik hijacking port 443 | Docker / Networking | High | Draft |
| 02 | Caddy blocked by Apache on port 80 | Reverse Proxy | High | Draft |
| 03 | Cloudflare "Invalid SSL certificate" | TLS / DNS | High | Draft |
| 04 | Mixing `.home` and public domains with wrong TLS | TLS / Caddy | High | Draft |
| 05 | systemctl reload caddy not working | Docker / Systemd | High | Draft |
| 06 | Jellyseerr could not reach Jellyfin | Docker Networking | High | Draft |
| 07 | Uptime Kuma not monitoring containers on other networks | Docker Networking | High | Draft |
| 08 | Nextcloud conflicting with qBittorrent on port 8081 | Ports | High | Draft |
| 09 | Homepage/qBittorrent: wrong API port (6881 vs 8080) | Configuration | High | Draft |
| 10 | Open WebUI conflicting with Homepage on port 3000 | Ports | High | Draft |
| 11 | Open WebUI could not reach Ollama (Docker boundary) | Docker / Networking | High | Draft |
| 12 | n8n crashing due to volume permission error | Permissions | Medium | Needs logs |
| 13 | WireGuard: client connected but no internet | VPN / NAT | High | Draft |
| 14 | wg-easy outdated image / missing sysctl | VPN | Medium | Draft |
| 15 | UFW not installed / services exposed on 0.0.0.0 | Firewall / Security | High | Draft |
| 16 | CGNAT issue with friend on Parsec | Networking / ISP | High | Draft |
| 17 | AdGuard breaking some websites | DNS | High | Draft |
| 18 | Prowlarr DNS errors inside container | DNS / Docker | High | Draft |
| 19 | Caddy unable to resolve upstream hostname | Docker Networking | High | Draft |
| 20 | wstunnel: WireGuard over WebSockets (school firewall) | VPN / Firewall | Medium | Draft |
| 21 | Navidrome not reachable over Tailscale | VPN / Firewall | Medium | Needs logs |
| 22 | "Unable to parse TLS packet header" on Navidrome | TLS | High | Draft |
| 23 | Jellyfin CPU spike at 3am | Media / Monitoring | High | Draft |
| 24 | Jellyfin VA-API hardware acceleration setup | Media / Hardware | High | Draft |
| 25 | Octo-Fiesta "Stream was not readable" | Music | Low | Needs logs |
| 26 | AudioMuse rate limit 429 from Gemini API | AI / Automation | Medium | Draft |
| 27 | ONLYOFFICE / Nextcloud integration incomplete | Cloud | Low | Needs logs |
| 28 | Jellyfin Discord RPC setup | Media | Medium | Draft |
| 29 | Feishin → Navidrome configuration | Music | Medium | Draft |

## Documentation Priority

Most valuable for portfolio (covering Linux, Docker, Networking, TLS, VPN, DNS, Permissions):

1. Pelican/Traefik hijacking port 443
2. Caddy port 80 conflict with Apache
3. Docker network mismatch (Jellyseerr → Jellyfin)
4. WireGuard full tunnel NAT failure
5. Open WebUI → Ollama Docker boundary issue
6. AdGuard DNS instability
7. UFW / service exposure review
8. Cloudflare SSL error
9. n8n volume permission denied
10. Jellyfin CPU spike due to media processing

---

> **How to contribute**: for each incident, create a page at `incidents/<name>.md` following the [template](#template).

## Template

```markdown
# Incident: <Title>

## Summary
Brief description of the incident.

## Impact
What stopped working.

## Symptoms
- Symptom 1
- Symptom 2

## Root Cause
The main cause of the issue.

## Diagnosis
Commands used to diagnose:

\`\`\`bash
example --command
\`\`\`

## Resolution
Steps taken to fix it.

## Prevention
How to avoid it in the future.

## Lessons Learned
What I learned technically.
```
