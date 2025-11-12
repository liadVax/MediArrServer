# Jellyfin Setup Guide

![]("Logo")

<img src="https://raw.githubusercontent.com/jellyfin/jellyfin/1da67e5e10fea9f3bca66e4f510db25f1b4fcd80/Jellyfin.Server/wwwroot/api-docs/banner-dark.svg" width="256" height="128">

## Overview

**Jellyfin** is a free and open-source media server that allows you to organize, manage, and stream your movies and TV shows to any device.  
It serves as an alternative to Plex, offering full privacy, no subscriptions, and complete control over your media environment.

**Jellyfin Official Site:** [Jellyfin](https://jellyfin.org/)

## Configuration

### 1. Update `compose.yaml`

- `/path/to/data/media` modify to your media directory, Make sure this directory as defined in the [Data Directory Structure](../readme.md#File-and-Folder-Structure).

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
cd ~/media_server/jellyfin
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Jellyfin in your browser:

```
http://<your-server-ip>:8096
```

## Setup

1. Follow and complete the initial setup wizard.
2. Add your Movies and TV folders to build your library.
