# Football Analytica

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/) 
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)](https://opencv.org/) 
[![YOLOvx](https://img.shields.io/badge/YOLOv8-Ultralytics-orange)](https://github.com/ultralytics/ultralytics) 
[![scikit-learn](https://img.shields.io/badge/scikit--learn-0.24%2B-brightgreen)](https://scikit-learn.org/) 
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

A computer vision pipeline for automated football match analysis.

## Features

- Detect and track players, referees, and footballs using YOLOv8
- Team assignment via K-means clustering on jersey colors
- Camera motion estimation and compensation
- Perspective transformation for real-world measurements
- Player speed and distance calculations
- Custom model training capabilities

## Output
![Output](football_analysis/output_videos/screenshot.png)

## Architecture

![Architecture Diagram](football_analysis/Architecture-Diagram.png)

## Project Structure

```text
football_analysis/
├── input_videos/                   # Sample match videos
├── output_videos/                  # Processed output videos
├── models/                         # Pretrained & custom YOLO models
├── camera_movement_estimator/      # Optical flow & stabilization
├── player_ball_assigner/           # Team & ball assignment
├── speed_and_distance_estimator/   # Movement metrics
├── training/                       # Model training scripts
├── utils/                          # Helper functions
├── view_transformer/               # Perspective correction
├── main.py                         # Main pipeline
├── yolo_inference.py               # Detection-only script
├── requirements.txt                # Dependencies
├── README.md                       # Documentation
└── LICENSE                         # MIT License
```
## Installation

### Prerequisites
- Python 3.8+
- Git
- pip

### Setup
```bash
git clone https://github.com/<your-username>/football_analysis.git
cd football_analysis

python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

pip install --upgrade pip
``` 
## Usage

### Full Pipeline
```bash
python main.py \
  --input input_videos/sample_match.mp4 \
  --output output_videos/ \
  --weights models/yolov8s.pt
```
  Process includes:
- � **Object detection** - Identify players, ball, and referees using YOLOv8
- 📷 **Camera stabilization** - Compensate for camera movement via optical flow
- 👥 **Team assignment** - Cluster players by jersey colors using K-means
- ⚽ **Ball tracking** - Maintain possession statistics and trajectory
- 📏 **Metric calculation** - Compute speed, distance, and positioning
- 🎬 **Video annotation** - Generate output with visual analytics overlay

## Detection Only
```bash
python yolo_inference.py \
  --weights models/yolov5s.pt \
  --source input_videos/sample_match.mp4 \
  --save-video
  ```
  ## Sample Data
- **Input:** `input_videos/sample_match.mp4`  
- **Model:** `yolov8s.pt` *(download separately)*  
- **Output:** `output_videos/output_video.avi`  



## Technical Details

### Player Detection
- 🚀 YOLOv8 model fine-tuned on football players  
- 🌓 Handles occlusion and variable lighting conditions  

### Team Assignment
- 🎨 K-means clustering on dominant jersey colors  
- 🔄 Adaptive to different team color schemes  

### Camera Compensation
- 📹 Optical flow based stabilization  
- 📐 Perspective transformation using field markings  

### Metrics
- 🏃 **Speed:** km/h measurements  
- 📏 **Distance:** meters covered  
- 🔥 **Position heatmaps:** Player activity zones  

## Resources
- [YOLOv8 Documentation](https://github.com/ultralytics/ultralytics/blob/main/docs/en/models/yolov8.md)  
- [OpenCV Tutorials](https://docs.opencv.org/)  
- [scikit-learn Clustering](https://scikit-learn.org/stable/modules/clustering.html)  