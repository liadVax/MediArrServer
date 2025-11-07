# Prowlarr Setup Guide

## Overview

**Prowlarr** is the indexer manager for the *arr ecosystem — it connects your *arr applications (Sonarr, Radarr, Lidarr, etc.) to multiple indexers and manages them.

**Prowlarr Official Site:** [Prowlarr](https://prowlarr.com)

## Configuration

### 1. Update `.env`

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
cd ~/media_server/prowlarr
```

1. Run the container:

```bash
docker compose up -d
```

2. Access Prowlarr in your browser:

```
http://<your-server-ip>:9696
```

## Setup

1. In _Settings > Indexers_:
   - Add _FlareSolverr_:
     - _Name_: `FlareSolverr`
     - _Tags_: `flaresolverr`
     - _Host_: `http://flaresolverr:8191` or `http://10.10.0.0:8191`
   - Test and Save
2. In _Settings > Apps_:
   - Add _Raddar_:
     - _Name_: `Radarr`
     - _Prowlarr Server_: `http://prowlarr:9696`
     - _Radarr Server_: `http://radarr:7878`
     - _API Key_: In Raddar go to _Setting > General_ copy `API Key`
     - Test and Save
   - Add _Sonnar_, Same procedure.
   - Add _Lidarr_, Same procedure.
3. In _Setting > Download Clients_:
   - Add _qBittorrent_:
     - _Host_: `qbittorrent` or use your `IP address`
     - qBittorrent _Username_ and _Password_
     - _Default Category_: `prowlarr`
     - Test and Save
   - Add _NZBGet_, Same procedure.
4. In _Setting > General_ Change:
   - In _Authentication_ Select `Forms (Login Page)`
   - _Username_ and _Password_ for future logins
5. In _Indexers_:
   - Click Add Indexers and select you favorite Torrents/Usent Indexers.
     - Cloudflare DDoS Protection blocked, add in _Tags_ `flaresolverr`, Verify `Flaresolverr` container running.
   - Test and Save
