```
---
version: "2.1"
services:
  sonarr:
    image: lscr.io/linuxserver/sonarr:latest
    container_name: sonarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/New_York
    volumes:
      - ./data:/config
      - ./tvseries:/tv #optional
      - ./downloadclient-downloads:/downloads #optional
    ports:
      - 8989:8989
    restart: unless-stopped
``