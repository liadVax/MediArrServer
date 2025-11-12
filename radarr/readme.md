# Radarr Setup Guide

![](https://github.com/Radarr/Radarr/blob/develop/Logo/128.png?raw=true "Logo")

## Overview

**Radarr** is a movie collection manager for Usenet and BitTorrent users. It automates the downloading, sorting, and renaming of movies, working seamlessly with indexers and download clients.

**Radarr Official Site:** [Radarr](https://radarr.video/)

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
cd ~/media_server/radarr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Radarr in your browser:

```
http://<your-server-ip>:7878
```

## Setup

1. In _Series > Library Import_:
   - Click _Start Import_ Choose `/data/media/movies`
2. In _Setting > Media Management_:
   - Enable _Rename Movies_
   - Click _Show Advanced_ and Enable _Use Hardlinks instead of Copy_
3. In _Setting > General_:
   - In _Authentication_ Select `Forms (Login Page)`
   - _Username_ and _Password_ for future logins
4. In _Setting > Download Clients_:
   - Add _qBittorrent_:
     - _Host_: `qbittorrent` or use your `IP address`
     - qBittorrent _Username_ and _Password_
     - _Category_: `movies`
     - Test and Save
   - Add _NZBGet_, Same procedure.
5. In _Setting > Profiles_:
   - Select the profile that you want to use/prefer
   - For custom Quality Profiles you can use:
     - [TRaSh-Guide](https://trash-guides.info/Radarr/radarr-setup-quality-profiles)
     - [Profilarr](../profilarr)
