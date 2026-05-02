# Satellite Image Processing

A Python toolkit for processing and analyzing satellite imagery using classical computer vision techniques (no machine learning required).

Built with OpenCV, NumPy, and Pillow, the project is split into two independent modules.

---

## Project Structure


Satellite Image processing/
├── satellite_processor/ # CLI image processing tool
│ ├── main.py # Entry point (argparse CLI)
│ ├── processor.py # Core processing functions
│ ├── utils.py # File I/O helpers
│ ├── requirements.txt
│ └── samples/ # Sample satellite images
│
└── satellite-analyzer/ # Land cover classification script
├── analyze.py # HSV-based pixel classifier
├── requirements.txt
└── samples/ # Sample satellite images

---

## Getting Started

### Prerequisites

- Python 3.11+
- pip

### Installation

```bash
git clone <repo-url>
cd "Satellite Image processing"

# Install dependencies for processor module
pip install -r satellite_processor/requirements.txt

# Install dependencies for analyzer module
pip install -r satellite-analyzer/requirements.txt
Module 1: Satellite Processor

A command-line tool that applies image processing operations to satellite images.

Supported Formats
.jpg
.jpeg
.png
.tif
.tiff
Usage
python satellite_processor/main.py --input <image_path> --operation <operation>
Operations
Operation	Description
grayscale	Converts the image to grayscale
enhance	Boosts local contrast using CLAHE (per-channel for RGB)
edges	Detects edges using Canny edge detection
ndvi	Computes an NDVI-like vegetation index visualization
all	Runs all operations at once

Note:
NDVI works best with 4-band images (NIR + RGB). For standard RGB images, the green channel is used as a pseudo-NIR proxy.

Examples
# Single operations
python satellite_processor/main.py --input satellite_processor/samples/sample.jpg --operation grayscale
python satellite_processor/main.py --input satellite_processor/samples/sample.jpg --operation edges
python satellite_processor/main.py --input satellite_processor/samples/sample.jpg --operation enhance

# NDVI (best with multi-band TIF)
python satellite_processor/main.py --input sample.tif --operation ndvi

# Run all operations
python satellite_processor/main.py --input satellite_processor/samples/sample.jpg --operation all
Output
Saved to: satellite_processor/output/
Custom output directory:
--output <dir>
Module 2: Satellite Analyzer

An interactive script that classifies every pixel in a satellite image into land cover categories using HSV color thresholds.

Categories
Category	Output Color	Method
Water	Blue	HSV hue range: 90–140
Vegetation	Green	HSV hue range: 35–85
Land / Urban	Gray	Everything else
Usage
# Direct image input
python satellite-analyzer/analyze.py samples/City.jpeg

# Interactive mode (lists available samples)
python satellite-analyzer/analyze.py
Output
Saves: satellite-analyzer/output/result.jpg
Prints percentage breakdown, for example:
Water: 12%  |  Vegetation: 45%  |  Land: 43%
Sample Images

Included in both modules:

City.jpeg, City-1.jpeg — urban areas
Desert.jpeg — arid terrain
Snow.jpeg — snow-covered terrain
Water.jpeg — water bodies
India.jpeg — mixed terrain
Tech Stack
Library	Version	Purpose
Python	3.11	Runtime
OpenCV	4.10.0	Image processing and computer vision
NumPy	1.26.4	Array operations
Pillow	10.4.0	Image I/O support
License

This project is intended for educational and research purposes.
