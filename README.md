# yolo11-visdrone-detector

Real-time aerial object detection system for autonomous drones - optimized for surveillance, search & rescue use cases with Streamlit deployment interface.

## Features

- **YOLOv11 Object Detection**: High-performance object detection trained on VisDrone dataset
- **Aerial Imagery Optimization**: Models trained specifically on drone footage for superior accuracy
- **Real-time Inference**: Fast detection on video and image inputs
- **Web Interface**: User-friendly Streamlit application for easy deployment
- **Multi-class Detection**: Detects multiple object categories common in aerial surveillance
- **Production-Ready**: Optimized models with comprehensive error handling

## Dataset

This project uses the **VisDrone Dataset** - a large-scale benchmark for object detection in drone imagery containing:
- Real-world drone footage from various altitudes and perspectives
- Diverse environmental conditions and object scales
- Comprehensive annotations for robust model training

## Installation

### Prerequisites
- Python 3.8+
- CUDA-capable GPU (recommended) or CPU

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/aadityakr45/yolo11-visdrone-detector
   cd yolo11-visdrone-detector
   ```

2. **Create virtual environment**
   ```bash
   python -m venv yolo11env
   # On Windows
   yolo11env\Scripts\activate
   # On Linux/Mac
   source yolo11env/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Run Streamlit Web App

```bash
streamlit run app.py
```

The web interface will open in your browser (typically at `http://localhost:8501`) where you can:
- Upload images or videos for detection
- View real-time detection results
- Analyze object counts and statistics
- Download annotated outputs

### Use Pre-trained Models

The project includes pre-trained YOLOv11 models:
- `yolo11n.pt` - Nano model (fastest, lower accuracy)
- `yolo11s.pt` - Small model (balanced speed/accuracy)
- `runs/train/visdrone_yolo11s/weights/best.pt` - Fine-tuned model on VisDrone dataset

## Model Training

To train models on your own data:

```bash
from ultralytics import YOLO

# Load a pretrained model
model = YOLO('yolo11s.pt')

# Train on your dataset
results = model.train(
    data='path/to/dataset.yaml',
    epochs=100,
    imgsz=640,
    device=0  # GPU device
)
```

## Project Structure

```
yolo11-visdrone-detector/
├── app.py                          # Streamlit web application
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── yolo11n.pt                      # YOLOv11 Nano model
├── yolo11s.pt                      # YOLOv11 Small model
├── VisDrone_Dataset/              # VisDrone dataset
│   ├── VisDrone2019-DET-train/    # Training set
│   ├── VisDrone2019-DET-val/      # Validation set
│   └── VisDrone2019-DET-test-dev/ # Test set
├── runs/                          # Training and detection outputs
│   ├── train/                     # Training results
│   └── detect/                    # Detection results
└── detections_out/                # Output annotations
```

## Requirements

See [requirements.txt](requirements.txt) for complete dependencies:
- streamlit
- torch
- ultralytics
- opencv-python
- pillow
- matplotlib
- pandas
- numpy

## Performance

The fine-tuned YOLOv11s model on VisDrone dataset achieves:
- Real-time inference on drone imagery
- Optimized for aerial perspective detection
- Handles multiple object scales and occlusions

## Use Cases

- **Surveillance & Monitoring**: Real-time monitoring of large areas
- **Search & Rescue**: Rapid object detection in emergency situations
- **Precision Agriculture**: Crop and livestock monitoring
- **Infrastructure Inspection**: Bridge, building, and utility monitoring
- **Traffic Analysis**: Road and intersection monitoring from drone perspective

## Future Enhancements

- Model quantization for edge deployment
- Multi-GPU inference
- Video streaming integration
- Custom training dashboard
- API endpoint for integration

## License

This project uses VisDrone dataset under their terms. Check the dataset licensing agreement.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## Contact

For questions or support, please open an issue on the GitHub repository.

---

**Built with YOLOv11 by Ultralytics**
