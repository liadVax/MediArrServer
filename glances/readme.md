# Glances Setup Guide

<img src="https://raw.githubusercontent.com/nicolargo/glances/c4f6c04eb40c41f050bfce4ecb63308ea49d838b/docs/_static/Glances%20Logo.svg" width="128" height="128">

## Overview

**Glances** is a system monitoring tool that provides real-time insights into your server’s CPU, memory, disk, network usage, and running processes all from a web-based dashboard.

**Glances Official Site:** [Glances](https://nicolargo.github.io/glances/)

## Deployment

1. Change to container directory:

```bash
cd ~/media_server/glances
```

2. Run the container:

```bash
docker compose up -d
```

3. Access Glances via your browser:

```
http://<your-server-ip>:61208
```
