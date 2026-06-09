# Image Processing Pipeline for Psychophysics

A modular Jupyter notebook pipeline for loading, transforming, analysing, and exporting face images for use in psychophysics experiments. Developed as part of the following study:

> Pang, D. K. F., Hibble, A., Smithson, H. E., & Azzopardi, P. (in preparation). AI-Generated Psychophysics Face Stimuli: Methods, Challenges, and Best Practices.

---

## Contents

| File | Description |
|------|-------------|
| `Image_Processor.ipynb` | Main processing pipeline notebook |
| `requirements.txt` | Python package dependencies |
| `.gitignore` | Git ignore rules |

---

## Pipeline Overview

Each processing step can be independently toggled on or off via the configuration cell. Steps run in the following order:

| Step | Description |
|------|-------------|
| 1 | Load images (single file or entire folder) |
| 2 | Convert to greyscale |
| 3 | Face detection & landmark-based alignment and scaling |
| 4 | Scale and crop to target dimensions |
| 5 | Adjust luminance, contrast, and spatial frequency content |
| 6 | Apply oval mask with gradient transition |
| 7 | Compute image analytics (histogram, luminance, contrast, Fourier) |
| 8 | Export processed images |

---

## Requirements

```
pip install -r requirements.txt
```

**Packages:** `numpy`, `Pillow`, `matplotlib`, `scipy`, `opencv-contrib-python`

> **Note:** The pipeline will automatically download `lbfmodel.yaml` on first run — a pre-trained facial landmark model (~53 MB). It is cached locally and reused on subsequent runs.

---

## Quick Start

1. Install dependencies: `pip install -r requirements.txt`
2. Place images in `./input/` (or update `INPUT_PATH` in the configuration cell)
3. Open `Image_Processor.ipynb` and run all cells top-to-bottom
4. Processed images are saved to `./output/` by default

---

## Configuration

All settings are contained in a single configuration cell (Section 2). Key parameters:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `INPUT_PATH` | `./input` | Path to input image(s) |
| `OUTPUT_FOLDER` | `./output` | Output directory |
| `OUTPUT_FORMAT` | `PNG` | Export format (PNG, JPEG, TIFF, BMP, WEBP, GIF) |
| `ENABLE_FACE_ALIGN` | `True` | Landmark-based face centring and scaling |
| `ENABLE_OVAL_MASK` | `True` | Oval mask with soft gradient edge |
| `ENABLE_ANALYTICS` | `True` | Per-image analytics dashboard |
| `TARGET_MEAN_LUMINANCE` | `128` | Target mean luminance (0–255) |
| `TARGET_RMS_CONTRAST` | `30` | Target RMS contrast (0–127) |
| `OBSERVER_BASED` | `True` | Scale frequency axes in cycles per degree (cpd) |

---

## Citation

If you use this pipeline in your research, please cite:

```
Pang, D. K. F., Hibble, A., Smithson, H. E., & Azzopardi, P. (in preparation).
AI-Generated Psychophysics Face Stimuli: Methods, Challenges, and Best Practices.
```

---

## License

MIT License. See `LICENSE` for details.
