# Dockge Setup Guide

![](https://github.com/louislam/dockge/blob/master/frontend/public/icon-192x192.png?raw=true "Logo")

## Overview

Dockge is a lightweight web-based interface for managing Docker containers and stacks. It serves as your container manager — allowing you to deploy, monitor, and control all your services in one interface.

**Dockge homepage:** [Dockge](https://dockge.kuma.pet)

## Configuration

### 1. Update `compose.yaml`

- `/path/to/stacks` modify to media server directory, recommend on `/home/user/home_server`.
- Setup `DOCKGE_STACKS_DIR`.

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/dockge
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Dockge via your browser:

```
http://<your-server-ip>:5001
```

## Notes

- To manage services, either create them via the Dockge Web UI or move their `compose.yaml` and `.env` files into your configured stack path (`DOCKGE_STACKS_DIR`).
