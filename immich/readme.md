# Immich Setup Guide

![](https://raw.githubusercontent.com/immich-app/immich/4c9142308f3beeb86f898509e3502ebf40b05339/design/immich-logo.svg "Logo")

## Overview

**Immich** is a self-hosted photo and video backup solution designed for mobile and web platforms.  
It provides automatic uploads from your devices, AI-powered search and face recognition — all stored securely on your own server.  
Immich is an excellent open-source alternative to Google Photos or Apple iCloud Photos.

**Immich Official Site:** [Immich](https://immich.app/)

## Configuration

### 1. Update `.env`

```
UPLOAD_LOCATION=<your-immich-directory>
DB_DATA_LOCATION=<your-immich-directory>
TZ=<your-timezone>
DB_PASSWORD=<your-password>
```

- Modify `UPLOAD_LOCATION` and `DB_DATA_LOCATION` to point to your preferred immich directory to store all pictures, metadata and etc...

- Find your timezone `TZ`, from the [TZ Database List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/immich
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Immich in your browser:

```
http://<your-server-ip>:2283
```

## Setup

1. Follow and complete the initial setup wizard.
2. Configure automatic backups from your mobile device and manage your photo collections.
