🎨 Interactive Projection Mapping on a Wooden Portrait

An interactive projection mapping installation that merges art and computation.
A wooden portrait framed on the wall comes alive through gesture and sound-based control,
reacting in real time to the user’s hand movements and environmental audio.

🧠 Concept

This project transforms a painted wooden face portrait into a living canvas using projection mapping.
Users can interact naturally:

🖐️ Pinch Gesture (via webcam) → Adjusts the brightness (0–100) of the projection

👏 Clap / Sound Detection → Modifies the contrast level dynamically

🌈 A live projected UI slab (1–100) shows the current brightness level beside the portrait

The result: a seamless blend of physical art, light, and interactivity —
where visuals evolve in response to the user and the environment.

🧱 System Architecture

The projection system is built in TouchDesigner and structured into 14 Base COMPs,
each representing a unique visual region of the wooden portrait.

Every base handles a different section (e.g., cheeks, forehead, eyes, background, frame),
and contains around 10 internal modules to manage visual states and effects.

🧩 Inside Each Base
Component Type	Function
Timer / Count CHOPs	Control timed transitions and animation cycles
Switch / Layer / Feedback TOPs	Handle active texture layers and feedback loops
Level TOPs	Dynamically adjust brightness & contrast
Null TOPs	Output processed textures to the global composite
Res TOPs	Scale visuals to correct projection size
🌐 Global Interaction Flow
Input Source	Processing	Visual Effect
🖐️ Hand (Webcam)	MediaPipe HandPose → Pinch distance mapping	Adjusts brightness (0–100)
🎤 Sound (Microphone)	Audio amplitude thresholding	Toggles or adjusts contrast

Each input is processed via Python scripts and transmitted to TouchDesigner (via CHOP input or OSC).
TouchDesigner then distributes these values to all 14 bases simultaneously.

🧩 TouchDesigner Network Overview

The .toe file defines a modular structure connecting interaction data to projection visuals.

Input Feed: Static portrait texture or live camera feed.

Interaction CHOPs: Receive values from Python (brightness & contrast).

Processing: Math, Level, and Composite TOPs apply real-time adjustments.

UI Layer: Overlays a 1–100 brightness indicator slab.

Output: Combines all 14 Base outputs into a single projection mapped image.

🛠️ Technologies Used
Tool / Library	Role
TouchDesigner (.toe)	Projection mapping, composition, and real-time rendering
MediaPipe (HandPose model)	Hand tracking for brightness control
Python (OpenCV, NumPy)	Interface between interaction and projection system
Sounddevice / PyAudio	Detecting claps or environmental sound triggers
Git LFS	Storing large TouchDesigner .toe project files
Projector + Wooden Frame Setup	Physical display and calibration environment
📁 Repository Structure
projection-mapping-interactive/
├── final_demo.toe            # Main TouchDesigner project
├── hand_interaction.py       # MediaPipe-based brightness control
├── audio_detection.py        # Sound-based contrast control
├── doc/
│   ├── Screenshot 2025-10-23 094223.png
│   ├── Screenshot 2025-10-23 094601.png
│   └── architecture_diagram.png (optional)
├── media/                    # Portrait textures or videos
├── README.md                 # Documentation (this file)
└── .gitattributes            # Git LFS tracking for .toe

🚀 How to Run

Clone the repository

git clone https://github.com/Bhanupal22600/projection-mapping-interactive.git
cd projection-mapping-interactive
git lfs pull


Install dependencies

pip install mediapipe opencv-python numpy sounddevice


Run interaction scripts

python hand_interaction.py
python audio_detection.py


Open the TouchDesigner project

Launch final_demo.toe

Link the CHOP inputs to your brightness & contrast parameters

Start your projector and align visuals with the wooden portrait frame

Enjoy the interactive experience! ✨

🔮 Future Enhancements

Add face tracking to align visuals dynamically

Introduce multi-mode filters or visual effects

Extend with voice-based or OSC network control

Create a mobile UI for manual calibration

👨‍💻 Author

Bhanupal Singh
📍 IIIT-Delhi
🎓 Independent Design Project (2025)
🖥️ Interactive Projection Mapping on a Wooden Portrait

📸 Preview
Setup	Projection