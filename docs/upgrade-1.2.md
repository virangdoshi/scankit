# Upgrade from 1.1.x → 1.2.0

## Highlights

- **Scan profiles**: `profile: minimal | standard | audit | soak`
- **Scan-only workflow**: `reusable-security-scan.yml` — read-only permission ceiling
- **`.scankit.yml`**: repo config via `config-path` input
- **Optional DAST**: `enable-dast` + `dast-url` (staging only)
- **Notifications**: `enable-notifications` + `notification-webhook`
- **PR triage**: category grouping in sticky comment

## Pin bump

Replace your workflow SHA with the [v1.2.0](https://github.com/virangdoshi/scankit/releases/tag/v1.2.0) release commit:

```yaml
uses: YOUR_ORG/scankit/.github/workflows/reusable-security-full.yml@b9246b836e49f952795404d85ceb8e3c65281d7d
```

## New inputs (optional)

```yaml
with:
  profile: standard          # or minimal | audit | soak
  config-path: .scankit.yml  # optional repo config
  enable-dast: false
  dast-url: ""
  enable-notifications: false
  notification-webhook: ""
```

## Scan-only adoption

For teams that reject `contents: write`:

```yaml
uses: YOUR_ORG/scankit/.github/workflows/reusable-security-scan.yml@SHA
```

See [`templates/security-scan-only.yml`](../templates/security-scan-only.yml).

## Breaking changes

None for existing callers — defaults match 1.1 behavior (`profile` empty → `standard`).
