# 🦠 Face Mask Detection and Tracking with MobileNetV2-SSD and ROS

## 📌 Overview

This project presents a practical deep learning and robotics pipeline for detecting unmasked individuals using a lightweight neural network and tracking them in real-time using ROS (Robot Operating System). Initiated in the context of the COVID-19 pandemic, the aim is to ensure mask compliance in public spaces through automated visual inspection and alert mechanisms.

---

## 🎯 Motivation

With the global outbreak of COVID-19, monitoring mask usage became critical for public health. This project aims to support such efforts by leveraging deep learning (MobileNetV2 + SSD) and ROS to build a low-power, real-time detection system that alerts or tracks people not wearing masks correctly.

---

## 🧠 Methodology

- **Face Detection:** MTCNN is used to locate faces in the frame.
- **Mask Classification:** MobileNetV2-SSD classifies faces as masked or unmasked.
- **Tracking:** If an unmasked face is detected, a robot tracks the subject using the KCF tracking algorithm.
- **Heatmap Visualization:** Activation heatmaps are used to understand the model’s internal attention and failure points.

---
## 🗂️ Project Structure

```
face-mask-detection-tracking/
├── face_detector/             # Pre-trained MobileNetV2-SSD face mask detection model
│   └── mask-detector.model
├── detect_cam.py              # Main webcam inference script
├── heatmap_cam.py             # Optional: CAM visualization support
├── tfrecord.py                # Dataset to TFRecord conversion utility
├── xml_to_csv.py              # Label conversion for training
├── output.avi                 # Sample output video with detections
├── requirements.txt           # Python dependencies
├── LICENSE
└── README.md
```

## ⚙️ Dependencies

- Python 3.7+
- OpenCV
- PyTorch
- MTCNN
- TensorFlow (optional)
- ROS (Noetic/Melodic)

Install the required Python packages:
```bash
pip install opencv-python torch torchvision facenet-pytorch
```

---

## 🚀 Running the Project

### 1. Run Inference on Webcam:
```bash
python detect_cam.py
```

### 2. Convert Annotations:
```bash
python xml_to_csv.py
```

### 3. Generate TFRecord:
```bash
python tfrecord.py
```

### 4. Generate Heatmap (optional visualization):
```bash
python heatmap_cam.py
```
---

## 📄 Report


You can read the full final project report [here](https://drive.google.com/file/d/1I6Oe_XAt5WJirAt_QgipY5Qrbt3nApZ8/view?usp=sharing).
---

## 🧪 Datasets

Public datasets used for training and evaluation:

- [AIZOO Dataset](https://drive.google.com/file/d/1QspxOJMDfrAWVV7AUNc0rjo1EPEDW/view)
- [RMFD Dataset](https://drive.google.com/open?id=1UlOk6EtiaXTHylRUx2mySgvJX9ycoeBp)
- [Face Mask Detection Dataset](https://drive.google.com/open?id=1UlOk6EtiaXTHylRUx2mySgvJX9ycoeBp)

---

## 🧠 Insights from Heatmaps

The heatmaps revealed the following:

- The model attends to **nose regions** in frontal views and **cheeks** in side views.
- Layers with **low activation** suggest under-utilization.
- Head motion and blur lead to **false negatives**, revealing robustness challenges.

---

## 📌 Limitations & Future Work

- Detection accuracy drops significantly under fast motion or occlusion.
- Future work may explore YOLOv5 or MobileNetV3 for better trade-offs.

---

## 🧾 References

[1] Howard et al., "Searching for MobileNetV3", arXiv:1905.02244  
[2] MTCNN for face detection: https://github.com/ipazc/mtcnn  
[3] MobileNetV2-SSD implementation: https://github.com/tongyuhome/MobileNetv2-SSD

---

## 🪪 License

This project is released under the MIT License. See [LICENSE](./LICENSE) for more.
