# Radarr Setup Guide

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

1. Start the container:

```bash
docker compose up -d
```

2. Access Radarr in your browser:

```
http://<your-server-ip>:7878
```
