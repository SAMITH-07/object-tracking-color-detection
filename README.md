# Object Tracking Based on Color Detection

A real-time object tracking system that detects and tracks objects based on their color using OpenCV and computer vision techniques.

## 🎯 Features

- **Real-time Color Detection**: Tracks objects based on HSV color values
- **Live Camera Feed**: Uses webcam for real-time tracking
- **Directional Commands**: Outputs movement commands based on object position
- **Color Calibration Tool**: GUI application to calibrate HSV values for different colors
- **Visual Feedback**: Draws tracking circles and position indicators

## 📁 Project Structure

```
object-tracking-color-detection/
├── main.py                     # Main tracking application
├── colorCalibrationforHSV.py   # HSV color calibration tool
├── README.md                   # Project documentation
└── .gitignore                  # Git ignore file
```

## 🚀 Installation

### Prerequisites
- Python 3.7+
- OpenCV
- imutils
- NumPy
- PIL (Pillow)
- tkinter (usually comes with Python)

### Install Dependencies
```bash
pip install opencv-python imutils numpy pillow
```

## 🎮 Usage

### Step 1: Calibrate Color Values (Optional but Recommended)
Run the color calibration tool to find optimal HSV values for your target color:

```bash
python colorCalibrationforHSV.py
```

**Features:**
- Interactive HSV sliders
- Preset buttons for Red, Green, Blue
- Live camera preview with color masking
- Screenshot capability for static calibration

### Step 2: Run the Main Tracking System
```bash
python main.py
```

**Controls:**
- Press 'q' to quit the application
- The system will print directional commands based on object position

## 🎯 How It Works

1. **Camera Capture**: Continuously captures frames from webcam
2. **Color Processing**: Converts frames to HSV color space
3. **Color Masking**: Creates binary mask for target color range
4. **Contour Detection**: Finds objects matching the color
5. **Object Tracking**: 
   - Draws circle around detected object
   - Calculates center position and radius
   - Outputs directional commands

## 📊 Movement Logic

The system outputs commands based on object position in the frame:

| Command | Condition | Description |
|---------|-----------|-------------|
| **Right** | x < 150 | Object on left side |
| **Left** | x > 450 | Object on right side |
| **Front** | radius < 250 | Object centered but far |
| **Stop** | radius > 250 | Object too close |

## 🎨 Color Configuration

Default configuration tracks red objects:
```python
redLower = (98, 48, 86)
redUpper = (163, 255, 255)
```

Use the calibration tool to find optimal values for your specific color and lighting conditions.

## 📸 Example Use Cases

- **Robotics**: Object following and navigation
- **Automation**: Color-based sorting systems
- **Security**: Tracking specific colored objects
- **Education**: Computer vision learning projects
- **Gaming**: Motion tracking applications

## 🔧 Troubleshooting

### Camera Not Found
- Change camera index in `main.py` (line 7):
  ```python
  camera = cv2.VideoCapture(0)  # Try 0, 1, 2, etc.
  ```

### Poor Detection
- Adjust HSV values using the calibration tool
- Ensure good lighting conditions
- Check if the target color is distinct from background

### Performance Issues
- Reduce frame width in `main.py` (line 13):
  ```python
  frame = imutils.resize(frame, width=600)  # Reduce from 1000
  ```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source. Feel free to use, modify, and distribute.

## 👤 Author

**SAMITH-07**
- GitHub: [SAMITH-07](https://github.com/SAMITH-07)

## 🙏 Acknowledgments

- OpenCV community for computer vision tools
- imutils library for convenient image processing functions

---

**Note**: This project requires a webcam to function properly. Make sure your camera is connected and not being used by other applications.
