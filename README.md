# Emojimizer

**Photo > emoji.** Drop in a photo, get back a layered emoji moodboard.

Runs entirely in the browser — no server, no uploads, no dependencies to install. Just open `emojimizer.html`.

## How it works

1. You load a photo.
2. [COCO-SSD](https://github.com/tensorflow/tfjs-models/tree/master/coco-ssd) (via TensorFlow.js) detects objects and places a matching emoji over each one, sized to its bounding box.
3. [MobileNet](https://github.com/tensorflow/tfjs-models/tree/master/mobilenet) classifies the overall scene and adds contextual emoji.
4. The result is a white-background collage you can export as a JPG or download as a compact text encoding.

Both models download once from a CDN (~8 MB total), then run locally.

## Controls

| Control | What it does |
|---|---|
| Scale | How large the emoji render relative to their detected bounding box |
| Max objects | Upper limit on COCO-SSD detections shown |
| Confidence | Detection threshold — lower values produce more (and weirder) results |
| Atmosphere | Number of mood emoji scattered in the background |

## Export

- **Export JPG** — renders the collage to a canvas at 2× display resolution and saves as JPEG
- **Download encoding** — saves the layout as a plain-text file (`emoji|x%|y%|size%|rotation|layer` per line), small enough to embed anywhere that renders emoji

## Usage

No build step. Open `emojimizer.html` in any modern browser.

```
git clone https://github.com/yourname/emojimizer
open emojimizer.html
```
