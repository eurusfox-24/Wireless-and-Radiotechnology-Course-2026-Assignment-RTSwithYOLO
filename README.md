# Intelligent Home Monitoring System (Localhost Implementation)

## Team Information
* **Laptop A (Camera/Sender) & Laptop B (AI Node/Receiver):** Both roles were executed on a single machine (localhost) for this implementation instead of working in pairs.

## System Configuration
* **Sender IP Address:** `127.0.0.1` (localhost)
* **Stream URL:** `http://127.0.0.1:5000/video_feed`

## Execution Steps

### 1. Starting the Video Stream
The video stream was initiated using Flask and OpenCV to capture the local webcam.
Run the following command in the first terminal:

```bash
python app.py
```
This started the local web server broadcasting the webcam feed on port 5000.

### 2. Running YOLO Detection
In a separate, second terminal window on the same machine, the YOLO object detection script was executed:

```bash
python yolo_stream.py
```
**Note:** The `STREAM_URL` in `yolo_stream.py` was modified to `http://127.0.0.1:5000/video_feed` to properly capture the local stream.

## Results & Detections
* **Objects Detected:** Person, cell phone, cup *(Note: update this list based on what was actually detected in your webcam feed)*.

YOLOv8 successfully captured the incoming localhost video stream frame-by-frame, applying bounding boxes and confidence labels to identified objects in real time.

## Troubleshooting & Fixes
* **Problem:** Adapting the two-laptop network requirement to a single PC setup.
* **Fix:** Used the local loopback address (`127.0.0.1`) as the target IP. It was also necessary to run the scripts in two entirely separate terminal instances so the Flask server could run continuously in the background while the YOLO script processed the stream.

## Proof of Execution

(LaptopA/flaskStream.png) Flask terminal running and/or browser showing `http://127.0.0.1:5000/video_feed`.
* **[Screenshot 2]:** YOLO "Home Monitoring" window actively showing bounding boxes around detected objects.
