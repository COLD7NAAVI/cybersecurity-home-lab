# Cybersecurity Home Lab

An AWS-based cybersecurity practice environment built for authorized security testing and web application security learning.

## Lab Architecture

```text
Internet
   │
   ▼
AWS EC2
   │
   ├── Ubuntu 24.04
   │
   ├── AWS Security Group
   │      ├── SSH :22
   │      ├── HTTP :80
   │      └── HTTPS :443
   │
   ├── Caddy v2.11.4
   │      └── Automatic HTTPS / Let's Encrypt
   │
   └── Docker
          │
          └── OWASP Juice Shop v20.1.1
                 │
                 └── localhost:3000
