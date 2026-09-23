# 🚗 Safe Driving — Real-Time Driver Monitoring

Computer Vision project for real-time driver monitoring using YOLOv8.

The system detects:
- 📱 Mobile phone usage
- ✅ Seatbelt
- ⚠️ No seatbelt
- 🚘 Windshield

It also uses temporal smoothing to improve detection stability in video streams.

---

## 🎯 Project Objective

The objective of this project is to develop a computer vision system capable of monitoring a driver's behavior from video.

The system combines object detection and temporal analysis to reduce unstable predictions between consecutive video frames.

---

## 🧠 Technologies

- Python
- YOLOv8
- Ultralytics
- OpenCV
- PyTorch
- Jupyter Notebook
- Roboflow
- Computer Vision

---

## 🏗️ System Pipeline

Video
↓
Frame extraction with OpenCV
↓
YOLOv8 object detection
↓
Seatbelt / No Seatbelt / Mobile classification
↓
Temporal smoothing
↓
Final driver status

---

## 📊 Dataset

The project uses a custom annotated dataset containing:

- Mobile
- Seatbelt
- No Seatbelt
- Windshield

The dataset was progressively improved through several versions.

### Dataset versions

| Version | Main objective |
|---|---|
| V1 | Seatbelt + mobile detection |
| V2 | Introduction of `no_seatbelt` |
| V3 | Enrichment of `no_seatbelt` annotations |

The datasets are not included in this repository.

---

## 🤖 Model

The project uses YOLOv8 Nano with transfer learning from pretrained weights.

Training configuration:

- Model: YOLOv8n
- Image size: 640 × 640
- Epochs: up to 50
- Batch size: 16
- Device: CPU

---

## 📈 V3 Results

Performance on the held-out test set:

| Class | Precision | Recall | mAP@50 |
|---|---:|---:|---:|
| Mobile | 75.6% | 81.6% | 79.4% |
| No Seatbelt | 46.7% | 67.7% | 48.2% |
| Seatbelt | 93.1% | 95.1% | 96.8% |
| Windshield | 99.5% | 100% | 99.5% |

Overall:

- Precision: 78.7%
- Recall: 86.1%
- mAP@50: 81.0%
- mAP@50-95: 46.0%

> These metrics were obtained on the project's test split and should not be interpreted as real-world accuracy.

---

## 🎥 Video Detection

OpenCV is used to:

1. Read the video frame by frame
2. Send each frame to YOLOv8
3. Retrieve detections
4. Annotate the frame
5. Apply temporal smoothing
6. Generate the final output video

---

## 🔄 Temporal Smoothing

To reduce unstable predictions between consecutive frames, the system maintains a sliding window of recent detections.

A status is confirmed only after a sufficient number of positive detections within the temporal window.

This reduces rapid transitions such as:

`SEATBELT → NO SEATBELT → SEATBELT`

caused by individual frame-level predictions.

---

## 🚀 Future Improvements

- Improve `no_seatbelt` detection
- Add more real-world driving videos
- Improve robustness to different camera angles and lighting conditions
- Test larger YOLO models
- GPU training
- Driver-specific region of interest
- Object tracking
- Real-time dashboard with Streamlit

---

## 👨‍💻 Author

Ahmed Abida

Computer Engineering Student  
AI & Computer Vision
