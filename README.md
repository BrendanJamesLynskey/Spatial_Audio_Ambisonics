# Spatial Audio & Ambisonics

An interactive single-file HTML application for exploring spatial audio concepts including binaural rendering, first-order ambisonics, sound field visualization, speaker configurations with VBAP panning, and HRTF exploration.

## Features

### 1. Binaural Panner
- Top-down 2D view with listener at center
- Place up to 8 sound sources by clicking the canvas
- Drag sources around the listener in real-time
- HRTF-based binaural rendering via Web Audio API `PannerNode`
- Displays azimuth and distance for each source
- Selectable distance attenuation models: inverse, linear, exponential
- Adjustable reference distance, max distance, and rolloff factor

### 2. Ambisonics Encoder/Decoder (First-Order)
- Encodes mono sources to B-format (W, X, Y, Z channels)
- Displays encoding equations: W = S, X = S cos(theta) cos(phi), Y = S sin(theta) cos(phi), Z = S sin(phi)
- Visualizes B-format polar patterns (figure-8 for X, Y, Z; omnidirectional for W)
- Shows real-time B-format channel levels
- Virtual speaker array decoder with octagonal speaker positions

### 3. Sound Field Visualization
- Animated top-down pressure field as a color map
- Shows interference patterns from multiple sources
- Frequency-dependent: adjust frequency to see wavelength changes
- Sweet spot indicator based on wavelength and speaker configuration

### 4. Speaker Configuration (VBAP)
- Presets: Stereo, Quad, 5.1, 7.1, Octagonal
- Speakers displayed on the 2D map
- Vector Base Amplitude Panning (VBAP) gain computation
- Real-time gain coefficient display for each speaker in dB

### 5. HRTF Explorer
- Visualizes ITD (Interaural Time Difference) vs azimuth using the Woodworth model
- Visualizes ILD (Interaural Level Difference) vs azimuth at 1 kHz and 4 kHz
- Current source position highlighted on ITD/ILD curves
- Cone of confusion visualization on the main canvas
- Explanation of how the brain resolves spatial ambiguity

### 6. Test Sound Sources
- **White noise** - flat spectrum random signal
- **Pink noise** - 1/f spectrum using Voss-McCartney algorithm
- **Sine tone** - adjustable frequency (60-4000 Hz)
- **Drum loop** - synthesized kick/snare/hihat pattern at 120 BPM
- **Microphone input** - live audio from system mic
- Each source independently positionable, with volume and mute controls

## Usage

1. Open `index.html` in a modern browser (Chrome, Firefox, Edge)
2. Click **START AUDIO** to initialize the Web Audio context
3. Use **headphones** for proper binaural/HRTF rendering
4. Click on the canvas to place sources, drag to reposition
5. Switch between tabs to explore different spatial audio concepts
6. Adjust controls in the left panel to modify source properties

## Controls

- **Click** on canvas: add a new source or select nearest
- **Drag** a source: reposition it in real-time
- **Shift+Click**: force add a new source
- **Scroll wheel**: zoom in/out
- Left panel: source type, frequency, volume, distance model
- Right panel: tab-specific visualizations and metrics

## Technical Details

- Built with vanilla JavaScript, HTML5 Canvas, and the Web Audio API
- Uses `PannerNode` with `HRTF` panning model for binaural rendering
- All synthesis is done in-browser (no external audio files)
- Single HTML file with no dependencies beyond Google Fonts

## Requirements

- Modern web browser with Web Audio API support
- Headphones recommended for binaural audio
- Microphone access required only for the microphone input source type
