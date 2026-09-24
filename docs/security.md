# Security Configuration

## Lab Scope

This environment is a controlled cybersecurity laboratory intended for authorized testing and security education.

The OWASP Juice Shop application is intentionally vulnerable and is used as the practice target.

## AWS Security Group

Inbound access is limited to the required services:

| Service | Protocol | Port | Purpose |
|---|---|---:|---|
| SSH | TCP | 22 | Administrative access |
| HTTP | TCP | 80 | HTTP traffic and ACME validation |
| HTTPS | TCP | 443 | Public web access |

No direct inbound access to Docker port 3000 is required.

## Application Exposure

Juice Shop is bound to:

127.0.0.1:3000

This prevents direct external access to the application port.

Caddy acts as the public-facing reverse proxy.

Traffic flow:

Internet
  |
  v
AWS Security Group
  |
  v
Caddy :443
  |
  v
127.0.0.1:3000
  |
  v
OWASP Juice Shop

## HTTPS

Caddy automatically manages the TLS certificate using Let's Encrypt.

HTTP traffic is redirected to HTTPS.

## Security Principles

The lab follows these principles:

- Expose only required network ports.
- Keep the application container off the public interface.
- Use HTTPS for external access.
- Use a dedicated intentionally vulnerable application as the practice target.
- Keep testing within authorized scope.
- Never place credentials, private keys, access tokens, or secrets in the Git repository.

## Important

The public endpoint should be treated as a security-training environment.

Do not use real credentials, sensitive personal information, or production data inside the Juice Shop environment.
