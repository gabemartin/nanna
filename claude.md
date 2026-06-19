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

- Self-contained: `index.html` + small vendored `lib/` files (no build step, no CDN, no package manager)
- Large, clean display with very readable text
- Real-time transcription via hold-to-speak
- Hold to speak as main action
- High contrast, minimal clutter design
- Responsive for phones, tablets, and computers
- Clear error handling for browser compatibility and microphone permissions

## Current Features (v1)

- ✅ Web Speech API integration
- ✅ Hold to speak button with visual feedback
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
- ✅ Voice commands with visual feedback ("clear text" while holding)
- ✅ Dark/Light mode toggle with localStorage persistence
- ✅ Tap-to-correct: tap a word for phonetic replacement suggestions (Double Metaphone over a word list, ranked by sound-alike closeness + frequency)
- ✅ "My words": custom replacement pairs and vocabulary, persisted in localStorage

### Tap to Correct
Speech-to-text mistakes are usually *similar-sounding* words rather than typos, so a phonetic engine (not a spell-checker) drives suggestions:
- The header **✦ correct** toggle enters correction mode; words become tappable and a popover lists ranked replacements.
- Engine lives in `lib/double-metaphone.js` (vendored MIT, words/double-metaphone) + `lib/wordlist.js` (common-English candidate pool). Loaded via plain `<script src>`, exposing `doubleMetaphone` and `NANNA_WORDLIST` globals — still no build step or CDN.
- Custom terms (`nannaCustomCorrections`, `nannaCustomVocab` in localStorage) layer on top via the "My words" manager: replacement pairs always win; vocabulary is surfaced for similar-sounding words.

### Voice Commands
While holding the button to speak, you can say:
- **"clear text"** - Clears all transcribed text from the display
- When a command is recognized, a green confirmation message appears on screen
- Command phrases are automatically removed from the transcript

### Dark/Light Mode
The app includes a theme toggle for comfortable viewing in different lighting conditions:
- Click the moon (🌙) icon to switch to dark mode
- Click the sun (☀️) icon to switch back to light mode
- Your preference is automatically saved and remembered for future visits
- Smooth transitions between themes
- All UI elements adapt to the selected theme with appropriate colors and contrast

## Potential Enhancements

### User Experience
- Color theme options (additional themes beyond dark/light)
- Text history management (save/load sessions)
- Word count display
- Language selection support
- Custom color schemes for high contrast variations

### Accessibility
- Keyboard shortcuts for common actions
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

