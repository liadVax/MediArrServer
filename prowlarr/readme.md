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

1. Start the container:

```bash
docker compose up -d
```

2. Access Prowlarr in your browser:

```
http://<your-server-ip>:9696
```
