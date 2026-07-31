# Project-HTW---Patient-Observation-System
This project is designed to observe and monitor patients via a live camera feed. It detects and categorizes body postures (standing, sitting, lying, etc.) and identifies whether a patient’s eyes are open or closed (sleeping/awake). Additionally, it can detect a cup near the patient’s mouth to count drinking events.
## For Users

- **Purpose**  
  This application helps in monitoring patients by:
  - **Body Position Detection**: Identifying if the patient is standing, sitting, or lying (on different sides, back, or belly).  
  - **Eye State Detection**: Determining if the patient is awake or sleeping.  
  - **Drinking Detection**: Counting how many times a patient takes a drink.

- **Usage**  
  1. **Start the Application**  
     - Upon launching, you will see a main window with a camera feed frame, status indicators (LED labels), and control buttons.  
  2. **Start/Stop Buttons**  
     - **Start**: Initiates the camera feed and begins detecting posture, eye state, and optionally drinking events.  
     - **Stop**: Halts the camera feed and resets the interface.  
  3. **Drinking Mode**  
     - **Toggle** the ‘Drinking’ button to activate or deactivate the drinking detection feature.  
  4. **Language Settings**  
     - Access the menu at the top to switch between German (DE) and English (EN).  
  5. **Status Indicators (LED labels)**  
     - These reflect the detected posture and state (sleeping/awake). When a posture is detected, the corresponding label lights up.  
  6. **Drink Counter**  
     - Displays how many times the application has detected a cup near the mouth.

---

## For Developers

### Project Structure

- **`main.py`**  
  The main entry point that initializes the GUI, sets up the menu, handles user interactions (buttons, language changes), and starts/stops camera processing threads.

- **`language.py`**  
  Manages the multilingual translation for all on-screen texts (German/English).

- **`position_detector.py`**  
  Uses the YOLO v8 pose model to detect key body points and determine posture. Mediapipe’s FaceMesh is used to analyze the eye aspect ratio to detect open/closed eyes.

- **`drink_detector.py`**  
  Uses a YOLO model for cup detection. Checks the distance between the cup and the patient’s mouth to count drinking events.

### Dependencies

1. **Python 3.8+**  
   Ensure you have a recent version of Python.
2. **OpenCV (`opencv-python`)**  
   Used for camera handling, frame processing, and image display.
3. **Mediapipe**  
   Required for FaceMesh and pose/landmark detection.
4. **Ultralytics (`ultralytics`)**  
   Contains the YOLO v8 implementation.
5. **Pillow (`PIL`)**  
   Required for handling and displaying images within the GUI.
6. **Tkinter**  
   Python’s standard GUI library (usually included in most Python installations).

### Development and Modification

- **Cloning and Setup**  
  1. Clone the repository (example):
     ```bash
<<<<<<< HEAD
     git clone https://github.com/yourusername/projekt-htw.git
=======
     git clone https://github.com/yourusername/object-recognition-system.git
>>>>>>> 8468db59ff6c6b1926dacb6f12cb364369043189
     ```
  2. Install dependencies (example using pip):
     ```bash
     pip install opencv-python mediapipe ultralytics pillow
     ```

- **Model Files**  
  - By default, the project references `yolov8n-pose.pt` for posture detection and `yolov8s.pt` for cup detection.  
  - If you train or obtain newer models, replace the paths in `position_detector.py` and `drink_detector.py`.

- **Adjusting Thresholds**  
  - To tweak sleeping detection, modify the eye aspect ratio threshold in `position_detector.py`.  
  - To change how close the cup must be to the mouth to count as a “drinking event,” adjust the `drinking_distance_threshold` in `drink_detector.py`.

### Contributing

- **Feature Requests**: Submit an issue or pull request on GitHub.  
- **Code Reviews**: All pull requests will be reviewed to maintain code quality.  
- **Testing**: Use sample video feeds or a connected webcam. Test different positions and actions (sitting, lying, drinking) for accuracy.

---

**Enjoy improving and customizing the Patient Observation System!**
