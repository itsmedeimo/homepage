# My Personal Homepage Configuration
A complete homepage configuration of [Homepage](https://gethomepage.dev/) for anyone to use as an example to create their own homepage.

I have included my [docker-compose.yaml](/docker/docker-compose.yaml) deployment that I used on my Dockge to deploy my Homepage instance and also an [example.env](/docker/.env) file with all my environment variables that are passed to the container. 

```yaml
version: "3.3"
services:
  homepage:
    image: ghcr.io/gethomepage/homepage:latest
    container_name: homepage
    ports:
      - 3000:3000
    env_file: ./.env # use .env
    volumes:
      - ./config:/app/config # Make sure your local config directory exists
      - /var/run/docker.sock:/var/run/docker.sock # (optional) For docker integrations, see alternative methods
    environment:
      PUID: $PUID # read them from .env
      PGID: $PGID # read them from .env
networks:
  dockge_default:
    external: true
```

## Configuration
The files are located inside the [config folder](/config)
### Settings
[settings.yaml](/config/settings.yaml)

### Bookmarks
[bookmarks.yaml](/config/bookmarks.yaml)

### Services
[services.yaml](/config/services.yaml)

### Widgets
[widgets.yaml](/config/widgets.yaml)