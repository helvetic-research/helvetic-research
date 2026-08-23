# Security Policy

## Reporting a vulnerability

Please report suspected security issues privately to
**[security@helveticresearch.com](mailto:security@helveticresearch.com)** or through a private
GitHub security advisory. Do not open a public issue for an undisclosed vulnerability.

Please include reproduction steps and the affected endpoint or component. We aim to acknowledge
reports within three business days and provide a remediation timeline after triage.

## In scope

- The hosted MCP endpoint and web application
- Google sign-in and MCP OAuth flows
- Account and research-record isolation
- Report and result access controls
- Vulnerabilities that could affect confidentiality, integrity, or authentication

## Out of scope

- Volumetric denial-of-service against the current free hosting tier
- Findings that require a previously compromised user device or browser extension
- Availability or correctness defects inside third-party market-data providers
- Social-engineering attempts against users or staff

## Current controls

- Google-only customer identity; no customer passwords are stored
- OAuth with PKCE, short-lived authorization codes, rotating refresh tokens, and revocation
- Tokens and authorization codes stored only as hashes
- Per-account ownership checks for stored research and exports
- Rate limiting, workload ceilings, and a single-heavy-job concurrency guard
- Security headers including CSP, HSTS on HTTPS, frame denial, MIME sniffing protection,
  referrer policy, and permissions policy
- Structured request and tool-call audit events
- Automated secret scanning, dependency auditing, and baseline web security scanning
- Production refusal to start with the development secret on a public HTTPS URL

## Product boundary

Helvetic Research does not execute trades or connect to brokers. Arbitrary client code is not run
inside the hosted web/MCP process. Any future code-execution capability must use a separately
isolated worker without access to application secrets, customer storage, or unrestricted network
resources.

## Current limitations

The current service is pre-institutional and uses free-tier infrastructure. It does not promise an
uptime SLA. A formal third-party penetration test and compliance review are recommended before use
by institutional teams.

For public security and privacy information, see:

- [Security overview](https://helveticresearch.com/security)
- [Privacy policy](https://helveticresearch.com/privacy)
- [Terms of use](https://helveticresearch.com/terms)
