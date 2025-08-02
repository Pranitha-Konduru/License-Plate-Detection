
License Plate OCR Project
=========================

This project implements a license plate detection and OCR pipeline using YOLOv8 and EasyOCR within a Jupyter notebook (.ipynb).

Prerequisites
-------------
- Python 3.7 or higher
- pip package manager

Installation
------------
Run the following command to install required libraries:

```
pip install ultralytics easyocr opencv-python numpy matplotlib pillow
```

Directory Structure
-------------------
```
.
|-- final_code.ipynb               # Jupyter notebook containing the complete pipeline
|-- dataset/
|   |-- images/
|       |-- train/
|       |-- val/
|       `-- test/
|-- runs/
    `-- detect/
        `-- train/weights/best.pt  # Custom trained YOLO weights (optional)
```

Usage
-----

1. **Launch the Jupyter Notebook**:
   ```bash
   jupyter notebook final_code.ipynb
   ```

2. **Run Cells Sequentially**:
   - **Imports & Model Loading**: Adjust `get_model_path()` if you have custom weights.
   - **Preprocessing Functions**: Noise filters, edge detectors, and enhancements.
   - **Detection & OCR Cells**: Apply YOLO detection and EasyOCR to each detected region.
   - **Visualization**: Display bounding boxes and recognized text on images.

3. **Optional: Convert to Script**:
   ```bash
   jupyter nbconvert --to script final_code.ipynb --output run_ocr.py
   python run_ocr.py --input-dir dataset/images/test --output-dir results
   ```

Configuration
-------------
- **Model Path**: `get_model_path()` returns custom weights if found at `/kaggle/working/runs/detect/train/weights/best.pt`, otherwise downloads `yolov8n.pt`.
- **OCR Settings**: Modify `reader = easyocr.Reader(['en'], gpu=torch.cuda.is_available())` to change languages or GPU usage.

Outputs
-------
- Prints detected license plate text in the notebook console.
- Overlays bounding boxes and recognized text on images displayed inline.

Notes
-----
- For GPU acceleration, ensure CUDA and NVIDIA drivers are installed.
- Feel free to tweak preprocessing parameters (e.g., kernel sizes, thresholds) to improve OCR accuracy.
