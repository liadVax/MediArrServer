# Plex Setup Guide

## Overview

**Plex** is a powerful media server that organizes your movies and TV shows and streams them to any device.  
It integrates seamlessly with \*arr applications (like Radarr, Sonarr, and Lidarr), automatically updating your library when new media is downloaded.

**Plex Official Site:** [Plex](https://www.plex.tv/)

## Configuration

### 1. Update `compose.yaml`

- `/path/to/data/media` modify to your media directory, Make sure this directory as defined in the [Data Directory Structure](../readme.md#File-and-Folder-Structure).

### 2. Update `.env`

```
PUID=<your-user-id>     # User ID for file ownership
PGID=<your-group-id>    # Group ID for file ownership
TZ=<your-timezone>      # e.g., Europe/London
PLEX_CLAIM=<your-key>   # Plex Claim Token
```

- You can find your `PUID` and `PGID` with:

```bash
id $USER
```

- Find your timezone `TZ`, from the [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

- Get your `PLEX_CLAIM` Token from [Plex.tv](https://www.plex.tv/claim)

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/plex
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Plex in your browser:

```
http://<your-server-ip>:32400/web
```

## Setup

1. Sign in with your Plex account (or create one if you don’t have it).
2. Follow the setup wizard to add your Movies, TV, and Music libraries.
3. Configure remote access if you want to stream outside your local network.

## Notes

- If Plex page doesn’t load the first time, allow Plex through firewall.

```bash
 sudo ufw allow 32400
```
