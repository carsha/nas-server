# NAS Server

Simple server for media streaming, requesting & downloading.

## VPN Usage

This repository is based upon a mullvad vpn provider, however Gluetun supports a wide range of providers. You can find instructions at the [gluetun-wiki](https://github.com/qdm12/gluetun-wiki/tree/main/setup/providers) and make the required modifications to `core/gluetun.yml`.

## Initial Setup

> NOTE: Initial logins to the *arr applications will prompt to configure authentication settings. Use defaults and set a username/password.

1. Define all values in `.env` (see `env.example`)
2. Run all containers via `docker-compose up`
3. Obtain the temporary username/password from the qbittorrent container logs
4. Launch [qBittorrent](http://localhost:8080/)
5. Navigate to Tools > Options > Web UI and set a new username and password
6. Launch [Radarr](http://localhost:7878/)
7. Navigate to Settings > Media Management, click the **Add Root Folder** button and add /data
8. Navigate to Settings > Download Clients and add a qBittorrent client (enter the username/password you set in step 4)
9. Navigate to Settings > General and make a note of the API Key
10. Launch [Sonarr](http://localhost:8989/) and repeat steps 7 to 9
11. Launch [Prowlarr](http://localhost:9696/) 
12. Navigate to Settings > Apps and add Radarr & Sonarr, using the API keys you took note of earlier.
13. Navigate to Settings > Indexers and add a FlareSolverr indexer proxy with  the below details

| Tags  | Host                   |
| ----- | ---------------------- |
| flare | http://localhost:8191/ |
14. Navigate to Indexers and add your preferred indexers (I'd recommend EZTV & YTS at minimum). 

> If you add any indexers which utilise Cloudflare/DDoS-Guard protection, be sure to tag them with `flare` to enable proxying via flaresolverr.

