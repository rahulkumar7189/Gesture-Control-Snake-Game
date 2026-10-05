# Gesture-Control-Snake-Game

<p align="center">
  <img src="https://socialify.git.ci/rahulkumar7189/Gesture-Control-Snake-Game/image?font=Source+Code+Pro&language=1&name=1&owner=1&pattern=Circuit+Board&stargazers=1&theme=Dark" alt="Gesture Control Snake Game Banner">
</p>

<p align="center">
  <strong>Play the classic Nokia Snake game using nothing but your hand gestures!</strong>
</p>


## 📖 Overview

This project brings the iconic Nokia Snake game to life with modern computer vision technology. Using OpenCV and MediaPipe for real-time hand tracking, you can control the snake with intuitive swipe gestures, activate speed boosts with pinch gestures, and restart the game—all without touching your keyboard! Experience the nostalgic Nokia-green theme combined with cutting-edge gesture recognition.

**Two windows will open when you run the game:**
- **Pygame window**: The classic snake game with nostalgic graphics
- **OpenCV window**: Real-time webcam feed showing hand tracking visualization

---

## ✨ Features

- **🎯 Gesture-Based Control**: Control the snake's direction (Up, Down, Left, Right) using real-time hand swipe gestures
- **⚡ Speed Boost**: Pinch your thumb and index finger together to activate a temporary speed boost
- **🔄 Gesture-Based Restart**: Show an 'UP' gesture after "Game Over" to restart instantly
- **🎨 Nostalgic Graphics**: Classic Nokia-style monochrome green graphics with blocky snake segments and 3D-effect head
- **👁️ Visual Feedback**: Separate OpenCV window displays your webcam feed with MediaPipe's hand landmarks overlaid
- **💥 Particle Effects**: Satisfying particle burst animation when the snake eats fruit
- **🚀 Multi-Threaded Architecture**: Game logic (Pygame) and gesture detection (OpenCV/MediaPipe) run on separate threads for smooth, lag-free performance

---

## 🛠️ Tech Stack

- **Python 3.8+**
- **Pygame**: Core game logic, rendering, and window management
- **OpenCV**: Webcam capture and video processing
- **MediaPipe**: Real-time hand landmark detection and gesture recognition
- **NumPy**: High-performance numerical operations

---

## 🚀 Getting Started

A setup script is included to make installation easy!

### 1. Clone the Repository

```bash
git clone https://github.com/rahulkumar7189/gesture-control-snake-game.git
cd gesture-control-snake-game
```

### 2. Create a Virtual Environment (Recommended)

**For Windows:**
```bash
python -m venv venv
.\venv\Scripts\activate
```

**For macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Run the Setup Script

This script will automatically check for and install all required libraries (`pygame`, `opencv-python`, `mediapipe`, `numpy`).

```bash
python setup.py
```

### 4. Run the Game!

Once setup is complete, launch the game:

```bash
python main.py
```

**Note:** Make sure your webcam is connected and has permission to be used.

---

## 🎮 How to Play (Controls)

| Gesture | Action |
|---------|--------|
| **Move Hand (Swipe)** | Move your entire hand in the direction you want the snake to go (UP, DOWN, LEFT, RIGHT) |
| **Pinch (Speed Boost)** | Pinch your thumb and index finger together to make the snake move faster |
| **Show 'UP' Gesture** | After a Game Over, make an 'UP' gesture to restart the game |
| **ESC Key** | Press ESC on the Pygame window to quit the game |

---

## 📁 File Structure

```
.
├── .gitignore
├── LICENSE
├── README.md                  ← You are here!
├── gesture_controller.py      ← Handles webcam, MediaPipe detection, and gesture logic
├── main.py                    ← Main entry point. Manages threads and combines game + gestures
├── setup.py                   ← Installation script to set up dependencies
└── snake_game.py              ← The Pygame snake game logic and rendering
```

---

## 🧠 How It Works

The application uses a **multi-threaded architecture** to ensure high performance:

### Main Thread (`main.py`)
- Runs the Pygame game loop
- Listens for Pygame events (like ESC key)
- Receives the latest gesture commands (e.g., `Direction.UP`, `is_speed_boost`) from the gesture thread
- Calls `game.update()` and `game.draw()` at a fixed framerate

### Gesture Thread (`main.py` → `gesture_controller.py`)
- Runs a separate loop that continuously captures frames from the webcam using `cv2`
- Processes each frame with MediaPipe to find hand landmarks
- Calculates swipe gestures based on hand movement and pinch gestures based on finger distance
- Updates a shared `GameManager` state that the main thread can read
- Displays the annotated webcam feed in a separate "Gesture Control" window

**Why Multi-Threading?**  
This design prevents the computationally-heavy computer vision and machine learning models from blocking or lagging the Pygame game loop, resulting in a smooth, responsive gaming experience.

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

<p align="center">Made with ❤️ by <a href="https://github.com/rahulkumar7189">rahulkumar7189</a></p>
