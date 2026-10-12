# Homelab

self-hosted ubuntu homelab using Docker Compose

## Services
| Service | Port | URL |
|---|---|---|
| Nginx Proxy Manager | 80, 443 (proxy), 81 (admin) | http://SERVER_IP:81 |
| Portainer | 9443 (https), 9000 (http) | https://SERVER_IP:9443 |
| Uptime Kuma | 3001 | http://SERVER_IP:3001 |
| Homepage | 3000 | http://SERVER_IP:3000 |

## Structure
- `compose.yml` starts every stack at once
- `stacks/` one compose file per service
- `data/` persistent app data (git-ignored, created on first start)

## Setup
```bash
git clone <this repo> ~/homelab
cd ~/homelab
cp .env.example .env              # then edit HOMEPAGE_ALLOWED_HOSTS
docker network create homelab     # one time only
docker compose up -d
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
Containers use `restart: always`, so they come back after a crash or reboot
as long as Docker itself starts on boot:
```bash
sudo systemctl enable docker
```

## Notes
Each service is managed with Docker Compose and stored in Github
