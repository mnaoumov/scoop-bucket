# Scoop Bucket

## L1. Manifest format

- Each manifest is a JSON file in `bucket/`
- `url` field must use hardcoded version (not `$version` — that only works in `autoupdate`)
- `autoupdate.url` uses `$version` placeholder for auto-update support
- Include `hash` when available (SHA256)
- Include `checkver` to detect new upstream releases

## L2. Hosted assets

- For apps without a stable download URL, host the archive as a GitHub release on this repo
- Tag releases as `v<version>` (e.g., `v1.0.0`)

## L3. Naming

- Manifest filenames: kebab-case (e.g., `b2-cli.json`, `language-indicator.json`)
