# NZBGet Setup Guide

![](https://github.com/nzbget/nzbget/blob/develop/webui/img/favicon-256x256.png?raw=true "Logo")

## Overview

**NZBGet** is a lightweight and efficient Usenet downloader optimized for performance and automation.  
It integrates with \*arr applications (like Radarr, Sonarr, and Lidarr) to automatically download and organize media files from Usenet servers.

**NZBGet Official Site:** [NZBGet](https://nzbget.net/)

## Configuration

### 1. Update `compose.yaml`

- Modify `/path/to/data/usenet` to point to your actual usenet directory, as defined in the [Data Directory Structure](../README.md#file-and-folder-structure)

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
cd ~/media_server/nzbget
```

2. Run the container:

```bash
docker compose up -d
```

3. Access NZBGet in your browser:

```
http://<your-server-ip>:6789
```

4. Login Credentials, Defaults in first launch

```bash
Username: nzbget
Password: tegbzn6789
```

## Setup

1. In _PATHS_ Change:
   - MainDir `/data/usenet`
   - DestDir `${MainDir}/complete`
   - InterDir `${MainDir}/incomplete`
   - Enable _Pre-allocate disk space for all files_
   - _Default Save Path_: `/data/torrents`
2. In _SECURITY_ Change:
   - _ControlUsername_ and _ControlPassword_ for future logins
3. In _CATEGORIES_ Add/Modify:
   - _Category 1_:
     - _name_: `movies`
     - _DestDir_: `${MainDir}/complete/movies`
   - _Category 2_:
     - _name_: `tv`
     - _DestDir_: `${MainDir}/complete/tv`
   - _Category 3_:
     - _name_: `music`
     - _DestDir_: `${MainDir}/complete/music`
