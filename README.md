## AI-Cursor — Hand-Tracking Virtual Mouse (OpenCV + MediaPipe)

AI-Cursor is a hand-gesture controlled virtual mouse that lets you move your cursor, click, drag, and perform actions without touching your physical mouse — powered by computer vision.

It uses:
- OpenCV (live camera feed)
- MediaPipe Hands (21 landmark hand-pose model)
- PyAutoGUI / pynput (mouse control)
- Custom gesture detection logic (angles + distances)

This project allows you to control your computer by simply moving your hand in front of the camera.

## 📸 Demo
### Hand Tracking Mode
![Hand Tracking](/images/image1.png)
### Cursor Moving Mode
![Cursor Moving](/images/image2.png)
### Single Click Mode
![Single Click](/images/image3.png)
### Double Click Mode
![Double Click](/images/image4.png)

## 🚀 Features
1. ✔️ Cursor Movement
- Move your index finger → moves the mouse cursor smoothly.
2. ✔️ Left Click Gesture
- Pinch gesture
- Or angle-based gesture depending on your util.py logic.
3. ✔️ Right Click Gesture
- Gesture-based trigger using finger angles.
4. ✔️ Real-Time Hand Tracking
- Uses MediaPipe’s 21 landmark model with good accuracy.
5. ✔️ Lightweight & Fast
- Works on normal webcams (30–60 FPS depending on CPU).
6. ✔️ Cross-platform
- macOS
- Windows
- Linux

## 🧠 How It Works
1. Capture Video
OpenCV grabs frames from your webcam.
2. Detect Hand Landmarks
MediaPipe Hands outputs 21 (x,y,z) coordinates per frame.
3. Extract Useful Points
You detect:
- Index fingertip
- Thumb tip
- Knuckles
- Wrist
etc.
4. Map Finger Position → Cursor Position
Hand coordinates → screen coordinates:
```bash
cursor_x = screen_width * index_finger_x
cursor_y = screen_height * index_finger_y
```
5. Detect Gestures
- Your util.py calculates:
- Finger angles
- Distances
- Pinch detection
- Up/down states
6. Trigger Mouse Actions
- PyAutoGUI or pynput performs:
- Move
- Click
- Right-click
- Drag

## 🛠️ Installation
1. Clone the Repository
```bash
git clone https://github.com/ishaan-bhalla/AI-cursor.git
cd AI-cursor
```
2. Create Python Environment (Recommended: Python 3.11)
```bash
python3.11 -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows
```
3. Install Dependencies
```bash
pip install -r requirements.txt
```
## ▶️ Usage
Simply run:
```bash
python main.py
```
Then:
- Hold your hand in front of the webcam
- Raise your index finger → move cursor
- Pinch (thumb + index) → click
- Other gestures depend on your angle logic

## 📂 Project Structure
```
AI-cursor/
├── main.py              # Main gesture mouse controller
├── util.py              # Angle + distance calculations
├── requirements.txt     # Dependencies
├── images/              # (Add your demo pictures here)
└── README.md
```
## 🔧 Technologies Used
```
|      Component       |        Technology       |
|----------------------|-------------------------|
| Programming Language |       Python 3.11       |
| Hand Tracking        |     MediaPipe Hands     |
| Computer Vision      |        OpenCV           |
| Mouse Control        |   PyAutoGUI, pynput     |
| Math / Utils         |        NumPy            |
| OS Support           |        MacOs            |
```

## ⚠️ Notes / Limitations

- Accuracy depends on lighting
- Gestures might trigger accidentally without debounce
- Cursor may jitter (no smoothing filter yet)
- Works best at 60–100 cm distance from camera
