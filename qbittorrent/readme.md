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

1. Change to container directory:

```bash
cd ~/media_server/qBittorrent
```

2. Run the container:

```bash
docker compose up -d
```

3. Access qBittorrent in your browser:

```
http://<your-server-ip>:8080
```

4. Login Credentials, In first launch qBittorrent it will generate a random password. You can find it in container logs:

```bash
docker container logs qbittorrent
```

## Setup

1. In _Setting > Downloads_:
   - Enable _Delete .torrent files afterward_
   - Enable _Pre-allocate disk space for all files_
   - _Default Save Path_: `/data/torrents`
   - (Optional) Enable _Excluded file names_ and add from [List](./blacklist.txt)
2. In _Setting > WebUI_:
   - _Username_ and _Password_ for future logins
   - _Enable Bypass authentication for clients on local host_
     Or Enable _whitelisted IP subnet_ and write subnet `10.10.0.0/24` [Container Bridge Network](../README.md#container-bridge-network)
   - Disable Cross-Site Request Forgery (CSRF) protection.
