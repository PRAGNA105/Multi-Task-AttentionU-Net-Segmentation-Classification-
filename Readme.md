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

yaml
Copy code

---

## ⚙️ Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/yourusername/brain-tumor-inference.git
   cd brain-tumor-inference
Create a virtual environment (optional but recommended)

bash
Copy code
python -m venv venv
source venv/bin/activate       # On macOS/Linux
venv\Scripts\activate          # On Windows
Install dependencies

bash
Copy code
pip install -r requirements.txt
If you don’t have a requirements.txt, install manually:

bash
Copy code
pip install numpy pandas pillow matplotlib tqdm
🧠 Running the Inference
Place your trained model and input images in appropriate folders (e.g., model/ and data/).

Update the all_data list and run_inference() function inside the script to load your data and model.

Run the script:

bash
Copy code
python inference_script.py
Once complete, you’ll see:

bash
Copy code
✅ All done! Visualizations saved to 'prediction_outputs/visualizations'
📄 Classification results saved to: prediction_outputs/classification_results.csv
🖼️ Example Output Visualization
Below is an example visualization of the model’s output.
The left side shows the MRI image with the tumor segmentation overlay, and the right side shows the predicted tumor class and confidence score.

<p align="center"> <img src="prediction_outputs/visualizations/sample_result.png" alt="Example Overlay Visualization" width="600"/> </p>
If your visualization image is stored elsewhere, update the image path above (e.g., images/overlay_example.png).

📊 Output Examples
1️⃣ Visualization
Each image shows:

Left: Original MRI image with red overlay highlighting the predicted tumor region.

Right: Predicted tumor class and model confidence.

2️⃣ CSV Output
image	class	probability
patient_001	Glioma	0.9534
patient_002	Meningioma	0.8772

🧱 Key Functions
Function	Description
overlay_mask_on_image()	Blends segmentation mask on top of the original MRI image using transparency.
save_visualization()	Creates side-by-side visualization of overlay + class info.
run_inference()	(To be defined) Loads model, predicts segmentation mask, class, and confidence.
tqdm	Displays progress bar during inference loop.

🧰 Requirements
Library	Version (Suggested)
Python	3.8+
numpy	>=1.23
pandas	>=1.4
pillow	>=9.2
matplotlib	>=3.5
tqdm	>=4.64

💡 Notes
The run_inference() function should return:

python
Copy code
mask_image, predicted_class, class_prob
mask_image: predicted segmentation mask (as a PIL image)

predicted_class: tumor type (string)

class_prob: probability (float between 0–1)

The script expects masks with pixel values 0–255.

🏁 Results
Visual Overlays → prediction_outputs/visualizations/

Classification CSV → prediction_outputs/classification_results.csv

Both files are automatically generated at the end of execution.

👩‍💻 Author
Guthikonda PRagna
📧 guthikondapragnagmail.com
💼 GitHub: PRAGNA_!05
