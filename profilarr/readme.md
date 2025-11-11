# Profilarr Setup Guide

## Overview

**Profilarr** is a management tool designed to synchronize quality profiles, custom formats, and other configuration settings across multiple \*arr applications. It saves time and reducing manual setup.

**Profilarr Official Site:** [Profilarr](https://github.com/voltron2000/profilarr)

---

## Configuration

### 1. Update `.env`

```bash
TZ=<your-timezone>      # e.g., Europe/London
```

- You can find your `TZ` in: [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/profilarr
```

1. Run the container:

```bash
docker compose up -d
```

1. Access Profilarr in your browser:

```
http://<your-server-ip>:6868
```

## Setup

1. In _Databse_:
   - Click _Link Repository_ and add [Database](https://github.com/Dictionarry-Hub/database)
1. In _External Apps_:
   - Add _Radarr_:
     - _Name_: `Radarr`
     - _Type_: `Radarr`
     - _Arr Server_: `http://radarr:7878`
     - _API Key_: In Radarr go to _Setting > General_ copy `API Key`
     - Test and Save\_
   - Add _Sonarr_, Same procedure.
1. In _Quality Profiles_ select preferred profiles and import to `Radarr` and `Sonarr`.

- For more info use https://dictionarry.dev
