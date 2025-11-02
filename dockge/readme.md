# Dockge Setup Guide

## Overview

Dockge is a lightweight web-based interface for managing Docker containers and stacks. It serves as your container manager — allowing you to deploy, monitor, and control all your services in one interface.

**Dockge homepage:** [https://dockge.kuma.pet](https://dockge.kuma.pet)

## Configuration

### 1. Update `compose.yaml`

- Setup `/path/to/stacks`, (I used `/home/user/home_server`).
- Setup `DOCKGE_STACKS_DIR`.

### 2. Update `.env`

- Configure your user and group IDs:

```bash
id $USER
```

Use the output values for `PUID` and `PGID`.

- Set your timezone (TZ) using a value from the [TZ database list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

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
