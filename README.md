# Step-by-Step Composer

Standalone browser app for sketching melodies one note at a time. Pick a starting pitch, audition automatically suggested “next” notes, and tweak each note’s duration while hearing results immediately through the Web Audio API.

## Quick Start

1. Open `index.html` in a Chromium-based browser (Chrome 115+, Edge) or Firefox/Safari latest.
2. Select a starting note (C3–C6) and click **この音で始める**.  
   - The app seeds the sequence and unlocks the duration selector right below the button.
3. Use the **自動候補** buttons to listen/accept/skip suggested notes. Each accepted note becomes the new starting pitch and triggers another suggestion.
4. Adjust duration for the most recently added note via the dropdown (短め/標準/伸ばし/ホールド). The timeline displays both the source (user vs auto) and length label.
5. Use the timeline’s 🎧 button or **すべて再生** to audition the phrase. **最後の音を削除** backs up one step.

## Current Features

- **Guided Next-Note Suggestions**  
  Rule-based steps (±1, ±2, ±3, ±4, ±5) within C major, biasing singable leaps.
- **Immediate Audio Feedback**  
  Triangle-wave Web Audio playback with gentle ADSR tailoring for intelligible pitch.
- **Per-Note Duration Control**  
  Four presets per note, editable right after confirmation.
- **Responsive UI**  
  Pure HTML/CSS/JS, no build step or server required.

## Roadmap (See `plan.md`)

- Multi-scale/mode support and chord-aware heuristics.
- Modular candidate strategies (rule-based + ML).
- Rhythmic templates, multi-track layers, MIDI/MusicXML export.

## Development Notes

- Code lives entirely in `index.html`.
- Audio autoplays only after user interaction (browser policy).  
  First click primes `AudioContext`; without it no sound will emit.
- Tested on Chrome 143, Edge 121, Firefox 132, Safari 17.
