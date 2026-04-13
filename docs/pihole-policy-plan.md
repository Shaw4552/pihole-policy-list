# Pi-hole policy plan

## 1) Goal

Keep critical services working while still using segmented filtering by device trust level.

## 2) Group model

### Default
Use for global baseline rules that should apply everywhere.

Recommended:
- Apple core services
- Minimal CDN break-fix entries

### Trusted
Use for personal/admin devices that need fewer false positives.

Recommended:
- Apple app/CDN access
- Microsoft auth/productivity
- Bitwarden

### Infrastructure
Use for NAS, Pi-hole, Plex, monitoring, reverse proxy, and similar systems.

Recommended:
- Minimal blocking
- Add service-specific exceptions only when needed

### Kids
Moderate blocking. Add exceptions only for approved apps and school services.

### IoT
Aggressive blocking. Add vendor-specific exceptions only after testing.

### Guest
Aggressive blocking. Avoid broad allowlists.

## 3) Regex guidance

Use regex only when you really want wildcard coverage.

Examples:
- `(^|\\.)aaplimg\\.com$` for Apple CDN wildcard coverage
- `(^|\\.)captive\\.apple\\.com$` only if you need wildcard coverage for captive checks

## 4) Conflict rule

If a domain appears in both deny and allow, remove the deny entry first. Do not leave both in place and hope Pi-hole resolves it the way you want.

## 5) Change process

1. Add or edit the domain in the correct service list
2. Commit the change to Git
3. Update the hosted raw file URL in Pi-hole if needed
4. Run gravity update or refresh lists
5. Test from a device in the intended group
6. Document what changed and why
