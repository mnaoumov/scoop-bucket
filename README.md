# mnaoumov's Scoop Bucket

Personal [Scoop](https://scoop.sh/) bucket for apps not available in the official buckets.

## Usage

```powershell
scoop bucket add custom https://github.com/mnaoumov/scoop-bucket
scoop install custom/<app-name>
```

## Available packages

| Package                                          | Description                                       |
|--------------------------------------------------|---------------------------------------------------|
| [b2-cli](bucket/b2-cli.json)                     | Backblaze B2 Command Line Tool                    |
| [language-indicator](bucket/language-indicator.json) | Visual keyboard layout indicator near text cursor |
| [lightroom-plugins](bucket/lightroom-plugins.json)   | Lightroom plugins: jb_videometadata + copy-to-clipboard |
| [mremoteng](bucket/mremoteng.json)               | Multi-Remote Next Generation connection manager   |
| [throttlestop](bucket/throttlestop.json)         | CPU throttling and undervolting tool               |

## Updating

```powershell
scoop update custom
scoop update *
```

Manifests include `checkver` and `autoupdate` fields where possible.
