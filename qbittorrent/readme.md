# qBittorrent Setup Guide

## Overview

**qBittorrent** is a powerful, open-source BitTorrent client that provides a clean web interface and advanced features such as category-based organization, automated RSS downloads, and integration with \*arr applications (like Radarr and Sonarr).

**qBittorrent Official Site:** [qBittorrent](https://www.qbittorrent.org/)

## Configuration

### 1. Update `compose.yaml`

- Modify `/path/to/data/torrents` to point to your actual torrents directory, as defined in the [Data Directory Structure](../README.md#file-and-folder-structure)

### 2. Update `.env`

```
PUID=<your-user-id>     # User ID for file ownership
PGID=<your-group-id>    # Group ID for file ownership
TZ=<your-timezone>      # e.g., Europe/London
```

- You can find your `PUID` and `PGID` with:

```bash
id $USER
```

- You can find your `TZ` in: [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Start the container:

```bash
docker compose up -d
```

2. Access qBittorrent in your browser:

```
http://<your-server-ip>:8080
```

3. Login Credentials, In first launch qBittorrent it will generate a random password. You can find it in container logs

```bash
docker container logs qbittorrent
```

## Setup

-- TBD --
