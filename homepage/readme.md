# Homepage Setup Guide

## Overview

Homepage is a web-based dashboard that provides an overview of your media server: showing system stats, disks, connected services, weather, and shortcuts to your containers. It's highly customizable and serves as a dashboard for monitoring your server.

**Official Homepage:** [Homepage](https://gethomepage.dev/)

![](./myHomepage.png "My Homepage")

## Configuration

### 1. Update `compose.yaml`

- `path/to/icons` is optional variable, to displaying your own icons.
- `path/to/data` is optional variable, to displaying stats of disk data usage.

### 2. Update `.env`

- `PUID` & `PGID`, Set your user and group IDs using:

```bash
id $USER
```

- `TZ`, Set your timezone using a value from the [TZ database list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

- `HOMEPAGE_ALLOWED_HOSTS`, Use `*` for LAN access or specify your devices `ip` explicitly.

- `HOMEPAGE_VAR_WEATHER` is optional variable to show weather information, i used [openweathermap](https://openweathermap.org).

## Deployment

Start the container:

```bash
docker compose up -d
```

Access Homepage in your browser:

```
http://<your-server-ip>:3000
```
