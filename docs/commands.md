# Lab Commands

## Docker

Check Docker version:

sudo docker --version

Check Docker service:

sudo systemctl status docker --no-pager

List Docker images:

sudo docker images

List running containers:

sudo docker ps

List containers with useful information:

sudo docker ps --format 'table {{.Names}}\t{{.Image}}\t{{.Status}}\t{{.Ports}}'

## OWASP Juice Shop

Run Juice Shop:

sudo docker run -d \
  --name juice-shop \
  --restart unless-stopped \
  -p 127.0.0.1:3000:3000 \
  bkimminich/juice-shop:v20.1.1

Test locally:

curl -I http://127.0.0.1:3000/

Check port:

sudo ss -lntp | grep ':3000' || true

## Caddy

Check Caddy version:

caddy version

Check Caddy service:

sudo systemctl status caddy --no-pager

Validate configuration:

sudo caddy validate --config /etc/caddy/Caddyfile

Format configuration:

sudo caddy fmt --overwrite /etc/caddy/Caddyfile

Reload configuration:

sudo systemctl reload caddy

Check service state:

sudo systemctl is-active caddy

View recent logs:

sudo journalctl -u caddy --since "2 minutes ago" --no-pager

## HTTPS Validation

Test the HTTPS endpoint:

curl -I https://16-170-37-185.sslip.io

Expected result:

HTTP/2 200

## Git

Check repository state:

git status

Stage documentation:

git add .

Commit:

git commit -m "docs: update home lab documentation"

Push:

git push origin main
