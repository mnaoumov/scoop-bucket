# mnaoumov's Scoop Bucket

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?logo=buy-me-a-coffee&logoColor=black)](https://www.buymeacoffee.com/mnaoumov) [![CI](https://img.shields.io/github/actions/workflow/status/mnaoumov/scoop-bucket/ci.yml?branch=main&label=CI)](https://github.com/mnaoumov/scoop-bucket/actions/workflows/ci.yml) [![License](https://img.shields.io/github/license/mnaoumov/scoop-bucket)](https://github.com/mnaoumov/scoop-bucket/blob/main/LICENSE)

Personal [Scoop](https://scoop.sh/) bucket for apps not available in the official buckets, or not in the release channel this bucket carries.

## Usage

```powershell
scoop bucket add mnaoumov https://github.com/mnaoumov/scoop-bucket
scoop install mnaoumov/<app-name>
```

## Available packages

| Package | Description |
| --- | --- |
| [foxit-pdf-editor](bucket/foxit-pdf-editor.json) | Foxit PDF Editor Pro |
| [headless-run](bucket/headless-run.json) | Run console programs without a visible window, preserving exit codes |
| [jb-videometadata-lrplugin](bucket/jb-videometadata-lrplugin.json) | Lightroom plugin for writing IPTC metadata into video files |
| [language-indicator](bucket/language-indicator.json) | Visual keyboard layout indicator near text cursor |
| [lr-copy-to-clipboard](bucket/lr-copy-to-clipboard.json) | Lightroom export plugin that copies photos to clipboard |
| [mremoteng](bucket/mremoteng.json) | Multi-Remote Next Generation connection manager, nightly builds |
| [qtranslate](bucket/qtranslate.json) | QTranslate desktop translation tool by QuestSoft |
| [qtranslate-ahatem](bucket/qtranslate-ahatem.json) | Open-source QTranslate rewrite with bundled Java |
| [texlive](bucket/texlive.json) | TeX Live distribution, installed portable with the small scheme |
| [vuescan](bucket/vuescan.json) | Scanner software with advanced features (portable) |

### Apps also in the official buckets

| Package | Status | Why |
| --- | --- | --- |
| `mremoteng` | Kept | It tracks the nightly builds (1.78.x); `extras/mremoteng` tracks the stable release (1.76.x) |
| `b2-cli` | Retired on 2026-11-27 | `main/b2` ships the same binary at the same version; install it with `scoop install main/b2` |
| `throttlestop` | Retired on 2026-11-27 | `extras/throttlestop` is newer and downloads from the author's own host, TechPowerUp; install it with `scoop install extras/throttlestop` |

To move an install of a retired app over, uninstall the `mnaoumov` copy and install the official one. Back up `ThrottleStop.ini` from the ThrottleStop app folder first, because this bucket's manifest did not persist it.

## Updating

```powershell
scoop update mnaoumov
scoop update *
```

Manifests include `checkver` and `autoupdate` fields where possible. The [Excavator workflow](.github/workflows/excavator.yml) runs them every 4 hours and commits each manifest that has a newer upstream version.

Two manifests have a `checkver` but no `autoupdate`, because they install files hosted as releases of this repo rather than the upstream download:

1. `foxit-pdf-editor` installs the upstream installer plus a post-install overlay, `update.zip`, that the upstream does not publish.
2. `vuescan` installs a portable repackage of VueScan; the upstream offers only an installer.

For these two, the Excavator workflow reports a newer upstream version in its log but changes nothing; a new release has to be packaged and uploaded by hand. The `vuescan` repackage carries a fourth version part (`9.8.53.02`), so `checkver` reports it as different from the upstream's three-part version even when the two match.

## Testing

The [CI workflow](.github/workflows/ci.yml) runs Scoop's manifest tests on every push to `main` and every pull request, in both Windows PowerShell and PowerShell 7. The tests check each changed manifest against Scoop's schema, and every file for a UTF-8 encoding with no BOM, CRLF line endings, a final newline and no trailing whitespace. The [Pull Requests workflow](.github/workflows/pull_request.yml) also runs Scoop's pull request checks, and `/verify` in a pull request comment runs them again.

To run the same checks locally, install the `Pester` (5.2.0 or later) and `BuildHelpers` modules, then run the scripts from a PowerShell session:

```powershell
Install-Module Pester, BuildHelpers -Scope CurrentUser
.\bin\test.ps1              # manifest tests
.\bin\checkver.ps1          # check for newer upstream versions
.\bin\checkurls.ps1         # check that every download URL answers
.\bin\checkhashes.ps1       # download every file and check its hash
.\bin\formatjson.ps1        # format the manifests the way Scoop does
.\bin\missing-checkver.ps1  # list the manifests without checkver or autoupdate
```

The scripts call the copies in your Scoop installation, or in `$env:SCOOP_HOME` when that is set. Run `bin\test.ps1` from a session rather than through `pwsh -File`: under `-File`, PowerShell 7 drops its exit code, so a failing run would exit 0.

## See also

| Project | Features | How `mnaoumov's Scoop Bucket` differs |
| --- | --- | --- |
| [`DEV-tools`](https://github.com/anderlli0053/DEV-tools) | Large community bucket of development tools, utilities and everyday apps; automated updates through GitHub Actions; carries `foxit-pdf-editor` and `qtranslate` | Overlaps on two apps; this bucket adds `headless-run`, `language-indicator`, the Lightroom plugins and `vuescan`, and keeps a small, hand-picked set |
| [`Extras`](https://github.com/ScoopInstaller/Extras) | Official Scoop bucket for apps outside `Main`; scheduled automatic updates; manifest tests on every pull request; carries `mremoteng` (stable) and `throttlestop` | This bucket carries mRemoteNG's nightly channel instead, and apps `Extras` does not carry, such as Foxit PDF Editor, VueScan and Language Indicator |
| [`Extras-Plus`](https://github.com/Scoopforge/Extras-Plus) | Community supplement to `Extras`; carries `texlive` | Overlaps on `texlive`; otherwise a different set of apps |
| [`Main`](https://github.com/ScoopInstaller/Main) | Default Scoop bucket for command-line tools; scheduled automatic updates; carries `b2`, the Backblaze B2 command-line tool this bucket used to publish as `b2-cli` | No overlap left; this bucket carries GUI apps, which `Main` does not accept |

Last searched for similar projects on 2026-11-27.

## Filing an issue (for AI agents and humans)

Open issues through the [issue forms](https://github.com/mnaoumov/scoop-bucket/issues/new/choose), not as blank issues.

Filing from the CLI or the API (`gh issue create --body`, or an AI agent filing for you) skips the form, and `gh issue create --template` cannot load an issue form. In that case, open the matching form in [`.github/ISSUE_TEMPLATE/`](https://github.com/mnaoumov/scoop-bucket/tree/HEAD/.github/ISSUE_TEMPLATE), copy every field as a `### <label>` heading in the form's order, and fill in each one. Always state the version you used and your operating system.

## License

[MIT](LICENSE) © [Michael Naumov](https://github.com/mnaoumov/). The `bin/` scripts and the CI and pull request workflows are copied from [`ScoopInstaller/BucketTemplate`](https://github.com/ScoopInstaller/BucketTemplate), released under the [Unlicense](https://unlicense.org/).
