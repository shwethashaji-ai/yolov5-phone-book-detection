# yolov5-phone-book-detection
Real-time webcam object detection of mobile phones and books using YOLOv5 in Google Colab, with bounding boxes, live counts, CSV logging and snapshots.
# 📱📖 Real-Time Phone & Book Detection with YOLOv5

A real-time object detection project that uses a webcam in Google Colab to detect **mobile phones** and **books**, draws bounding boxes with confidence scores, shows live counts, and logs every detection to a CSV file for analysis.

![Demo](demo.gif)
<!-- Add a screen recording or GIF of the detection running -->

## ✨ Features
- Detects **cell phones** and **books** using a pretrained YOLOv5 model (COCO dataset)
- Bounding boxes with class labels and confidence scores
- Live on-screen counter (objects in view now) and running total of appearances
- Automatic **CSV logging** of detections (timestamp, class, confidence, box coordinates)
- Automatic **snapshots** whenever the detected objects change
- Tuned for **small objects**: medium model, lower confidence threshold, higher input resolution, HD camera frames
- Log analysis with pandas and matplotlib

## 🛠️ Tech Stack
Python · PyTorch · YOLOv5 · OpenCV · NumPy · pandas · Matplotlib · Google Colab

## 🚀 How to Run
1. Open the notebook in Google Colab: [Open in Colab](your-colab-link)
2. Set the runtime to **GPU** (Runtime → Change runtime type → T4 GPU).
3. Run the cells in order:
   1. Install dependencies
   2. Load the model
   3. Start live detection (allow camera access in the browser)
   4. Analyze the detection log
   5. Download the results
4. Hold a phone or book 0.3–1.5 m from the camera in good lighting.
5. Stop the cell to end detection. The camera turns off automatically.

## ⚙️ Configuration
| Setting | Default | Purpose |
|---|---|---|
| `model.conf` | 0.20 | Confidence threshold (lower finds more small objects, but adds false positives) |
| `model.classes` | `[67, 73]` | COCO class IDs: 67 = cell phone, 73 = book |
| `IMG_SIZE` | 1280 (GPU) / 960 (CPU) | Inference resolution (higher helps small objects but is slower) |
| `LOG_EVERY` | 2 s | Minimum gap between CSV log writes |

To detect other COCO objects, change `model.classes`, or set it to `None` for all 80 classes.

## 📂 Output
- `detections_log.csv`: timestamp, class, confidence, x1, y1, x2, y2
- `snapshots/`: images saved when the detected objects change

## ⚠️ Limitations
- Uses the pretrained COCO "book" class, so small, thin, or edge-on books can be missed.
- Detection runs on single frames sent from the browser, so frame rate depends on the runtime (a few FPS on CPU, higher on GPU).
- Performance depends on lighting, distance, and background.

## 🔮 Future Improvements
- Fine-tune YOLOv5 on a custom dataset of small books for better accuracy
- Streamlit web app for image and video upload
- Deploy as a local real-time app with OpenCV
- Add evaluation metrics (precision, recall, mAP) on a labeled test set

## 📄 License
This project is released under the MIT License. YOLOv5 is licensed under AGPL-3.0, so check its terms if you plan to use this commercially.

## 👤 Author
**Shwetha** 
