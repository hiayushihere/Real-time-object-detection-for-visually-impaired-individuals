# Real-Time Object Detection and Depth Estimation Assistive System

A software-based assistive solution designed to empower visually impaired individuals by providing real-time object detection, depth estimation, directional guidance, and audio feedback via a single-camera input. Built with YOLOv5 and MiDaS models, the system integrates text-to-speech (TTS) and voice commands for seamless, hands-free operation.

---

## Features

* **Real-Time Object Detection**: Utilizes YOLOv5 pre-trained weights to detect up to 80 common object classes without custom datasets.
* **Depth Estimation**: Incorporates MiDaS to compute approximate distances of detected objects in each frame.
* **Directional Guidance**: Classifies object positions into left, center, or right relative to user’s viewpoint.
* **Audio Feedback**: Converts detection results—object label, distance, and direction—into clear, actionable voice prompts using `pyttsx3`.
* **Voice Command Interface**: Allows users to start or stop live detection through simple speech commands (e.g., "Go live", "Stop the live detection").
* **OCR Text Detection (Proposed Feature)**: Partially implemented Tesseract OCR integration to read text from the environment and relay it via audio feedback.

---

## System Requirements

* Python 3.8 or above
* Webcam or external camera
* **Libraries**:

  * `ultralytics` (YOLOv5)
  * `torch` & `torchvision`
  * `opencv-python`
  * `pyttsx3`
  * `speechrecognition`
  * `pyaudio` (or `pipwin install pyaudio` on Windows)
  * `Pillow`
  * `numpy`
  * `tesseract-ocr` (for OCR feature)

> **Note**: No GPU is required, though GPU acceleration (CUDA) can improve performance.

---

## Installation

1. **Clone the repository**


2. **Install dependencies**

3. **Download pre-trained weights**

   * YOLOv5: Included via `ultralytics` package
   * MiDaS: Automatically downloaded and cached by Torch Hub

4. **Install Tesseract OCR (optional)**

   * **Ubuntu**: `sudo apt-get install tesseract-ocr`
   * **Windows**: Download installer from [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki)

---

## Usage

1. **Run the application**

2. **Voice Commands**

   * **Start Live Detection**: Say "Go live"
   * **Stop Live Detection**: Say "Stop the live detection"

3. **Output**

   * Live window displaying bounding boxes, class labels, distances, and directions.
   * Real-time audio announcements describing detected objects.

---

## Demo / Results

![Screenshot 2024-11-26 193154](https://github.com/user-attachments/assets/d8e02d76-22fa-4554-9c73-180261656473)
![Screenshot 2024-11-27 022654](https://github.com/user-attachments/assets/f9509be6-f6c8-4517-a206-1cfb5c05cc36)


During tests, the system correctly identified objects (e.g., toothbrush, scissors, person) and provided accurate audio feedback:

* "Toothbrush detected at 0.33 meters to your left."
* "Scissors detected at 0.44 meters to your left."
* "Person detected at 0.52 meters straight ahead."

Performance remained stable despite CPU-only execution, though audio latency was observed under heavy load.

---

## Challenges and Limitations

* **CPU-Only Processing**: Lack of GPU led to slower frame rates and delayed audio output.
* **Memory Constraints**: Limited RAM affected simultaneous object detection, depth computation, and OCR processing.
* **Depth Calibration**: Environmental variations (lighting, clutter) introduced minor inaccuracies in distance estimation.
* **Predefined Classes**: Reliant on YOLOv5’s 80 COCO classes; custom object recognition is not supported.

---

## Proposed Feature: OCR Text Detection

A partially implemented OCR module using Tesseract to extract and read text from the scene. Initial results were promising in high-contrast scenarios but suffered due to hardware constraints.

---

## Future Outlook

* **Hardware Acceleration**: Leverage GPU or edge devices (e.g., NVIDIA Jetson) for real-time performance.
* **Feature Expansion**: Enhance OCR robustness, integrate haptic feedback, and extend object class coverage.
* **User-Centered Testing**: Conduct field trials with visually impaired users to refine audio prompts and interface usability.

