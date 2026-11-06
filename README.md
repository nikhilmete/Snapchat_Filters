# Snapchat_Filters
# Snapchat-style Photo Filters with OpenCV

Face detection + fun overlay filters + live webcam application using classic OpenCV tools.

## Features

- **Face & Eye Detection** using Haar Cascades
- **Colour / Lens Filters**
  - Grayscale, Invert, Sepia, Vintage
  - Warm, Cool, Vignette
  - Cartoon, Colour Pop, Beauty (skin smooth)
- **Sticker Filters** (drawn as transparent RGBA overlays)
  - Dog ears + nose
  - Sunglasses
  - Moustache
  - Bunny ears
  - Crown
- **Big-eyes cartoon filter** (local image warping)
- Single `apply_filter(image, name)` filter engine
- **Live Webcam App**
  - Real-time face detection
  - Switch filters with keyboard
  - FPS counter
  - Snapshot saving

## How Snapchat does it vs this project

Real Snapchat/Instagram filters use deep-learning face landmarks (dlib / MediaPipe / face-alignment).  
This project uses the classic OpenCV approach:

- Haar-cascade face & eye **bounding boxes**
- Stickers placed using **proportions** of the face box

It is slightly less precise when the head is tilted, but:
- Runs anywhere without extra heavy libraries
- Teaches the same core ideas
- Easy to upgrade later with `pip install mediapipe`

## Requirements

- Python 3.8+
- Webcam (for live mode)

```bash
pip install -r requirements.txt
```

## Project Structure (suggested)

```
snapchat-opencv-filters/
├── README.md
├── requirements.txt
├── assets/               # optional: face.jpg, custom stickers
├── src/
│   ├── detectors.py
│   ├── colour_filters.py
│   ├── stickers.py
│   ├── filter_engine.py
│   └── webcam_app.py
├── notebooks/
│   └── snapchat_filters.ipynb
└── main.py
```

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run the live webcam filter app
python main.py
```

### Webcam Controls (example)

| Key | Action              |
|-----|---------------------|
| `1-9` | Switch filter     |
| `s`   | Save snapshot     |
| `q`   | Quit              |

## Filters Available

| Name          | Type     | Description                          |
|---------------|----------|--------------------------------------|
| `grayscale`   | Colour   | Black & white                        |
| `sepia`       | Colour   | Classic sepia tone                   |
| `vintage`     | Colour   | Sepia + vignette + noise             |
| `warm`        | Colour   | Warmer colour temperature            |
| `cool`        | Colour   | Cooler colour temperature            |
| `vignette`    | Colour   | Darkened edges                       |
| `cartoon`     | Style    | Cartoon / comic look                 |
| `beauty`      | Style    | Skin smoothing inside face           |
| `color_pop`   | Style    | Colour only on face, rest gray       |
| `dog`         | Sticker  | Dog ears + nose                      |
| `sunglasses`  | Sticker  | Sunglasses overlay                   |
| `moustache`   | Sticker  | Moustache                            |
| `bunny`       | Sticker  | Bunny ears                           |
| `crown`       | Sticker  | Crown                                |

## Notes

- Put a clear front-facing photo named `face.jpg` next to the notebook for best results.
- If no photo is present, a simple cartoon face is drawn so every filter still runs.
- Haar cascades work best on front-facing faces with good lighting.

## License

Free for learning and personal projects.
