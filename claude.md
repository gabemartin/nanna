# Nanna - Speech-to-Text App for Grandmother

## Overview

A simple, accessible speech-to-text web application designed for a deaf grandmother to read what people are saying in real-time. The app uses the Web Speech API (built into Chrome/Edge/Safari) to display spoken words on screen with large, readable text.

## Quick Start

**👉 See [README.md](README.md) for complete setup and usage instructions.**

### TL;DR - How to Run

Just open `index.html` in Chrome, Edge, or Safari. No npm, no installation needed!

### iOS/Mobile Installation

The app can be installed as a standalone web app on iOS/Android:
- iOS: Open in Safari → Share → "Add to Home Screen"
- Opens without browser UI for a clean, app-like experience
- Uses `manifest.json` and iOS meta tags for PWA support
- Respects safe areas (notch/Dynamic Island) on newer iPhones

## Core Requirements

- Single HTML file (no external dependencies)
- Large, clean display with very readable text
- Real-time transcription with continuous listening
- Clear start/stop controls
- High contrast, minimal clutter design
- Responsive for phones, tablets, and computers
- Clear error handling for browser compatibility and microphone permissions

## Current Features (v1)

- ✅ Web Speech API integration
- ✅ Start/Stop listening button with visual feedback
- ✅ Large text display (48px default, customizable)
- ✅ Font size controls (A- / A+) with localStorage persistence
- ✅ Copy to clipboard functionality
- ✅ Clear text button
- ✅ Auto-scrolling as new text appears
- ✅ Pause detection with visual separators
- ✅ Status indicator (listening/ready)
- ✅ Interim results (show words as they're being spoken)
- ✅ Error handling for common issues
- ✅ Responsive design with mobile support
- ✅ High contrast mode support
- ✅ Custom scrollbar styling
- ✅ Voice commands with visual feedback
- ✅ Dark/Light mode toggle with localStorage persistence
- ✅ Slow mode for displaying one word at a time (accessibility feature)

### Voice Commands
The app now supports hands-free control via voice commands:
- **"clear text"** - Clears all transcribed text from the display
- **"stop listening"** - Pauses transcription (text stops appearing on screen, but still listens for commands)
- **"start listening"** - Resumes transcription after being paused
- **"slow mode"** - Enables slow mode (displays one word at a time)
- **"slow mode off"** - Disables slow mode (returns to normal view)

How it works:
- When you say "stop listening", the app enters a paused state where it continues listening for voice commands but doesn't display new text on screen
- While paused, you can still say "start listening" to resume, or "clear text" to clear the display
- Say "slow mode" to switch to one-word-at-a-time display, or "slow mode off" to return to normal
- When a command is recognized, a green confirmation message appears on screen
- Command phrases are automatically removed from the transcript
- The status indicator shows "Paused" when transcription is paused

### Dark/Light Mode
The app includes a theme toggle for comfortable viewing in different lighting conditions:
- Click the moon (🌙) icon to switch to dark mode
- Click the sun (☀️) icon to switch back to light mode
- Your preference is automatically saved and remembered for future visits
- Smooth transitions between themes
- All UI elements adapt to the selected theme with appropriate colors and contrast

### Slow Mode
An accessibility feature designed for users with cognitive difficulties or reading challenges:
- Click the "Slow Mode" button to toggle this feature on/off
- When enabled, displays one word at a time in very large text (120px on desktop)
- Shows the last 3 words above the current word for context
- Perfect for users who need extra time to read and process each word
- Also displays interim results (words being spoken) in real-time
- Preference is saved to localStorage
- Works seamlessly with all other features (voice commands, dark mode, etc.)

## Potential Enhancements

### User Experience
- Color theme options (additional themes beyond dark/light)
- Text history management (save/load sessions)
- Word count display
- Language selection support
- Custom color schemes for high contrast variations

### Accessibility
- Keyboard shortcuts for common actions
- Voice commands to control the app
- Text highlighting as words are spoken
- Larger touch targets for mobile

### Technical
- Offline support with service worker
- Export transcripts (TXT, PDF)
- Automatic punctuation improvements
- Speaker labels (if multiple people are talking)
- Text-to-speech playback option

### Settings/Preferences
- Remember user preferences (theme, font, language)
- Customizable pause threshold
- Auto-clear after X minutes
- Fullscreen mode

