# Pi-hole Policy Lists

Service-based allowlists for a segmented Pi-hole deployment.

## Structure

- `lists/apple-core-default.txt` — Apple domains that should usually stay global
- `lists/apple-trusted.txt` — Apple app/CDN domains for trusted clients
- `lists/microsoft-trusted.txt` — Microsoft auth and productivity domains for trusted clients
- `lists/bitwarden-trusted.txt` — Bitwarden browser/app domains
- `lists/cdn-core-default.txt` — Core CDN domains that commonly reduce breakage
- `docs/pihole-policy-plan.md` — recommended group model and deployment notes

## Suggested Pi-hole groups

- `Default` — global baseline
- `Trusted` — personal/admin devices
- `Infrastructure` — servers and core services
- `Kids` — family devices with moderate filtering
- `IoT` — aggressive filtering, allow only what is needed
- `Guest` — aggressive filtering

## Recommended assignments

### Default group
Use these lists globally:
- `apple-core-default.txt`
- `cdn-core-default.txt`

### Trusted group
Use these lists for your iPhone, laptop, Apple TVs, and similar devices:
- `apple-trusted.txt`
- `microsoft-trusted.txt`
- `bitwarden-trusted.txt`

## Notes

1. Remove conflicting deny entries before testing allow rules.
2. Prefer exact domains first. Use regex only when you intentionally want wildcard coverage.
3. Keep comments and list ownership documented in Git.
