# Sign Language to Text and Speech Conversion for Video Call Apps

## Overview

This project provides real-time sign language recognition specifically designed for **video call applications**. It overlays on platforms like Google Meet, Zoom Web, and Microsoft Teams to convert American Sign Language (ASL) fingerspelling into human-readable text and speech output.

## Key Features

- **Real-time sign language recognition** for video calls
- **Overlay interface** that works on top of video call platforms
- **Text-to-speech conversion** for seamless communication
- **Support for A-Z fingerspelling** of American Sign Language
- **Word suggestions and autocorrect** functionality
- **Cross-platform compatibility** (Windows, macOS, Linux)

## Project Components

### 1. Core Recognition Engine
- **CNN-based model** trained on hand landmark data
- **Mediapipe integration** for robust hand detection
- **8-group classification system** for improved accuracy (97%+)
- **Real-time processing** with minimal latency

### 2. Video Call Extension
- **Chrome extension** with overlay UI
- **Automatic video element detection** on call pages
- **Frame capture and processing** pipeline
- **Web-based text-to-speech** integration
- **Overlay controls** for start/stop/toggle functions

### 3. Original GUI Application
- **Standalone desktop application** with Tkinter interface
- **Live webcam feed** display
- **Real-time hand landmark visualization**
- **Text accumulation and word suggestions**
- **Built-in text-to-speech** using pyttsx3

## Architecture

```
Video Call Page (Meet/Zoom/Teams)
    ↓
Chrome Extension Overlay
    ↓
Frame Capture (largest video element)
    ↓
Backend API (Flask + TensorFlow)
    ↓
CNN Model Prediction (cnn8grps_rad1_model.h5)
    ↓
Text Output + Speech Synthesis
```

## Installation & Setup

### Prerequisites
- Python 3.9 or higher
- Webcam for local testing
- Chrome browser for extension testing

### Backend Setup
```bash
# Navigate to project directory
cd Sign-Language-To-Text-and-Speech-Conversion-master

# Install backend dependencies
pip install -r backend/requirements.txt

# Start the prediction server
python backend/server.py
```

### Chrome Extension Setup
1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select the `chrome-extension/` folder
5. The extension icon will appear in your toolbar

### Original GUI Application
```bash
# Run the standalone GUI version
python final_pred.py
```

## Usage Instructions

### For Video Call Extensions:
1. **Join a video call** on Google Meet, Zoom Web, or Teams
2. **Click the extension icon** in your Chrome toolbar
3. **Click "Start"** to begin sign language recognition
4. **Position your hand** clearly in the camera view
5. **Make sign language gestures** (A-Z fingerspelling)
6. **Watch the overlay** display recognized text in real-time
7. **Click "Speak"** to hear the accumulated sentence
8. **Use "Clear"** to reset the text buffer

### For Desktop GUI:
1. **Run the application**: `python final_pred.py`
2. **Allow webcam access** when prompted
3. **Position your hand** in the camera view
4. **Make sign language gestures** for letters A-Z
5. **View real-time predictions** in the character display
6. **See accumulated text** in the sentence area
7. **Use suggestion buttons** for word completion
8. **Click "Speak"** to hear the full sentence
9. **Click "Clear"** to reset everything

## Supported Sign Language Features

### Alphabet Recognition (A-Z)
- **A, E, M, N, S, T** (Group 1)
- **B, D, F, I, U, V, K, R, W** (Group 2) 
- **C, O** (Group 3)
- **G, H** (Group 4)
- **L** (Group 5)
- **P, Q, Z** (Group 6)
- **X** (Group 7)
- **Y, J** (Group 8)

### Special Gestures
- **Space**: Adds space between words
- **Backspace**: Removes last character
- **Next**: Advances to next word suggestion

## Technical Details

### Model Architecture
- **Convolutional Neural Network (CNN)**
- **Input**: 400x400 hand landmark skeleton images
- **Output**: 26-letter alphabet classification
- **Training**: 180 skeleton images per alphabet
- **Accuracy**: 97% (99% in optimal conditions)

### Hand Detection Pipeline
1. **Video frame capture** from webcam or call page
2. **Mediapipe hand detection** for landmark extraction
3. **Skeleton drawing** on white background
4. **CNN model prediction** for letter classification
5. **Post-processing rules** for disambiguation
6. **Text accumulation** and word formation

### Dependencies
- **TensorFlow 2.16+**: Deep learning framework
- **OpenCV**: Computer vision operations
- **Mediapipe**: Hand landmark detection
- **cvzone**: Hand tracking utilities
- **Flask**: Backend API framework
- **Tkinter**: GUI framework (desktop version)
- **pyttsx3**: Text-to-speech (desktop version)

## Supported Platforms

### Video Call Applications
- **Google Meet** (Web)
- **Zoom Web** (Browser version)
- **Microsoft Teams** (Web)
- **Other web-based video platforms**

### Operating Systems
- **Windows 10/11**
- **macOS 10.15+**
- **Linux** (Ubuntu 18.04+)

### Browsers
- **Google Chrome** (Extension)
- **Microsoft Edge** (Extension)
- **Mozilla Firefox** (Manual setup)

## Future Enhancements

- **Word-level recognition** instead of letter-by-letter
- **Real-time translation** between sign languages
- **Multi-hand gesture support** for complex signs
- **Mobile app version** for smartphones
- **Integration with popular video platforms** (native plugins)
- **Advanced language models** for better word prediction
- **Voice command integration** for hands-free control

## Contributing

This project aims to make video communication more accessible for deaf and hard-of-hearing individuals. Contributions are welcome for:

- **Model improvements** and accuracy enhancements
- **New sign language support** (ASL, BSL, etc.)
- **Platform integrations** and native plugins
- **UI/UX improvements** for better user experience
- **Performance optimizations** for real-time processing

## License

This project is developed for educational and accessibility purposes. Please ensure compliance with video platform terms of service when using the extension.

## Support

For issues, questions, or contributions, please refer to the project documentation and ensure all dependencies are properly installed for optimal performance.
