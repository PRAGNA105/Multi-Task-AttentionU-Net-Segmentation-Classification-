# 🧠 Brain Tumor Segmentation and Classification – Inference & Visualization

This project performs **automated brain tumor segmentation and classification** from MRI images.  
It uses a pre-trained deep learning model to generate **segmentation masks** and **tumor type predictions** and then produces **visual overlays** and **tabular results** for analysis.

---

## 🚀 Features

- Runs inference on all input MRI images.
- Generates segmentation masks highlighting tumor regions.
- Classifies each image into tumor type (e.g., *Glioma*, *Meningioma*, *Pituitary Tumor*, etc.).
- Saves **visual overlays** showing model predictions.
- Creates a **summary CSV** file with predicted class labels and confidence scores.

---

## 🧩 Directory Structure

project_root/
│
├── inference_script.py # Main script (the one you provided)
├── model/ # Folder containing trained model weights
├── data/ # Folder containing input images (.tif, .png, etc.)
│
└── prediction_outputs/
├── classification_results.csv # Saved CSV with predictions
└── visualizations/ # Contains overlay images


---

## ⚙️ Installation

1. Clone this repository
   ```bash
   git clone https://github.com/yourusername/brain-tumor-inference.git
   cd brain-tumor-inference

2. Create a virtual environment (optional but recommended)
   python -m venv venv
   source venv/bin/activate       # On macOS/Linux
   venv\Scripts\activate          # On Windows

3.Install dependencies
   pip install -r requirements.txt

   If you don’t have a requirements.txt, install manually:

   pip install numpy pandas pillow matplotlib tqdm


Running the Inference

1. Place your trained model and input images in appropriate folders (e.g., model/ and data/).

2. Update the all_data list and run_inference() function inside the script to load your data and model.

3. Run the script:

  python inference_script.py
 

4.Once complete, you’ll see:
   All done! Visualizations saved to 'prediction_outputs/visualizations'
   Classification results saved to: prediction_outputs/classification_results.csv

📊 Output Examples
1️⃣ Visualization

Each image shows:

Left: Original MRI image with red overlay highlighting the predicted tumor region.

Right: Predicted tumor class and model confidence.

2️⃣ CSV Output
image	class	probability
patient_001	Glioma	0.9534
patient_002	Meningioma	0.8772
patient_003	Pituitary Tumor	0.9125

🧱 Key Functions
Function	Description
overlay_mask_on_image()	Blends segmentation mask on top of the original MRI image using transparency.
save_visualization()	Creates side-by-side visualization of overlay + class info.
run_inference()	(To be defined) Loads model, predicts segmentation mask, class, and confidence.
tqdm	Displays progress bar during inference loop.

👩‍💻 Author

Your Name
📧 guthikondaPragna.com

💼 GitHub: PRAGNA_105
