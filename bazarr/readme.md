# Bazarr Setup Guide

![](https://github.com/morpheus65535/bazarr/blob/master/frontend/public/images/logo128.png?raw=true "Logo")

## Overview

**Bazarr** is a companion application for Sonarr and Radarr that automatically downloads and manages subtitles for your movies and TV shows.  
It supports multiple languages and integrates seamlessly with your existing \*arr stack to keep your media library complete with accurate, synced subtitles.

**Bazarr Official Site:** [Bazarr](https://www.bazarr.media/)

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

- You can find your `TZ` in: [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/bazarr
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Bazarr in your browser:

```
http://<your-server-ip>:8989
```

## Setup

1. In _Setting > General_:
   - In _Authentication_ Select `Forms (Login Page)`
   - _Username_ and _Password_ for future logins
2. In _Setting > Sonarr_:
   - Click _Enabled_
   - _Host_: `sonarr`
   - _API Key_: In Sonarr go to _Setting > General_ copy `API Key`
   - Click Test and Save
3. In _Setting > Radarr_:
   - Same procedure.
4. In _Setting > Languages_:
   - In _Languages Filter_ Type languages you want for your subtitles
   - In _Languages Profile_ Add new profile and add your languages
   - In _Default Language Profiles For Newly Added Shows_ Enable Series and Movies with your added profile
5. In _Setting > Providers_:
   - Add subtitles providers you would like to enable.

- For more info use https://wiki.bazarr.media
