# Ubuntu VNC Container Compose

## Launching steps

1. Install docker and openssl, e.g.
``
apt install docker.io docker-compose openssl
``

2. Create SSL certificate, e.g.
``
mkdir -p ssl
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ssl/nginx.key -out ssl/nginx.crt
``

3. Edit environments in docker-compose.yml
``
environment:
  - VNC_PASSWORD= <your password>
volume:
  - type: bind
    source: <your ssl directory>
    target: /etc/nginx/ssl
``

4. Start the service with docker-compose
``
docker-compose up -d
``
