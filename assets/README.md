# Assets

The project icon. The product name is still a working title, so the icon
has no lettering and survives a rename.

| File | Use |
|---|---|
| `icon.svg` | The app icon: the mark on a dark tile. Use it for launchers, the desktop client, the phone app and the browser favicon. |
| `icon-mark.svg` | The mark alone, on a transparent background, for light surfaces such as documents. |
| `icon-symbolic.svg` | A one-colour 16 px version that uses `currentColor`, for the Linux tray and GNOME symbolic icons. |

## The idea

A home with a voice inside it: one assistant for the whole household, kept
in your home. The colours come from the earlier voice assistant: warm
near-black surfaces, amber for the assistant and mint for the person. The
four amber bars are the assistant speaking and the mint bar is you.

| Colour | Hex | Earlier token |
|---|---|---|
| Tile, top | `#21211c` | `--color-surface-2` |
| Tile, bottom | `#0e0f0c` | `--color-bg` |
| House | `#ebe8dd` | `--color-ink` |
| Assistant | `#f2af48` | `--color-voice` |
| Person | `#82dbc9` | `--color-you` |

The visual identity is not decided yet (see
[the visual design](../docs/design/visual/README.md)). If it starts fresh
instead of keeping amber and mint, only these colours change.

No PNG exports yet. Generate them from `icon.svg` when a client needs them.
