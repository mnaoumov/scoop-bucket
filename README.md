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
| [throttlestop](bucket/throttlestop.json)                        | CPU throttling and undervolting tool                            |
| [vuescan](bucket/vuescan.json)                                  | Scanner software with advanced features (portable)              |

## Updating

```powershell
scoop update mnaoumov
scoop update *
```

Manifests include `checkver` and `autoupdate` fields where possible.
