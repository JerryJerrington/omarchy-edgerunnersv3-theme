# Edgerunners V3 for Omarchy

A Cyberpunk Edgerunners inspired theme for [Omarchy](https://omarchy.org/),
ported from [JerryJerrington/omarchy-edgerunnersv2-theme](https://github.com/JerryJerrington/omarchy-edgerunnersv2-theme)
(the "Aether" palette) to the Omarchy 4.5 theme format.

Amplified for the desktop: the original periwinkle accent is promoted to
neon magenta, and the window border is a magenta -> cyan gradient that
carries through the whole Omarchy shell (popups, notifications, launcher,
lock screen). The yellow slot keeps the original dusty mauve (`#b88faa`)
for a moodier tone.

## Palette

| Role | Colour |
| --- | --- |
| Background | `#05080A` |
| Foreground | `#EBECFD` |
| Accent / magenta | `#E957E8` |
| Red | `#f4349a` |
| Yellow | `#b88faa` (dusty mauve) |
| Orange | `#f652a9` |
| Green | `#7bbc96` |
| Cyan | `#9BF1F2` |
| Blue | `#807cda` |
| Muted | `#313c44` |
| Active border | `#E957E8 #9BF1F2 25deg` |

Terminal text is pure white (`#ffffff`) with a white cursor and a
white-on-muted selection (`#ffffff` on `#313c44`), as in the original
`omarchy-edgerunners-theme`. ANSI yellow is restored to the original dusty
mauve `#b88faa` / `#ddc6d5` for a moodier look.

## Install

From a git clone:

```bash
omarchy theme install https://github.com/<you>/omarchy-edgerunners-v2-theme.git
omarchy theme set edgerunners-v2
```

Or copy this directory to `~/.config/omarchy/themes/edgerunners-v2` and run:

```bash
omarchy theme set edgerunners-v2
```

## What is here

| File | Purpose |
| --- | --- |
| `colors.toml` | Semantic palette; Omarchy generates Neovim (aether.nvim), Gum, helix, tmux, VSCode, browser policy, GTK mode and the shell theme from it |
| `alacritty.toml`, `kitty.conf`, `foot.ini`, `ghostty.conf` | Terminal palettes: pure-white foreground `#ffffff`, white cursor, white-on-muted selection `#ffffff` on `#313c44` |
| `hyprland.lua` | Neon border gradient plus the original theme's expressive animation curves |
| `btop.theme` | btop palette from the original `omarchy-edgerunners-theme` |
| `chromium.theme` | Browser UI colour (`R,G,B`) |
| `icons.theme` | Icon theme (`Yaru-magenta`) |
| `keyboard.rgb` | Keyboard backlight accent |
| `shell.lock.toml` | Lock screen border/placeholder overrides |
| `shell.popups.toml` | 2px popup borders so the gradient reads |
| `backgrounds/` | The original ten wallpapers, converted to WebP |

Omarchy refuses `*.lua`, terminal configs and `vscode.json` from a theme
installed through `omarchy theme install`, because those run code. That means a
git install gets the colours but not the animation curves or these exact
terminal palettes (its terminals are regenerated from `colors.toml`, with the
theme's `#EBECFD` UI foreground instead of `#ffffff`). To keep everything as
shipped, remove the clone marker so Omarchy treats the directory as your own
theme:

```bash
rm -rf ~/.config/omarchy/themes/edgerunners-v2/.git
omarchy theme set edgerunners-v2
```

The gradient border still works for everyone, since it is data in
`colors.toml`.

## Listings (eza)

Omarchy aliases `ls` to `eza`, and eza does not read `colors.toml`; it emits
ANSI slots that the terminal resolves through the active theme palette. eza's
default paints directories slot 4 (blue). `~/.config/eza/theme.yml` moves them
to slot 5 (magenta) and spreads the other file kinds across the neon palette:

```yaml
filekinds:
  directory: {foreground: Magenta, is_bold: true}
  mount_point: {foreground: Cyan, is_bold: true, is_underline: true}

file_type:
  image: {foreground: LightCyan}
  video: {foreground: LightMagenta, is_bold: true}
  source: {foreground: LightBlue}
  compressed: {foreground: Red, is_bold: true}
```

The full mapping also covers git statuses, dates, headers, link counts and
permissions. `Magenta`, `Cyan`, `LightCyan` and friends are ANSI slot names, not
fixed hex, so switching to Catppuccin turns folders Catppuccin's magenta
without editing this file. Because eza cannot read a theme directory, the
mapping is a user-level file; copy the one from a machine where this theme is
set up, or recreate the keys above.

## Not carried over

The original repos were written for Omarchy 2.x. These files have no equivalent
in Omarchy 4.5 and were intentionally dropped, because the Omarchy shell
replaced the old bar, launcher, notifications and OSD, and GTK is Adwaita
based:

`waybar.css`, `walker.css`, `wofi.css`, `mako.ini`, `swayosd.css`, `gtk.css`,
`hyprlock.conf`, `vencord.theme.css`, `warp.yaml`, `zellij.kdl`, and the
bundled VS Code extension. Neovim, helix, tmux, Gum, VSCode and GTK are
regenerated from `colors.toml`.

## Credits

* Original palette, terminal colours and wallpapers: JerryJerrington / Aether
* Port: Edgerunners V3 for Omarchy 4.5 (terminal palette from
  `omarchy-edgerunners-theme`, shell/UI from `omarchy-edgerunnersv2-theme`, neon orange accent swap)
