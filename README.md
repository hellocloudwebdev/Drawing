# Air Draw — Gesture-Based Interactive Doodler

A gesture-based interactive drawing application powered by **MediaPipe** hand tracking and **Vite**. Draw in the air using natural hand gestures through your webcam!

**Made by: oae_neeraj**

## 🎨 Features

### Gesture Controls
- **Index Finger (Drawing Mode)** ☝️ - Draw smooth, glowing lines in the air
- **Open Palm (Eraser Mode)** ✋ - Erase strokes with your open hand
- **Pinch Gesture (Grab & Move)** 🤏 - Grab and reposition drawn strokes
- **Fist (Idle)** ✊ - Neutral gesture state

### Drawing Features
- **Multiple Colors** - Cyan, Magenta, Lime, Electric Blue, Hot Pink
- **Adjustable Thickness** - Control brush stroke width (1-20px)
- **Glow Intensity** - Add neon glow effects to your drawings (0-100%)
- **Particle Effects** - Visual feedback while drawing
- **Multiple Canvas Layers** - Camera feed, drawing, and UI overlays
- **Hand Skeleton Overlay** - View detected hand landmarks and tracking

### UI Controls
- **Color Palette** - Quick color selection
- **Thickness Slider** - Adjust brush size
- **Glow Slider** - Control glow intensity
- **Camera Toggle** - Switch between full, dim, or dark canvas
- **Undo** - Remove the last stroke
- **Clear** - Clear all drawings
- **Save** - Export drawing as PNG image
- **Hand Tracking HUD** - Real-time gesture indicator

### Audio Feedback
- Subtle sound effects for drawing start/end, erasing, grabbing, and mode switches
- Enhances interactive experience without being intrusive

## 🛠️ Tech Stack

- **Frontend Framework**: Vanilla JavaScript (ES Modules)
- **Build Tool**: Vite 5.4.0
- **Hand Detection**: MediaPipe Hand Landmarker (v0.10.18)
- **Styling**: CSS3 with animations and gradients
- **Canvas API**: For rendering drawings and graphics
- **Web APIs**: 
  - getUserMedia (Webcam access)
  - Web Audio API (Sound effects)
  - Canvas 2D Context

## 📋 Installation

### Prerequisites
- Node.js (v18.0.0 or higher)
- Modern web browser with webcam support
- Camera permissions enabled

### Setup

```bash
# Clone the repository
git clone https://github.com/hellocloudwebdev/Drawing.git
cd Drawing

# Install dependencies
npm install

# Start development server
npm run dev

# Open browser at http://localhost:5173
```

### Build for Production

```bash
npm run build
```

## 🎮 How to Use

1. **Allow Camera Access** - Grant camera permission when prompted
2. **Start Drawing** - Point your index finger at the camera (drawing mode)
3. **Select Colors** - Click color swatches in the toolbar
4. **Adjust Settings** - Use sliders to change thickness and glow
5. **Erase** - Open your palm to erase strokes
6. **Move Strokes** - Pinch and drag to reposition drawings
7. **Save Your Work** - Click the save button to download as PNG
8. **Camera Toggle** - Cycle between full camera, dim, or dark canvas

## 📁 Project Structure

```
Drawing/
├── main.js              # Core application logic
├── index.html           # HTML markup and UI
├── index.css            # Styling and animations
├── logo.png             # Application logo
├── vite.config.js       # Vite configuration
├── package.json         # Project metadata and dependencies
└── README.md            # This file
```

## 🔧 Core Functions

### Hand Detection & Gesture Recognition
- `initMediaPipe()` - Initialize MediaPipe Hand Landmarker
- `detectGesture(landmarks)` - Classify hand gestures from landmark positions
- `stabilizeGesture(rawGesture)` - Stabilize gestures across frames

### Drawing Engine
- `handleDrawing(landmarks)` - Process index finger drawing mode
- `handleErasing(landmarks)` - Process palm eraser mode
- `handleGrab(landmarks)` - Process pinch and grab interactions
- `drawGlowStroke(ctx, stroke)` - Render strokes with glow effects
- `redrawStrokes()` - Redraw all stored strokes

### Rendering
- `renderLoop()` - Main animation loop using requestAnimationFrame
- `drawHandSkeleton(ctx, landmarks)` - Render hand tracking overlay
- `drawCursorIndicator(ctx, landmarks, gesture)` - Show drawing cursor
- `updateAndDrawParticles(ctx)` - Animate particle effects

### Audio
- `playTone(freq, duration, type, volume)` - Generate sound effects
- Audio events for drawing, erasing, and mode switches

### Utilities
- `getLandmarkPos(landmark)` - Convert MediaPipe coordinates to canvas space
- `smoothPosition(rawPos)` - Apply position smoothing for stable drawing
- `findNearestStroke(pos)` - Locate closest stroke for grab interactions
- `lightenColor(hex, amount)` - Calculate lighter color variants

## 🎯 Gesture Detection Details

### Index Finger (Drawing)
- Index tip extended above PIP joint
- All other fingers curled down
- Used for drawing smooth lines

### Open Palm (Eraser)
- All fingers extended upward
- Thumb open outward
- Used for erasing strokes with circular brush

### Pinch (Grab & Move)
- Thumb tip close to index tip (<0.06 distance)
- Other fingers curled
- Used for selecting and moving strokes

### Fist (Idle)
- All fingers curled down
- Safe neutral state

## 🚀 Performance Optimizations

- **Gesture Stabilization** - Requires 3-4 consistent frames before gesture switch to prevent jitter
- **Position Smoothing** - Applies exponential smoothing (factor: 0.35) to drawing positions
- **Stroke Segmentation** - Eraser works by splitting strokes into segments outside the eraser radius
- **Canvas Layer System** - Separates camera, drawing, and UI for efficient redrawing
- **Particle Pooling** - Particles created and destroyed dynamically

## 🔐 Privacy & Permissions

- Camera feed is processed locally in your browser
- No data is sent to external servers
- MediaPipe models run client-side via WebAssembly

## 📝 License

Open source project for creative and educational use.

## 🙏 Credits

**Developer**: oae_neeraj  
**Hand Detection**: [Google MediaPipe](https://mediapipe.dev/)  
**Build Tool**: [Vite](https://vitejs.dev/)

---

**Enjoy drawing in the air! ✨**
