# Security Policy

## Scope

HomeTrack is designed for **local, private, self-hosted use only**.

- It does not transmit data to any external server.
- It does not collect telemetry, crash reports, or usage analytics.
- It is not designed for exposure to the public internet without additional hardening
  (reverse proxy with TLS, firewall rules, etc.).

## Supported Versions

| Version | Supported |
|---|---|
| `0.1.x` (current) | ✅ |

## Reporting a Vulnerability

If you discover a security vulnerability, please **do not open a public GitHub issue**.

Instead, report it privately via one of these methods:

1. **GitHub private vulnerability reporting** (preferred):
   Go to the repository → Security tab → "Report a vulnerability".

2. **Email**: Send details to the repository maintainer. Check the GitHub profile
   for contact information.

Please include:
- A clear description of the vulnerability
- Steps to reproduce (proof of concept if possible)
- The potential impact
- Any suggested mitigations

You will receive an acknowledgement within **72 hours** and a status update within
**7 days**.

## Security Design Notes

- All user input is validated via Pydantic before reaching the database.
- The CRUD layer uses SQLAlchemy's parameterised query API exclusively.
- The SQLite database is created with `0600` permissions (owner read/write only).
- No secrets are hardcoded; all configuration comes from environment variables.
- The container runs as a non-root user (`UID 1000`).
