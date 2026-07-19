# Meet rempad!

<img width="600" height="600" alt="rempad" src="https://github.com/user-attachments/assets/b60390c2-29d6-4efc-83f8-bf26436aa777" />

(Yeah it's remOTEGAMEpad, still used the exact hue of Rem's hair from Re:Zero lol)

## USB gamepad input forwarding with additional features over LAN via WebSocket

This app is for USB GAMEPAD INPUT FORWARDING first, STREAMING and TOUCH CONTROLS are just "there" and not perfect.

This should work offline over LAN, too.

## Quick Start

```bash
git clone https://github.com/yourname/rempad.git
cd rempad
chmod +x start.sh
./start.sh
```

Open `http://<your-ip>:8765` on your phone browser.

## Features

- Screen streaming at 60 FPS (1280x720 default) (Experimental AF, you're better off using Sunshine/Apollo)
- USB gamepad input forwarding via Web Gamepad API (Firefox first)
- Touch trackpad
- Touch-to-mouse trackpad (Steam Deck-style) for phone screen
- Input-only mode (disable video for lowest input latency)
- Customizable UI hue
- Cursor overlay
- No app, just an HTML with a server.

## Requirements

### Linux PC

- Python 3.10+
- X11 session (Wayland not supported for screen capture)
- PulseAudio or PipeWire

Install system dependencies (Arch):

```bash
sudo pacman -S python-mss python-pillow python-aiohttp python-evdev python-xlib
```

Or use the venv (created automatically by `start.sh`):

```bash
pip install -r requirements.txt
```

**Note:** Your firewall must allow incoming connections on port 8765:

```bash
sudo ufw allow 8765/tcp
```

### Android Phone

- USB OTG support
- USB gamepad (Xbox, PlayStation, generic) - optional
- Any browser (Firefox, Chrome, etc.)
- Touchscreen (for touch-to-mouse trackpad)

## Usage

### Screen Streaming

1. Run `./start.sh` on your PC
2. Open the displayed URL on your phone
3. You'll see your PC screen in the browser

### Gamepad Input

1. Connect USB gamepad to your phone via OTG
2. The gamepad is detected automatically
3. Use it to control games on your PC

### Input-Only Mode

Tap "Video" option to toggle to input-only mode. This will stop the video stream entirely for minimum input latency.

### UI Customization

Drag the hue slider in the top bar to change the UI color. Your preference is saved to localStorage (all local).

## CLI Flags

```
./start.sh [OPTIONS]

--host HOST       Bind address (default: 0.0.0.0)
--port PORT       Port (default: 8765)
--fps FPS         Target FPS (default: 60)
--quality Q       JPEG quality 1-100 (default: 50)
--scale PCT       Scale percent (default: 67 = 1280x720 from 1080p)
```

### Examples

```bash
./start.sh --fps 30 --quality 30 --scale 50
./start.sh --port 9000 --fps 90
```

## License

MIT
