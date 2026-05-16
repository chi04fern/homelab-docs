# Runbooks

Operational guides for common homelab tasks.

## Coming Soon

- How to add a new service with Caddy
- How to create a WireGuard client
- How to back up Nextcloud
- How to check container status
- How to update all containers

---

```bash
# Check status of all containers
docker ps -a

# Update a container
docker compose pull <service>
docker compose up -d <service>

# Live logs
docker logs -f <container_name>
```
