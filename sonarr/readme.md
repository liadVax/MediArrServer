# Sonarr Setup Guide

## Overview

Sonarr is an automated PVR (Personal Video Recorder) utility designed to track, download, and manage your TV show collection. It monitors multiple RSS feeds for new episodes, interfaces with your preferred download client (like qBittorrent or NZBGet), and automatically sorts and renames files.

**Sonarr Official Site:** [Sonarr](https://sonarr.tv/)

## Configuration (Docker Compose)

The configuration below uses variables defined in your root `.env` file (`PUID`, `PGID`, `TZ`) and assumes your volumes are mounted according to the paths in your `compose.yaml`.

### 1. Update `compose.yaml`

- `/path/to/data`, very **important** must be aligned with your data folders as described in the data directory structure section. (I used `/mnt/user/data`). This single volume must contain both your Movie Library and your Downloads folder.

### 2. Update `.env`

- `PUID` & `PGID`, Set your user and group IDs using:

```bash
id $USER
```

- `TZ`, Set your timezone using a value from the [TZ database list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

Start the container:

```bash
docker compose up -d
```

Access Homepage in your browser:

```
http://<your-server-ip>:8989
```
