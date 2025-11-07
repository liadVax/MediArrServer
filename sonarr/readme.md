# Sonarr Setup Guide

## Overview

**Sonarr** is a TV shows collection manager for Usenet and BitTorrent users. It automates the downloading, sorting, and renaming of the show, working seamlessly with indexers and download clients.

**Sonarr Official Site:** [Sonarr](https://sonarr.tv/)

## Configuration

### 1. Update `compose.yaml`

- `/path/to/data` modify to your data directory, Make sure this directory as defined in the [Data Directory Structure](../readme.md#File-and-Folder-Structure).

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
cd ~/media_server/sonarr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Sonarr in your browser:

```
http://<your-server-ip>:8989
```

## Setup

1. In _Series > Library Import_ Change:
   - Click _Start Import_ Choose `/data/media/tv`
2. In _Setting > Media Management_ Change:
   - Enable _Rename Episodes_
3. In _Setting > General_ Change:
   - In _Authentication_ Select `Forms (Login Page)`
   - _Username_ and _Password_ for future logins
4. In _Setting > Download Clients_:
   - Add _qBittorrent_:
     - _Host_: `qbittorrent` or use your `IP address`
     - qBittorrent _Username_ and _Password_
     - _Category_: `tv`
     - Test and Save
   - Add _NZBGet_, Same procedure.
