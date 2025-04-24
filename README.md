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
```

---

## ⚙️ Installation

1. **Clone this repo**  
   ```bash
   git clone https://github.com/your-username/edge_ai_deployment.git
   cd edge_ai_deployment
   ```

2. **Create & activate a virtual environment**  
   ```bash
   python3 -m venv venv
   source venv/bin/activate    # on Windows use `venv\\Scripts\\activate`
   ```

3. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare your data**  
   - Download & extract your datasets under the appropriate `*/data/` folders.  
   - Ensure train/val/test splits exist as expected by the dataset loaders in each module.

---

## ▶️ Usage

All commands invoke `main.py`:

```bash
python main.py <task> <mode>
```

- `<task>`:  
  - `seg` — image segmentation  
  - `det` — object detection  

- `<mode>`:  
  - `train` — train the model  
  - `eval`  — evaluate on validation/test set  
  - `infer` — run inference on sample images or video  

### Examples

- **Train segmentation** with U-Net on CamVid:  
  ```bash
  python main.py seg train
  ```

- **Evaluate detection** on VOC:  
  ```bash
  python main.py det eval
  ```

- **Inference** with YOLOv5-Nano on a sample video:  
  ```bash
  python main.py det infer --source path/to/video.mp4
  ```

---

## 🛠️ Extending & Customizing

- **Add new models**  
  - Create a new `*.py` in `models/` defining a `nn.Module` class.  
  - Register your model in the corresponding `scripts/train.py` loader.

- **Implement new datasets**  
  - Under `data/`, add a custom `Dataset` class for loading images & labels.  
  - Update `scripts/train.py` to import & instantiate your dataset.

- **Export & Optimize**  
  - Inside each `scripts/`, you can add export routines to ONNX or TensorRT.  
  - Insert post-training quantization or pruning workflows as needed.

- **Logging & Metrics**  
  - Integrate TensorBoard / Weights & Biases in `scripts/train.py` and `evaluate.py`.  
  - Compute mIoU for segmentation and mAP for detection.

---

## 📚 References

- **Segmentation Architectures**:  
  - U-Net, FastSCNN, BiSeNet, ENet, LEDNet  
- **Detection Architectures**:  
  - YOLOv5-Nano, SSD-Lite, EfficientDet-Lite0, MobileNet-SSD, NanoDet  
- **Datasets**:  
  - [CamVid](https://github.com/alexgkendall/SegNet-Tutorial)  
  - [Cityscapes](https://www.cityscapes-dataset.com/)  
  - [Pascal VOC](http://host.robots.ox.ac.uk/pascal/VOC/)  
  - [COCO](https://cocodataset.org/)

---

## 🤝 Contributing

1. Fork this repository  
2. Create your feature branch (`git checkout -b feature/YourFeature`)  
3. Commit your changes (`git commit -m "Add YourFeature"`)  
4. Push to the branch (`git push origin feature/YourFeature`)  
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

