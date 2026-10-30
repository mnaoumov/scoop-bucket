# mnaoumov's Scoop Bucket

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

## Filing an issue (for AI agents and humans)

Open issues through the [issue forms](https://github.com/mnaoumov/scoop-bucket/issues/new/choose), not as blank issues.

Filing from the CLI or the API (`gh issue create --body`, or an AI agent filing for you) skips the form, and `gh issue create --template` cannot load an issue form. In that case, open the matching form in [`.github/ISSUE_TEMPLATE/`](https://github.com/mnaoumov/scoop-bucket/tree/HEAD/.github/ISSUE_TEMPLATE), copy every field as a `### <label>` heading in the form's order, and fill in each one. Always state the version you used and your operating system.
