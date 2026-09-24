# Lessons Learned

## AWS Infrastructure

The lab demonstrated how to deploy a small cybersecurity environment on an EC2 instance and control external access through an AWS Security Group.

## Docker

The application was isolated inside a Docker container rather than being installed directly on the host.

Binding the application to 127.0.0.1:3000 allowed the reverse proxy to provide external access without exposing port 3000 directly.

## Reverse Proxy

Caddy simplified the deployment by providing reverse proxy functionality and automatic HTTPS certificate management.

## TLS

Let's Encrypt certificate issuance was successfully validated through the HTTP-01 challenge.

The final HTTPS endpoint returned HTTP/2 200.

## Troubleshooting

The deployment required validating each layer independently:

1. Verify Docker installation.
2. Verify Docker service.
3. Pull the Juice Shop image.
4. Start the container.
5. Test Juice Shop locally.
6. Verify port 3000.
7. Configure Caddy.
8. Validate Caddy configuration.
9. Reload Caddy.
10. Verify certificate issuance.
11. Test the public HTTPS endpoint.

This layered validation approach made it easier to identify configuration problems.

## Cybersecurity Practice

The completed environment provides a controlled target for learning web application security concepts using OWASP Juice Shop.

Future work can include documenting individual Juice Shop challenges, testing methodologies, findings, evidence, and remediation concepts.
