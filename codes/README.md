# Enhanced Oriented Bounding Box (OBB) Detection

This repository contains a comprehensive implementation of Oriented Bounding Box detection using multiple approaches. The implementation includes various methods for detecting rotated objects in images and provides visualization tools.

## Features

- Multiple detection methods:
  - Contour-based detection
  - Connected Components analysis
  - MSER (Maximally Stable Extremal Regions)
- Image preprocessing with CLAHE enhancement
- Configurable parameters for detection
- Visualization tools with angle and center point display
- Result export to JSON format
- Type hints and comprehensive documentation

## Requirements

Install the required packages using:

```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage

```python
from enhanced_obb_detection import EnhancedOBBDetector

# Create detector instance
detector = EnhancedOBBDetector()

# Load image
image = cv2.imread("your_image.jpg")

# Detect objects (choose method: 'contour', 'connected_components', or 'mser')
detections = detector.detect_objects(image, method='contour')

# Visualize results
result = detector.visualize_detections(image, detections)

# Display
cv2.imshow("Detection Results", result)
cv2.waitKey(0)

# Save results
detector.save_results(detections, "detections.json")
```

### Custom Configuration

You can customize the detector's parameters:

```python
config = {
    'min_area': 150,
    'max_area': 3000,
    'min_aspect': 1.5,
    'max_aspect': 4.0,
    'canny_low': 30,
    'canny_high': 200,
    'clahe_clip_limit': 3.0,
    'clahe_grid_size': (8, 8),
    'morph_kernel_size': (3, 3)
}

detector = EnhancedOBBDetector(config)
```

## Detection Methods

1. **Contour-based Detection**
   - Uses edge detection and contour analysis
   - Best for objects with clear boundaries
   - Configurable edge detection parameters

2. **Connected Components**
   - Uses region labeling and properties
   - Good for separated objects
   - Supports different connectivity options

3. **MSER Detection**
   - Uses Maximally Stable Extremal Regions
   - Effective for text and blob detection
   - Configurable region parameters

## Output Format

The detection results are returned as a list of dictionaries, each containing:
- `box`: Corner points of the oriented bounding box
- `center`: Center coordinates
- `width`: Box width
- `height`: Box height
- `angle`: Rotation angle in degrees
- `area`: Area of the detected region
- `confidence`: Detection confidence score

## Example

Run the example script:

```bash
python enhanced_obb_detection.py
```

This will:
1. Load a sample image
2. Apply all three detection methods
3. Display the results side by side
4. Save the detections to a JSON file

## License

This project is licensed under the MIT License - see the LICENSE file for details. 