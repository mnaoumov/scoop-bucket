# Scoop Bucket

## Filing an issue (for AI agents and humans)

Open issues through the [issue forms](https://github.com/mnaoumov/scoop-bucket/issues/new/choose), not as blank issues.

Filing from the CLI or the API (`gh issue create --body`, or an AI agent filing for you) skips the form, and `gh issue create --template` cannot load an issue form. In that case, open the matching form in [`.github/ISSUE_TEMPLATE/`](https://github.com/mnaoumov/scoop-bucket/tree/HEAD/.github/ISSUE_TEMPLATE), copy every field as a `### <label>` heading in the form's order, and fill in each one. Always state the version you used and your operating system.

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
