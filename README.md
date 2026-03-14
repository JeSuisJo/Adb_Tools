# adb_tools

Generic setup for scripting an Android device via ADB.

## Project structure

```
adb_tools/
├── platform-tools/
│   └── adb.exe              # ADB executable
├── helper/
│   ├── find_coords.py       # Click on the screen to get coordinates + RGB
│   └── make_a_screen.py     # Capture a region of the screen in PNG
├── tools/
│   ├── __init__.py
│   └── adb.py               # All ADB functions
├── check_id.py              # List all connected devices
├── config.json              # Device ID of the target device
└── README.md
```

## How to install
1. Install dependencies:
```bash
pip install pillow matplotlib
```
2. Fill the `device_id` in `config.json` (use `check_id.py` to find it)

## How to use

```python
from tools import tap, swipe, write, compare_image, is_color, stop, path

tap(500, 300)
hold(500, 300, ms=800) # Hold right button for 800ms
swipe(100, 800, 100, 200)
write("hello world")
enter() # Enter key
delete() # Delete key

# Image - relative path to the project root
if not compare_image(path("img/example.png"), (0, 0, 200, 100)):
    stop("Example image not found")

# Color
if is_color(540, 960, (255, 0, 0)):
    tap(540, 960)
```

## Helpers

| Script | Usage |
|---|---|
| `check_id.py` | Affiche les appareils ADB connectés |
| `helper/find_coords.py` | Capture l'écran, cliquer pour obtenir coords + RGB |
| `helper/make_a_screen.py` | Capture une région définie et la sauvegarde en PNG |
