# Dockge Setup Guide

## Overview

Dockge is a lightweight web-based interface for managing Docker containers and stacks. It serves as your container manager — allowing you to deploy, monitor, and control all your services in one interface.

**Dockge homepage:** [Dockge](https://dockge.kuma.pet)

## Configuration

### 1. Update `compose.yaml`

- Setup `/path/to/stacks`, (I used `/home/user/home_server`).
- Setup `DOCKGE_STACKS_DIR`.

## Deployment

Run the container:

```bash
docker compose up -d
```

Access Dockge via your browser:

```
http://<your-server-ip>:5001
```

## Notes

- Mounting `/var/run/docker.sock` allows Dockge to control Docker directly — handle this with care.
- To manage services, either create them via the Dockge web UI or move their `compose.yaml` and `.env` files into your configured stack path (`DOCKGE_STACKS_DIR`).
