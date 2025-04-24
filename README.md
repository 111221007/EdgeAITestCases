# EdgeAITestCases
# Edge AI Deployment

**Efficient Edge AI Model Deployment for Real-Time Inference**  
*A focus on latency reduction in autonomous systems and smart IoT applications*

---

## 🚀 Project Overview

This repository provides a modular Python framework for training, evaluating, and running inference on multiple lightweight Edge AI models:

- **Image Segmentation** (e.g. U-Net, FastSCNN, BiSeNet, ENet, LEDNet)  
- **Object Detection** (e.g. YOLOv5-Nano, SSD-Lite, EfficientDet-Lite0, MobileNet-SSD, NanoDet)

Each task lives in its own module (`image_segmentation/` and `object_detection/`), with clear separation of:

- `models/` — model definitions  
- `scripts/` — training / evaluation / inference entrypoints  
- `data/` — dataset storage  

A unified `main.py` lets you launch any module in **train**, **eval**, or **infer** mode.

---

## 📁 Repository Structure

```text
edge_ai_deployment/
├── README.md              ← this file
├── requirements.txt       ← Python dependencies
├── main.py                ← CLI entrypoint
│
├── image_segmentation/    ← Image-segmentation module
│   ├── models/            ← model architectures
│   │   ├── unet.py
│   │   ├── fast_scnn.py
│   │   ├── bisenet.py
│   │   ├── enet.py
│   │   └── lednet.py
│   ├── scripts/           ← training / evaluation / inference
│   │   ├── train.py
│   │   ├── evaluate.py
│   │   └── infer.py
│   └── data/              ← datasets (e.g. CamVid, Cityscapes)
│       ├── camvid/
│       └── cityscapes/
│
└── object_detection/      ← Object-detection module
    ├── models/            ← model architectures
    │   ├── yolov5_nano.py
    │   ├── ssd_lite.py
    │   ├── efficientdet_lite0.py
    │   ├── mobilenet_ssd.py
    │   └── nanodet.py
    ├── scripts/           ← training / evaluation / inference
    │   ├── train.py
    │   ├── evaluate.py
    │   └── infer.py
    └── data/              ← datasets (e.g. Pascal VOC, COCO subset)
        ├── voc/
        └── coco_subset/
