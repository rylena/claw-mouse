# desktopctl

A small, pragmatic desktop GUI control helper for Linux **X11**.

It’s designed for “vision loop” automation:
1) take a screenshot
2) decide where to click
3) move/click/type
4) repeat

Under the hood it wraps:
- `scrot` for screenshots
- `xdotool` for mouse/keyboard/window control

## Requirements

- Linux running **X11** (not Wayland-only)
- `python3`
- `xdotool`
- `scrot`

Ubuntu/Debian:
```bash
sudo apt-get update
sudo apt-get install -y xdotool scrot
```

## Install

No install step required — it’s a single script.

```bash
chmod +x desktopctl.py
./desktopctl.py --help
```

## Usage

### Screenshot
```bash
./desktopctl.py screenshot
./desktopctl.py screenshot --out /tmp/desktop.png
```

### Click
```bash
./desktopctl.py click 500 300
./desktopctl.py click 500 300 --button 3
```

### Type + keys
```bash
./desktopctl.py type "hello world"
./desktopctl.py key ctrl+l
./desktopctl.py key Return
```

### Mouse location
```bash
./desktopctl.py where
```

### Windows
```bash
./desktopctl.py windows
./desktopctl.py activate "Chromium"
```

### Open a URL
```bash
./desktopctl.py open https://example.com
```

## DISPLAY / XAUTHORITY

`xdotool`/`scrot` need access to your X session.

If you’re running from a headless shell/daemon where `DISPLAY` isn’t set, provide it explicitly:

```bash
DISPLAY=:0 XAUTHORITY=$HOME/.Xauthority ./desktopctl.py screenshot
```

You can also pass overrides:

```bash
./desktopctl.py --display :0 --xauthority $HOME/.Xauthority screenshot
```

## Notes

- Wayland support is intentionally not included (it’s a different stack). If you need Wayland support, open an issue and mention your compositor (GNOME/KDE/Sway/etc.).

## License

MIT
