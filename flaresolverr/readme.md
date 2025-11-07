# Flaresolverr Setup Guide

## Overview

Flaresolverr is a service that bypasses Cloudflare protections for web scraping or indexer requests. Many \*arr applications (Sonarr, Radarr, Lidarr, etc.) rely on Flaresolverr to access sites that use Cloudflare anti-bot protections.

**Flaresolverr repo:** [FlareSolverr](https://github.com/FlareSolverr/FlareSolverr)

## Configuration

### 1. Update `.env`

- Set your timezone (`TZ`) using a value from the [TZ database list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/flaresolverr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Flaresolverr via your browser:

```
http://<your-server-ip>:8191
```
