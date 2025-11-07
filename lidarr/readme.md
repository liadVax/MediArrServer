# Lidarr Setup Guide

## Overview

**Lidarr** is a music collection manager for Usenet and BitTorrent users. It automatically downloads new albums, and organizes your music library. Lidarr integrates seamlessly with download clients

**Lidarr Official Site:** [Lidarr](https://lidarr.audio/)

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

- Find your timezone `TZ`, from the [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/lidarr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Lidarr in your browser:

```
http://<your-server-ip>:8686
```

## Setup

1. In _Setting > Media Management_:
   - Add _Root Folder_:
     - _Name_: `music`
     - _path_: `/data/media/music`
   - Enable _Rename Tracks_
   - Click _Show Advanced_ and Enable _Use Hardlinks instead of Copy_
2. In _Setting > Download Clients_:
   - Add _qBittorrent_:
     - _Host_: `qbittorrent` or use your `IP address`
     - qBittorrent _Username_ and _Password_
     - _Category_: `movies`
     - Test and Save
   - Add _NZBGet_, Same procedure.
3. In _Setting > General_ Change:
   - In _Authentication_ Select `Forms (Login Page)`
   - _Username_ and _Password_ for future logins
