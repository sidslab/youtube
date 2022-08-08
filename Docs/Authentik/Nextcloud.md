```
---
version: "2"
services:
  nextcloud:
    image: linuxserver/nextcloud:latest
    container_name: nextcloud
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=${TZ}
    volumes:
      - ./config:/config
    ports:
      - ${PORT}:443
    restart: unless-stopped
    depends_on:
      - nextcloud_db
  nextcloud_db:
    image: linuxserver/mariadb:latest
    container_name: nextcloud_db
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
      - TZ=${TZ}
      - MYSQL_DATABASE=nextcloud_db
      - MYSQL_USER=nextcloud
      - MYSQL_PASSWORD=${DATABASE_PASSWORD}
    volumes:
      - ./nextcloud-db:/config
    restart: unless-stopped

```
`.env`

```
PUID=1000
PGID=1000
TZ=America/New_York
PORT=8443
MYSQL_ROOT_PASSWORD=<change>
DATABASE_PASSWORD=<change>
```
