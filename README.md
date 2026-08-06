# Waveshare PhotoPainter (B) Image Converter

A browser-based image converter for the [Waveshare PhotoPainter (B)](https://www.waveshare.com/photopainter.htm) 6-colour e-paper display.

The entire application runs **in your browser**. There is no installation, no server, no build step, and no telemetry. Images are processed locally on your machine and are never uploaded anywhere.

## Why this project exists

The official Waveshare converter works, but it is limited. It offers basic conversion with little control over the final result, making it difficult to get good-looking images out of a 6-colour e-paper panel.

This project was built to fill that gap with:

- **Better image quality** — more faithful tonal reproduction through proper colour matching and dithering
- **Better colour control** — per-colour tuning and recalibratable palette swatches
- **Better usability** — a workflow designed for making quick adjustments and seeing results immediately
- **Better preview** — side-by-side Original / Enhanced / Final previews with a compare slider
- **Modern UI** — a clean, responsive, desktop-style interface with a dark theme
- **Batch processing** — convert a queue of images and download them as a ZIP
- **Faster workflow** — drag-and-drop, live preview, and settings that persist between sessions

## Features

### Image Processing

Fine-tune the image before conversion with seven adjustments:

| Control | What it does |
| --- | --- |
| **Brightness** | Global brightness level |
| **Contrast** | Global tonal contrast |
| **Gamma** | Mid-tone curve adjustment |
| **Saturation** | Overall colour intensity |
| **Vibrance** | Colour intensity weighted toward less-saturated pixels |
| **Shadow Lift** | Raises dark regions without affecting highlights |
| **Highlight Compression** | Tames bright regions without crushing shadows |

Every adjustment has a one-click reset to its default value.

### Colour

- **Spectra 6 palette** — the PhotoPainter (B) 6-colour gamut (black, white, yellow, red, blue, green)
- **Perceptual colour matching** — perceptually-weighted RGB distance matching for each pixel
- **Adjustable colour tuning** — per-colour bias sliders that favour one palette colour over the others during matching
- **Recalibration** — click any swatch to redefine its real-world RGB value, with per-adjuster reset

### Dithering

- **Floyd-Steinberg** error-diffusion dithering
- **Adjustable strength** — control how much of the error is diffused to neighbouring pixels
- **Serpentine scanning** — alternates scan direction per row to reduce directional artefacts

### Workflow

- **Drag & Drop** — drop an image anywhere in the work area, or click **Change image…**
- **Crop** — aspect-locked crop with draggable handles, sized to your target resolution
- **Live Preview** — the pipeline re-runs instantly as you adjust any control
- **Batch Conversion** — queue multiple images and convert them with the current settings
- **ZIP Export** — download all converted images as a single ZIP archive

### Interface

- **Responsive desktop layout** — fixed toolbar and status bar, independently scrolling sidebars (usable at 1366×768 and up)
- **Dark theme** — with a light-theme toggle
- **Local settings persistence** — profiles, biases, and control values are saved to your browser between sessions, and can be exported/imported as a JSON file

## Installation

**There is nothing to install.**

- Open `index.html` in a modern browser
- No build process
- No network requests after the page loads
- Works offline once the file is saved

## Usage

1. **Open the app** — double-click `index.html` (or open the hosted version).
2. **Drag an image** — JPG, PNG, GIF, and BMP are supported. Drop it anywhere in the work area.
3. **Crop if desired** — the crop window is pre-sized to your target aspect ratio; drag it or its handles to choose what fills the display. Set width/height (default 480×800 portrait, 800×480 landscape).
4. **Adjust colour** — tune brightness, contrast, gamma, saturation, vibrance, shadows, and highlights. Pick a preset or set values manually.
5. **Preview** — watch the Original, Enhanced, and Final e-paper previews update live. Use the compare slider to A/B the result.
6. **Export BMP** — click **Download** to get a 24-bit BMP sized exactly for the display.
7. **Copy to SD card** — transfer the BMP onto the PhotoPainter's SD card.
8. **Insert into the PhotoPainter (B)** — the display renders it directly.

> [!TIP]
> Use the conversion queue for multiple images: **Add files** → **Convert all** → **Download ZIP**.

## Technical Details

- **Browser Canvas API** — all image decoding, cropping, resizing, and preview rendering uses the standard `canvas` API; no plugins or WebAssembly required.
- **Client-side image processing** — every pixel operation (colour adjustments, palette matching, error-diffusion dithering) runs in JavaScript on your machine.
- **No server** — the app is a single self-contained HTML file; nothing is transmitted.
- **BMP generation** — exports a 24-bit, bottom-up, BGR-order BMP with 4-byte row alignment, byte-compatible with the PhotoPainter (B) firmware's colour table.
- **Spectra 6 palette** — colours are matched to the real-world panel gamut during conversion, then mapped to the firmware's exact device values at export, so previews show what you tuned while the exported file renders correctly on the panel.

## Project Structure

| File | Purpose |
| --- | --- |
| `index.html` | The entire application (HTML, CSS, and JavaScript in one self-contained file) |
| `README.md` | This documentation |
| `LICENSE` | Project license |
| `docs/` | Screenshots and supporting documentation |

## Roadmap

- [x] Drag & Drop
- [x] Crop Tool
- [x] Live Preview
- [x] BMP Export
- [x] Batch Conversion & ZIP
- [x] Dark theme
- [x] Settings persistence
- [ ] CIELAB colour matching
- [ ] Additional dithering algorithms
- [ ] ICC profile support
- [ ] Automatic photo optimisation
- [ ] Device presets
- [ ] Keyboard shortcuts

## License

Licensed under the [MIT License](LICENSE). See the `LICENSE` file for details.

The project is based on [color-e-paper-image-converter](https://gitlab.com/matthew/color-e-paper-image-converter) by Matthew.