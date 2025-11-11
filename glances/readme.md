# Glances Setup Guide

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
