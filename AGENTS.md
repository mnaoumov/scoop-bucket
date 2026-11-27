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

## L4. Automated updates

- `.github/workflows/excavator.yml` runs Scoop's `checkver` and `autoupdate` every 4 hours (and on `workflow_dispatch`) through `ScoopInstaller/GithubActions`
- It commits each updated manifest as `github-actions[bot]` and pushes straight to `main` with `GITHUB_TOKEN` (`contents: write`), so `main` moves on its own: pull before you push
- `main` has no branch protection or ruleset; adding one that blocks direct pushes would stop these updates
- A manifest without `autoupdate` is only reported, never changed

## L5. Manifest tests

- `.github/workflows/ci.yml` runs `bin/test.ps1` (Scoop's Pester bucket tests, through `Scoop-Bucket.Tests.ps1`) on every push to `main` and every pull request, in `powershell` and `pwsh`; `.github/workflows/pull_request.yml` runs Scoop's pull request handler
- In CI the schema test covers only the manifests changed by the last commit; the file style test covers every file: UTF-8 without BOM, CRLF (`.gitattributes` sets `eol=crlf`), a final newline, no trailing whitespace, and spaces for indentation
- Before you commit a manifest, run `bin\formatjson.ps1` and `bin\test.ps1` from a PowerShell session. Never use `pwsh -File bin\test.ps1`, because its `#Requires -Modules` lines make it exit 0 under `-File` even when tests fail
- The style test reads every file on disk, including gitignored ones, so locally it also fails on tool-local files such as `.claude/settings.local.json` and `.codex/config.toml`. CI never checks those out, so treat those two lines as noise
- An empty array such as `"bin": []` fails the schema: leave the field out instead
- The `bin/` scripts and the two workflows are copied from `ScoopInstaller/BucketTemplate` (Unlicense)
