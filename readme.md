# Media Server - \*arr Stack

## Overview

This repository is my complete home media server using *arr stack.
“Lidarr, Prowlarr, Radarr, Readarr, Sonarr, and Whisparr are collectively referred to as "*arr" or "\*arrs". They are designed to automatically grab, sort, organize, and monitor your Music, Movie, E-Book, or TV Show collections for Lidarr, Radarr, Readarr, Sonarr, and Whisparr; and to manage your indexers and keep them in sync with the aforementioned apps for Prowlarr.”

### Services

| Name         | Description                                  | Port | Status | Notes                                              |
| ------------ | -------------------------------------------- | :--: | :----: | -------------------------------------------------- |
| Dockge       | Docker image management interface            |      |   ✔️   |                                                    |
| Homepage     | Personalized dashboard for server info       |      |   ✔️   |                                                    |
| Flaresolverr | Solves Cloudflare protections for indexers   |      |   ✔️   | Needed by some indexers                            |
| qBittorrent  | Torrent client                               |      |   ✔️   |                                                    |
| NZBGet       | Usenet downloader                            |      |   ✔️   |                                                    |
| Plex         | Media server for movies & TV                 |      |   ✔️   |                                                    |
| Jellyfin     | Media server for movies, TV, music           |      |   ❌   | `Plex` gave me better user experience              |
| Immich       | Personal photo/video backup solution         |      |   ✔️   |                                                    |
| Sonarr       | TV show manager & downloader                 |      |   ✔️   |                                                    |
| Radarr       | Movie manager & downloader                   |      |   ✔️   |                                                    |
| Lidarr       | Music collection manager                     |      |   ✔️   |                                                    |
| Prowlarr     | Indexer manager for Sonarr/Radarr/Lidarr     |      |   ✔️   |                                                    |
| Bazarr       | Subtitles management service for movies & TV |      |   ❌   | Didn't worked properly, Had problem with providers |

### Prerequisites

- **Operating System:** Ubuntu 24.04.3
- **Docker & Docker Compose** installed and configured
- **Network setup**: devices on same LAN

### File and Folder Structure

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

### User Permissions

Each container on your media server needs access to media files and configuration folders. Recommend setting up with, folders `775` and files `664`.
This ensures that when containers create or modify files, they remain accessible to other containers and to your user account without manual intervention.

### Container Bridge Network

When running multiple containers (Radarr, Sonarr, qBittorrent, etc.), they need to communicate directly with each other to exchange data and API calls.  
By default, Docker Compose creates an isolated network per stack, which prevents cross-communication between services in different Compose files.
To fix this, I defined a shared custom bridge network: `myservernet - 10.10.0.0/24`
This network allows containers to resolve each other by name (e.g., `qbittorrent`, `radarr`, `sonarr`) and communicate internally without exposing their ports to the host.

## Getting Started

1.  Clone this repository:

```
git clone https://{ENTER URL}.git
cd media_server
```

2. Create the custom Docker network:

```
docker network create --driver bridge --subnet 10.10.0.0/24 myservernet
```

3. Create folders at preferred directory:

```
mkdir -p {torrents/{movies,music,tv},usenet/{incomplete,complete/{movies,music,tv}},media/{movies,music,tv}}
```

4. Adjust data folder permissions:

```
sudo chown -R $USER:$USER /data
sudo chmod -R a=,a+rX,u+w,g+w /data
```

5. Enter each service folder, review its .env.example or .env, set your values, then:

```
docker compose up -d
```

6. Access each service via browser using your server’s IP and defined ports.
