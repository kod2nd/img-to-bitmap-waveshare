# Waveshare 7-Color E-Paper Image Converter

A client-side web app that converts images for the [Waveshare 7.3" ACeP 7-Color E-Paper photo frame](https://www.waveshare.com/photopainter.htm).

All processing happens in the browser -- no server required.

## Features

- Drag & drop or click to upload an image (JPG, PNG, GIF, BMP)
- Aspect-ratio-locked crop to fit the display dimensions
- Floyd-Steinberg dithering to the 7-color e-paper palette (black, white, green, blue, red, yellow, orange)
- Portrait/landscape orientation toggle
- Configurable output dimensions (default 480x800)
- Downloads a 24-bit BMP ready for the display

## Usage

Open `index.html` in a browser, or visit the hosted version:

**https://cdhoff03.github.io/waveshare-image-convert/**

1. Upload an image
2. Drag the crop to select what fills the display
3. Click **Convert**
4. Click **Download BMP**

Based on [color-e-paper-image-converter](https://gitlab.com/matthew/color-e-paper-image-converter) by Matthew.
