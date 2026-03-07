# Nanna - Speech-to-Text App

A simple, accessible real-time speech-to-text web application built for a deaf grandmother to read what people are saying. Uses the Web Speech API built into modern browsers — no installation, no dependencies, no server required.

**[Open the app](https://gabemartin.github.io/nanna/)**

## How to Run

**Just open the [hosted site](https://gabemartin.github.io/nanna/) in Chrome, Edge, or Safari.** Or download `index.html` and open it locally — no install needed.

No npm, no build step, no dependencies. The entire app is a single HTML file.

## Browser Compatibility

The Web Speech API is required. Supported browsers:

| Browser | Support |
|---------|---------|
| Chrome (desktop) | Full support |
| Edge (desktop) | Full support |
| Safari (desktop) | Full support |
| Safari (iOS) | Full support |
| Firefox | Not supported |
| Chrome (Android) | Full support |

A microphone is required. The browser will prompt for permission on first use.

> **Note:** Chrome/Edge may require an internet connection for speech recognition even though the app itself runs offline. Safari works fully offline.

## Installing as a Mobile App (PWA)

The app can be installed as a standalone web app on iOS and Android:

- **iOS:** Open in Safari → Share button → "Add to Home Screen"
- **Android:** Open in Chrome → menu → "Add to Home Screen" or "Install app"

Once installed, it opens without browser chrome for a clean, app-like experience. The app respects safe areas (notch/Dynamic Island) on newer iPhones.

## Features

### Core
- **Hold to speak** — press and hold the button to transcribe; release to stop
- Interim results — words appear as they're being spoken, then finalize
- Pause detection — a visual separator is inserted after ~1 second of silence
- Auto-scroll as new text appears
- Copy transcript to clipboard
- Clear transcript

### Display
- Large text by default (48px), adjustable with A- / A+ buttons
- Font size saved to localStorage and restored on next visit
- Dark/light mode toggle, preference saved to localStorage
- High contrast mode support via CSS media query

### Voice Commands
While holding the button to speak, you can say:

| Say | Effect |
|-----|--------|
| "clear text" | Clears all transcribed text |

When a command is recognized, a green confirmation overlay appears briefly. Command phrases are not added to the transcript.

## Project Structure

```
nanna/
├── index.html      # Entire application (HTML, CSS, and JS in one file)
├── manifest.json   # PWA manifest for home screen installation
├── icon.png        # App icon (512x512, used for PWA and iOS)
├── CLAUDE.md       # AI assistant context and project notes
└── README.md       # This file
```

## Contributing

### Architecture

The app is intentionally a **single HTML file** with no external dependencies. This is a core constraint — it makes the app trivially shareable (just send the file) and requires no setup to run or modify.

- All CSS is in a `<style>` block in `<head>`
- All JS is in a `<script>` block at the end of `<body>`
- CSS custom properties (`--bg-primary`, etc.) drive theming — dark mode is applied by toggling the `dark-mode` class on `<body>`

### Key State Variables

| Variable | Purpose |
|----------|---------|
| `isListening` | Whether speech recognition is active |
| `isHoldToSpeak` | Whether user is holding the button |
| `finalTranscript` | Accumulated HTML string of finalized speech |

### localStorage Keys

| Key | Values | Default |
|-----|--------|---------|
| `theme` | `"light"` / `"dark"` | `"light"` |
| `transcriptFontSize` | integer (px) | `48` |

### Design Principles

- **Accessibility first.** The primary user has difficulty reading — text must be large, clear, and high-contrast.
- **No dependencies.** Keep everything in `index.html`. Avoid adding build tools, package managers, or CDN links.
- **Simple over clever.** This is a single-purpose tool. Don't over-engineer.
- **Fail gracefully.** Show clear error messages for unsupported browsers or denied microphone permissions.

### Running Locally for Development

Since there's no build step, just open the file:

```bash
# Option 1: open directly
open index.html

# Option 2: serve over HTTP (useful for testing PWA features)
python3 -m http.server 8080
# then open http://localhost:8080
```

Some PWA features (like the manifest) only work when served over HTTP, not `file://`. Use option 2 if you're testing installation behavior.

### Testing Checklist

Before submitting changes, verify:

- [ ] Hold to speak works (touch and mouse)
- [ ] Text appears during speech (interim) and finalizes correctly
- [ ] Pause separators appear after silence
- [ ] Font size controls work and persist across page reload
- [ ] Clear button works in all states (listening, stopped)
- [ ] Copy button copies plain text (not HTML)
- [ ] Dark mode toggles and persists
- [ ] "Clear text" voice command works while holding
- [ ] Error message appears on unsupported browsers
- [ ] Responsive layout works on mobile (controls simplify correctly)
- [ ] Safe area padding works on iPhone with notch

## Potential Enhancements

See [CLAUDE.md](CLAUDE.md) for a full list. Top candidates:

- Language selection (currently hardcoded to `en-US`)
- Export transcript as TXT or PDF
- Keyboard shortcuts
- Auto-restart recognition after unexpected stops (Chrome kills it after ~60s of silence)
- Additional color themes
- Session history (save/load previous transcripts)
