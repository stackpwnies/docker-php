# PHP Docker Image

This is a Docker image built to be run via docker-compose, and provides:

- Nginx webserver
- rocket-nginx for those using WordPress
- A sane PHP-FPM install

## Environment variables

### APP_HOSTNAME

This should be set to whatever hostnames you are serving. Follow the [Traefik matchers format](https://docs.traefik.io/basics/#matchers).

## Volumes

The <project_name>_data volume is mapped to /applications inside the container.