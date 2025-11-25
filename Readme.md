# 🧠 Brain Tumor Segmentation and Classification

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An automated deep learning pipeline for brain tumor segmentation and classification from MRI images. This project uses pre-trained models to generate accurate segmentation masks, classify tumor types, and produce comprehensive visualizations for clinical analysis.

---

## 📋 Table of Contents

- [Features](#-features)
- [Sample Outputs](#-sample-outputs)
- [Installation](#️-installation)
- [Usage](#-usage)
- [Directory Structure](#-directory-structure)
- [Output Examples](#-output-examples)
- [Key Functions](#-key-functions)
- [Requirements](#-requirements)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## ✨ Features

- **Automated Inference**: Batch processing of MRI images for efficient analysis
- **Tumor Segmentation**: Precise pixel-level tumor boundary detection
- **Multi-class Classification**: Identifies tumor types including:
  - Glioma
  - Meningioma
  - Pituitary Tumor
  - No Tumor (healthy)
- **Visual Overlays**: Color-coded segmentation masks superimposed on original MRI scans
- **Confidence Scoring**: Probability metrics for each prediction
- **Export Results**: CSV reports for further analysis and record-keeping

---

## 🖼️ Sample Outputs

### Segmentation Overlay Visualization

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=1v7-J-RMKeWTimNM3rm-zTgKkvhhWMnBY" alt="Segmentation Overlay Example 1" width="700"/>
  <br>
  <em>Segmentation Overlay: MRI scan with tumor region detection and classification</em>
</p>

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=14hqAPnJExKqC9rnGyGAO_G1kH7rmyGnH" alt="Segmentation Overlay Example 2" width="700"/>
  <br>
  <em>Example: Multi-colored segmentation showing different tissue types</em>
</p>

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=16ZXzmitOCrsc96Wg6UheSYXL9W6Bjjwx" alt="Segmentation Overlay Example 3" width="700"/>
  <br>
  <em>Example: Tumor boundary detection with confidence scores</em>
</p>

### Classification Results Dashboard

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=1FitlVH0vkvmTX4dDoRgRYLxEyaniK8Wk" alt="Classification Results CSV Table" width="500"/>
  <br>
  <em>Comparison of multiple MRI scans with their corresponding predictions</em>
</p>
```



## ⚙️ Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- 4GB+ RAM recommended
- GPU support (optional, for faster inference)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/PRAGNA_105/brain-tumor-inference.git
   cd brain-tumor-inference
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   # On macOS/Linux
   python -m venv venv
   source venv/bin/activate

   # On Windows
   python -m venv venv
   venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

   **Or install manually:**
   ```bash
   pip install numpy pandas pillow matplotlib tqdm torch torchvision
   ```

4. **Download pre-trained model**
   - Place your trained model weights in the `model/` directory
   - Ensure the model file is named appropriately (e.g., `best_model.pth`)

---

## 🚀 Usage

### Quick Start

1. **Prepare your data**
   - Place MRI images (`.tif`, `.png`, `.jpg`) in the `data/` folder
   - Supported formats: TIFF, PNG, JPEG

2. **Configure the script**
   ```python
   # In inference_script.py, update these variables:
   MODEL_PATH = "model/best_model.pth"
   DATA_DIR = "data/"
   OUTPUT_DIR = "prediction_outputs/"
   ```

3. **Run inference**
   ```bash
   python inference_script.py
   ```

4. **View results**
   ```bash
   ✅ Processing complete!
   📊 Processed 50 images
   📁 Visualizations saved to: prediction_outputs/visualizations/
   📄 Classification results: prediction_outputs/classification_results.csv
   ```

### Advanced Usage

**Process specific images:**
```python
from inference_script import run_inference

# Process single image
result = run_inference("data/patient_001.tif")
print(f"Tumor Type: {result['class']}, Confidence: {result['probability']:.2%}")
```

**Batch processing with custom thresholds:**
```python
# Set confidence threshold
CONFIDENCE_THRESHOLD = 0.85

# Filter results
high_confidence_results = results[results['probability'] > CONFIDENCE_THRESHOLD]
```

---

## 🗂️ Directory Structure

```
brain-tumor-inference/
│
├── inference_script.py          # Main inference script
├── requirements.txt             # Python dependencies
├── README.md                    # This file
│
├── model/                       # Model weights directory
│   └── best_model.pth          # Pre-trained model
│
├── data/                        # Input MRI images
│   ├── patient_001.tif
│   ├── patient_002.tif
│   └── ...
│
├── prediction_outputs/          # Generated results
│   ├── classification_results.csv
│   │
│   └── visualizations/          # Overlay images
│       ├── patient_001_overlay.png
│       ├── patient_002_overlay.png
│       └── ...
│
└── utils/                       # Helper functions (optional)
    ├── preprocessing.py
    └── postprocessing.py
```

---

## 📊 Output Examples

### 1. Visual Overlays

Each visualization contains:
- Left Panel: Original MRI scan with red segmentation overlay (tumor region)
- Right Panel: Predicted classification with confidence score


**Color Coding:**
- 🔴 Red overlay: Detected tumor region
- Transparency: 0.4 alpha for clear visibility

### 2. Classification Results (CSV)

| image        | class       | probability | timestamp           |
|--------------|-------------|-------------|---------------------|
| patient_001  | Glioma      | 0.9534      | 2024-03-15 14:23:11 |
| patient_002  | Meningioma  | 0.8772      | 2024-03-15 14:23:12 |
| patient_003  | No Tumor    | 0.9821      | 2024-03-15 14:23:13 |
| patient_004  | Pituitary   | 0.9156      | 2024-03-15 14:23:14 |

**CSV includes:**
- Image filename
- Predicted tumor class
- Confidence probability (0-1)
- Processing timestamp

---

## 🔧 Key Functions

### Core Functions

| Function | Description | Returns |
|----------|-------------|---------|
| `run_inference(image_path)` | Executes model prediction pipeline | `(mask, class, probability)` |
| `overlay_mask_on_image(img, mask)` | Blends segmentation mask with MRI | `PIL.Image` |
| `save_visualization(img, mask, class, prob, output_path)` | Creates side-by-side visualization | `None` |
| `load_model(model_path)` | Loads pre-trained weights | `torch.nn.Module` |
| `preprocess_image(image)` | Normalizes and resizes input | `torch.Tensor` |

### Function Details

**`run_inference(image_path)`**
```python
Args:
    image_path (str): Path to input MRI image

Returns:
    mask_image (PIL.Image): Segmentation mask (0-255 pixel values)
    predicted_class (str): Tumor type classification
    class_prob (float): Prediction confidence (0.0-1.0)
```

**`overlay_mask_on_image(img, mask, alpha=0.4)`**
```python
Args:
    img (PIL.Image): Original MRI image
    mask (PIL.Image): Binary segmentation mask
    alpha (float): Overlay transparency (default: 0.4)

Returns:
    PIL.Image: Blended visualization
```

---

## 📦 Requirements

### Python Dependencies

| Library      | Version    | Purpose                          |
|--------------|------------|----------------------------------|
| Python       | 3.8+       | Core runtime                     |
| numpy        | ≥1.23.0    | Array operations                 |
| pandas       | ≥1.4.0     | CSV handling and data analysis   |
| pillow       | ≥9.2.0     | Image processing                 |
| matplotlib   | ≥3.5.0     | Visualization generation         |
| tqdm         | ≥4.64.0    | Progress bars                    |
| torch        | ≥1.12.0    | Deep learning inference          |
| torchvision  | ≥0.13.0    | Image transformations            |

### Hardware Requirements

- **Minimum**: 4GB RAM, 2GB storage
- **Recommended**: 8GB RAM, GPU with 4GB VRAM, 10GB storage

---

## 💡 Tips & Best Practices

1. **Image Quality**: Use high-resolution MRI scans (256×256 or higher) for best results
2. **Preprocessing**: Ensure images are properly skull-stripped if required by your model
3. **Batch Size**: Process 10-20 images at a time to avoid memory issues
4. **Model Updates**: Regularly retrain with new data to maintain accuracy
5. **Validation**: Always verify predictions with medical professionals

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 Contact

**Guthikonda Pragna**

- 📧 Email: guthikondapragna@gmail.com
- 💼 GitHub: [@PRAGNA_105](https://github.com/PRAGNA_105)

---

## 🙏 Acknowledgments

- Thanks to the medical imaging community for providing datasets
- Inspired by state-of-the-art brain tumor segmentation research
- Built with ❤️ for advancing medical AI applications

---

<p align="center">
  <strong>⭐ If you find this project helpful, please consider giving it a star!</strong>
</p>

---

