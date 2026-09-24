# Home Lab Setup

## Environment

- Cloud Provider: AWS
- Region: eu-north-1 (Stockholm)
- Operating System: Ubuntu 24.04 LTS
- Compute: Amazon EC2
- Container Runtime: Docker
- Reverse Proxy: Caddy
- Application: OWASP Juice Shop v20.1.1
- HTTPS: Let's Encrypt via Caddy

## Network Configuration

The EC2 Security Group allows:

- SSH: TCP 22
- HTTP: TCP 80
- HTTPS: TCP 443

The Juice Shop container itself is bound only to:

127.0.0.1:3000

External access is provided through Caddy.

## Docker

Docker was installed and enabled as a system service.

The Juice Shop image used:

bkimminich/juice-shop:v20.1.1

Container configuration:

- Container name: juice-shop
- Internal port: 3000
- Host binding: 127.0.0.1:3000
- Restart policy: unless-stopped

## Caddy

Caddy v2.11.4 was installed and configured as a systemd service.

Caddy provides:

- Reverse proxy
- Automatic HTTPS
- HTTP to HTTPS redirection
- Let's Encrypt certificate management

## Domain

The lab uses an sslip.io hostname mapped to the EC2 public IPv4 address.

Example:

16-170-37-185.sslip.io

## Validation

The following checks were performed successfully:

- Docker service active
- Juice Shop container running
- Local Juice Shop HTTP response: 200 OK
- Caddy service active
- HTTPS certificate obtained successfully
- HTTPS endpoint returned HTTP/2 200
- Juice Shop accessible through the HTTPS endpoint

## Purpose

This environment is intended for authorized cybersecurity learning, web application security practice, and controlled testing.
