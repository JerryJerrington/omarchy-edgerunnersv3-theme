# Edgerunners V3 for Omarchy Quattro 4.5

A Cyberpunk Edgerunners inspired theme for [Omarchy Quattro](https://omarchy.org/) 4.5,
ported from [JerryJerrington/omarchy-edgerunnersv2-theme](https://github.com/JerryJerrington/omarchy-edgerunnersv2-theme)
(the "Aether" palette) to the Omarchy Quattro 4.5 theme format.

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
| Blue | `#E957E8` |
| Muted | `#313c44` |
| Active border | `#E957E8 #9BF1F2 25deg` |

Terminal text is pure white (`#ffffff`) with a white cursor and a
white-on-muted selection (`#ffffff` on `#313c44`), as in the original
`omarchy-edgerunners-theme`. ANSI yellow is restored to the original dusty
mauve `#b88faa` / `#ddc6d5` for a moodier look.

## Install

From a git clone:

```bash
omarchy theme install https://github.com/JerryJerrington/omarchy-edgerunnersv3-theme.git
omarchy theme set edgerunners-v3
```

Or copy this directory to `~/.config/omarchy/themes/edgerunners-v3` and run:

```bash
omarchy theme set edgerunners-v3
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
git install gets the colours but not the animations in `hyprland.lua`, the
exact terminal palettes, or the rest of the shipped configs (terminals are
regenerated from `colors.toml`, with the theme's `#EBECFD` UI foreground
instead of `#ffffff`). To keep everything as shipped, remove the clone marker
so Omarchy treats the directory as your own theme:

```bash
rm -rf ~/.config/omarchy/themes/edgerunners-v3/.git
omarchy theme set edgerunners-v3
```

The gradient border still works for everyone, since it is data in
`colors.toml`.

## Credits

* Original palette, terminal colours and wallpapers: JerryJerrington / Aether
* Port: Edgerunners V3 for Omarchy Quattro 4.5 (terminal palette from
  `omarchy-edgerunners-theme`, shell/UI from `omarchy-edgerunnersv2-theme`)


## Hyprland Borders & Animations

For custom Hyprland borders and animations, see the separate repo: [omarchy-edgerunnersv3-hypr](https://github.com/JerryJerrington/omarchy-edgerunnersv3-hypr). 

These files (`hyprland.lua`) are not shipped with the theme as they run code in Hyprland and are ignored by Omarchy's theme installer when the theme is cloned as a git repo.
