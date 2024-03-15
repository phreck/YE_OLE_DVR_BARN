# YE OLE HOME DVR DOCUMENTATION OF PHRECK

*So you want to do stuff at home huh? So you like having high quality, hard to find, quirky shit available to watch wherever, whenever huh?*

**So you decide to make some shit for yourself.**

## Required Services

- transmission-openvpn
- prowlarr
- sonarr
- radarr
- bazarr
- flaresolverr
- tautulli
- overseerr
- unpackerr

## Things to watch out for

- Ensure youre using the network_mode: "service:transmission-openvpn" for all containers that you require VPN access for.
- Ensure that you review all config variables. Ive added a few placeholders as needed.
- Remember, these docker-compose files and configs within are what have worked for me with minimal effort. Dont expect magic.
- RTFM you nerds.

## Things to know

- There are multiple docker-compose files here due to use of a NAS and other compute to run services
- You can likely combine these docker-compose files as you wish, as long as you consider volume configurations appropriately
- Beware of the NFS mount configurations, and kill them with prejudice if you aint usin that trash
- DFIU you savages.

## PS

- Im absolutely positive you can do this better than me
- Im 100 percent sure ive mucked something up
- Im 1000 percent sure that you can shut the fuck up

### transmission-openvpn

OPENVPN and Transmission BT Client. Well maintained and frequent development. Vast variety of VPN providers natively supported and available through simple config in dockerfile etc... A single container that provides Torrent Client with web interface as well as RTC/API access to the internal network, and an internal facing web proxy to point anything to that you would like to use the VPN as egress.

Of note, use the docker host/container network magic to force other services to transit the VPN and not the public internet.

Github: <https://github.com/haugene/docker-transmission-openvpn>
Dockerhub: <https://hub.docker.com/r/haugene/transmission-openvpn/>
Docs: <https://haugene.github.io/docker-transmission-openvpn/>

### prowlarr

Simple/Easy to use and configure indexer management and configuration. Prowlarr pushes indexer configs etc... to clients like sonarr and radarr and keeps them sync'd. Very extensible and well documented if you should choose to do anything complex. Prowlarr has Search capabolities built in as well from the web app which will search cached records as well as across configured indexers etc... API endpoints and RSS Feeds queriable per indexer also available.

Github: <https://github.com/Prowlarr/Prowlarr>
linuxserver.io: linuxserver/prowlarr:latest
Docs: <https://prowlarr.com/>
      <https://docs.linuxserver.io/images/docker-prowlarr/>

### sonarr

A television collection manager for usenet/BT use. Capable of monitoring RSS feeds, interfacing with usenet/BT clients for download management, grabbing, sorting and renaming files - as well as video quality management of new and existing files. Same functionality as radarr, but for television shows. Natively integrates with prowlarr for indexer magic.

Github: <https://github.com/sonarr/sonarr>
linuxserver.io: linuxserver/sonarr:latest
Docs: <https://wiki.servarr.com/en/sonarr>
      <https://docs.linuxserver.io/images/docker-sonarr/>

### radarr

A movie collection manager for usenet/BT use. Capable of monitoring RSS feeds, interfacing with usenet/BT clients for download management, grabbing, sorting and renaming files - as well as video quality management of new and existing files. Same functionality as sonarr, but for movies. Natively integrates with prowlarr for indexer magic.

Github: <https://github.com/radarr/radarr>
linuxserver.io: linuxserver/radarr:latest
Docs: <https://wiki.servarr.com/en/radarr>
      <https://docs.linuxserver.io/images/docker-radarr/>

### bazarr

You like having captions available? Do you like having consistent styling for your captions? Do you like having the captions that match the timings of your source? Then use this. companion application to Sonarr and Radarr. It can manage and download subtitles based on your requirements. You define your preferences by TV show or movie and Bazarr takes care of everything for you. Fully integrates with radarr/sonarr/prowlarr for extra easy install and use.

Github: <https://github.com/morpheus65535/bazarr>
linuxserver.io: linuxserver/bazarr:latest
Docs: <https://www.bazarr.media/>

### flaresolverr

Captcha management. Works to bypass cloudflare and DDoS-GUARD protection via wrangling user requests through its proxy. You may not need this. Doesnt hurt to have up though.

Github: <https://github.com/FlareSolverr/FlareSolverr>
Dockerhub: flaresolverr/flaresolverr:latest
Docs: <https://github.com/FlareSolverr/FlareSolverr?tab=readme-ov-file#readme>

### tautulli

Useful for plex server stats and management. Not a requirement.

Github: <https://github.com/Tautulli/Tautulli>
linuxserver.io: linuxserver/tautulli:latest
Docs: <https://github.com/Tautulli/Tautulli/wiki>

### overseerr

Way more fun to browse, search and download media with overseerr. Also allows for multiple users, request tagging and request management. Integrates with radarr, sonarr, plex and a variety of other tools.

Github: <https://github.com/sct/overseerr>
Dockerhub: sctx/overseerr:latest
Docs: <https://overseerr.dev/>
      <https://docs.overseerr.dev/>

### unpackerr

Deals with archived files. Extracts and deposits file for retrieval by sonarr/radarr etc...

Github: <https://github.com/Unpackerr/unpackerr>
Dockerhub: golift/unpackerr:latest
Docs: <https://unpackerr.zip/>
      <https://unpackerr.zip/docs/introduction>
