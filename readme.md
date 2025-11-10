# Media Server - \*arr Stack

<img src="./homepage/homepage/icons/MyLogo.png" width="65%">

## Overview

This repository is my complete home media server using *arr stack.
“Lidarr, Prowlarr, Radarr, Readarr, Sonarr, and Whisparr are collectively referred to as "*arr" or "\*arrs". They are designed to automatically grab, sort, organize, and monitor your Music, Movie, E-Book, or TV Show collections for Lidarr, Radarr, Readarr, Sonarr, and Whisparr; and to manage your indexers and keep them in sync with the aforementioned apps for Prowlarr.”

## Services

Quick overview of each service included in this media server stack.
| Name | Description | Port | Status | Notes |
| -----| ----------- | :--: | :----: | ----- |
| [Dockge](./dockge) | Docker image management interface | `5001` | ✔️ | |
| [Homepage](./homepage) | Personalized dashboard for server info | `3000` | ✔️ | |
| [Flaresolverr](./flaresolverr) | Solves Cloudflare protections for indexers | `8191` | ✔️ | Needed by some indexers |
| [qBittorrent](./qbittorrent) | Torrent client | `8080` | ✔️ | |
| [NZBGet](./nzbget) | Usenet downloader | `6789` | ✔️ | |
| [Plex](./plex) | Media server for movies & TV | `32400` | ✔️ | |
| [Jellyfin](./jellyfin) | Media server for movies, TV, music | `8096` | ❌ | Dropped it, `Plex` gave me better user experience |
| [Immich](./immich) | Personal photo/video backup solution | `2283` | ✔️ | |
| [Sonarr](./sonarr) | TV show manager & downloader | `8989`| ✔️ | |
| [Radarr](./radarr) | Movie manager & downloader | `7878` | ✔️ | |
| [Lidarr](./lidarr) | Music collection manager | `8686` | ✔️ | |
| [Prowlarr](./prowlarr) | Indexer manager for Sonarr/Radarr/Lidarr | `9696` | ✔️ | |
| [Bazarr](./bazarr) | Subtitles management service for movies & TV | `6767` | ❌ | Didn't worked properly, Had problems with subtitle providers |
| [Profilarr](./profilarr) | Configuration management tool for Radarr/Sonar | `6868` | ✔️ | (Optional) For easy import custom formats and quality profiles|
| [Overseerr](./overseerr) | Request management and media discovery tool | `5055` | ✔️ | |
| [Glances](./glances) | Real-time monitoring tool | `61208` | ✔️ | |

## Recommended Setup Order

To ensure a smooth setup and proper inter-service integration, it’s recommended to deploy the containers in the following order:

1. `Dockge`
1. `Flaresolverr`
1. `Glances`
1. `qBittorrent, NZBGet`
1. `Radarr, Sonarr, Lidarr`
1. `Prowlarr`
1. `Plex, Jellyfin`
1. `Profilarr`
1. `Bazarr`
1. `Overseerr`
1. `Homepage`

## Prerequisites

- **Operating System:** Ubuntu 24.04.3
- **Docker & Docker Compose** Installed and configured
- **Network setup**: Devices on same LAN

## File and Folder Structure

It is important that your media server has a well-organized file and folder structure. Along with generally easier file and folder management.

```
data
├── torrents
│   ├── movies
│   ├── music
│   └── tv
├── usenet
│   ├── incomplete
│   └── complete
│       ├── movies
│       ├── music
│       └── tv
└── media
    ├── movies
    ├── music
    └── tv
```

- For more info https://trash-guides.info/File-and-Folder-Structure

## User Permissions

Each container on your media server needs access to media files and configuration folders. Recommend setting up with, folders `775` and files `664`.
This ensures that when containers create or modify files, they remain accessible to other containers and to your user account without manual intervention.

## Hard Links Usage

The server uses hard link to efficiently manage files without duplicating data. By referencing the same file content through multiple paths, we reduce storage usage and improve performance during updates or backups. This approach ensures consistency across linked files while keeping operations lightweight and reliable.
To verify if a file is hard-linked, you can use:

```bash
ls -al /path/to/your/download/location/
```

The output will be list of all files, On the left side the number after the permissions is greater than 1 its hardlinked

```bash
-rw-r--r-- 2 user user ... 'file 1' ✔️ hardlinked
-rw-r--r-- 1 user user ... 'file 2' ❌ not hardlinked
-rw-r--r-- 3 user user ... 'file 3' ✔️ hardlinked
```

## Container Bridge Network

Docker containers network is isolated by default, which prevents cross-communication between services.
We'll setup a custom bridge network: `myservernet - 10.10.0.0/24`
This network allows containers to resolve each other by name and communicate internally without exposing their ports to the host.

## Getting Started

1.  Clone this repository:

```bash
git clone https://github.com/liadVax/MediArrServer.git
cd media_server
```

2. Create custom Docker network:

```bash
docker network create --driver bridge --subnet 10.10.0.0/24 myservernet
```

3. Create data folders at preferred directory:

```bash
mkdir -p {torrents/{movies,music,tv},usenet/{incomplete,complete/{movies,music,tv}},media/{movies,music,tv}}
```

4. Setup data folder permissions:

```bash
sudo chown -R $USER:$USER /data
sudo chmod -R a=,a+rX,u+w,g+w /data
```

5. Enter each service folder, setup the .env, docker-compose.yaml and then:

```bash
docker compose up -d
```

6. Access each service via browser using your server’s IP and defined ports.

---

## Helpful Guides and Sources

- https://trash-guides.info
- https://wiki.servarr.com
