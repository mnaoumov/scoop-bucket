# mnaoumov's Scoop Bucket

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?logo=buy-me-a-coffee&logoColor=black)](https://www.buymeacoffee.com/mnaoumov)

Personal [Scoop](https://scoop.sh/) bucket for apps not available in the official buckets.

## Usage

```powershell
scoop bucket add mnaoumov https://github.com/mnaoumov/scoop-bucket
scoop install mnaoumov/<app-name>
```

## Available packages

| Package                                                          | Description                                                     |
|------------------------------------------------------------------|-----------------------------------------------------------------|
| [b2-cli](bucket/b2-cli.json)                                    | Backblaze B2 Command Line Tool                                  |
| [foxit-pdf-editor](bucket/foxit-pdf-editor.json)                | Foxit PDF Editor Pro (portable)                                 |
| [headless-run](bucket/headless-run.json)                      | Run console programs without a visible window, preserving exit codes |
| [jb-videometadata-lrplugin](bucket/jb-videometadata-lrplugin.json) | Lightroom plugin for writing IPTC metadata into video files  |
| [language-indicator](bucket/language-indicator.json)             | Visual keyboard layout indicator near text cursor               |
| [lr-copy-to-clipboard](bucket/lr-copy-to-clipboard.json)        | Lightroom export plugin that copies photos to clipboard         |
| [mremoteng](bucket/mremoteng.json)                              | Multi-Remote Next Generation connection manager                 |
| [qtranslate-ahatem](bucket/qtranslate-ahatem.json)              | Open-source QTranslate rewrite with bundled Java                |
| [throttlestop](bucket/throttlestop.json)                        | CPU throttling and undervolting tool                            |
| [vuescan](bucket/vuescan.json)                                  | Scanner software with advanced features (portable)              |

## Updating

```powershell
scoop update mnaoumov
scoop update *
```

Manifests include `checkver` and `autoupdate` fields where possible.

## See also

| Project | Features | How `mnaoumov's Scoop Bucket` differs |
| --- | --- | --- |
| [`DEV-tools`](https://github.com/anderlli0053/DEV-tools) | Large community bucket of development tools, utilities and everyday apps; automated updates through GitHub Actions; carries `foxit-pdf-editor`, `qtranslate` and `throttlestop` | Overlaps on three apps; this bucket adds `b2-cli`, `headless-run`, `language-indicator`, the Lightroom plugins and `vuescan`, and keeps a small, hand-picked set |
| [`Extras`](https://github.com/ScoopInstaller/Extras) | Official Scoop bucket for apps outside `Main`; scheduled automatic updates; manifest tests on every pull request; carries `mremoteng` and `throttlestop` | Overlaps on two apps, with the same upstream binaries; this bucket adds apps `Extras` does not carry, such as Foxit PDF Editor, VueScan and Language Indicator |
| [`Extras-Plus`](https://github.com/Scoopforge/Extras-Plus) | Community supplement to `Extras`; carries `texlive` | Overlaps on `texlive`; otherwise a different set of apps |
| [`Main`](https://github.com/ScoopInstaller/Main) | Default Scoop bucket for command-line tools; scheduled automatic updates; carries `b2`, the same Backblaze B2 command-line tool | Overlaps on the Backblaze B2 command-line tool, published here as `b2-cli`; this bucket also carries GUI apps, which `Main` does not accept |

Last searched for similar projects on 2026-11-27.

## Filing an issue (for AI agents and humans)

Open issues through the [issue forms](https://github.com/mnaoumov/scoop-bucket/issues/new/choose), not as blank issues.

Filing from the CLI or the API (`gh issue create --body`, or an AI agent filing for you) skips the form, and `gh issue create --template` cannot load an issue form. In that case, open the matching form in [`.github/ISSUE_TEMPLATE/`](https://github.com/mnaoumov/scoop-bucket/tree/HEAD/.github/ISSUE_TEMPLATE), copy every field as a `### <label>` heading in the form's order, and fill in each one. Always state the version you used and your operating system.
