# Homelab

self-hosted dell ubuntu homelab using Docker Compose

## Servers
- Dell OptiPlex 3070 Micro, i5-9500T, 2.2 GHz, 16GB RAM, 512GB SSD
- HP EliteDesk 800 G4 Mini, i5-8500T, 2.1 GHz, 16GB RAM, 256GB NVMe SSD 

## Services
| Service | Port | URL |
|---|---|---|
| Nginx Proxy Manager | 80, 443 (proxy), 81 (admin) | http://SERVER_IP:81 |
| Portainer | 9443 (https), 9000 (http) | https://SERVER_IP:9443 |
| Uptime Kuma | 3001 | http://SERVER_IP:3001 |
| Homepage | 3000 | http://SERVER_IP:3000 |
| Jellyfin | 8096 | http://SERVER_IP:8096 |

Other services ('payslips', 'studyflow', etc) are in separate repos.

## Structure
- `compose.yml` starts every stack at once
- `stacks/` one compose file per service
- `data/` persistent app data (git-ignored, created on first start)

```

## Everyday commands
Run from the repo root:
```bash
docker compose ps                        # status
docker compose logs -f uptime-kuma       # logs for one service
docker compose pull && docker compose up -d   # update images
docker compose down                      # stop everything
```

## Keeping it running

```bash
sudo systemctl enable docker
```

## Notes
Each service is managed with Docker Compose and stored in Github
