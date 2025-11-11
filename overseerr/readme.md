# Overseerr Setup Guide

## Overview

**Overseerr** is a request management and media discovery tool it allows users to request movies and TV shows for your media server.
It integrates directly with **Plex** or **Jellyfin** for library monitoring, and works with **Radarr**, and **Sonarr** to automatically process approved requests.

**Overseerr Official Site:** [Overseerr](https://overseerr.dev/)

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

- Find your timezone `TZ`, from the [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/overseerr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Overseerr in your browser:

```
http://<your-server-ip>:5055
```

## Setup

1. Sign in with your Plex account.
1. In _Radarr Setting_, Add Radarr:
   - _Server Name_: `Radarr`
   - _Hostname_: `http://radarr:7878`
   - _API Key_: In Radarr go to _Setting > General_ copy `API Key`
   - Click _Test_
   - Select your _Quality Profile_
   - Select your _Root Folder_
   - Click _Add Server_
1. Add _Sonarr_, Same procedure.
