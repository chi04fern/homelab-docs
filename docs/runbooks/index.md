# Runbook

Guide operative per task comuni nel homelab.

## In arrivo

- Come aggiungere un nuovo servizio con Caddy
- Come creare un client WireGuard
- Come fare backup di Nextcloud
- Come verificare lo stato dei container
- Come aggiornare tutti i container

---

```bash
# Stato di tutti i container
docker ps -a

# Aggiornare un container
docker compose pull <service>
docker compose up -d <service>

# Log in tempo reale
docker logs -f <container_name>
```
