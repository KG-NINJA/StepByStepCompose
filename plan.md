# Melody Engine Enhancement Plan

## 1. Foundations (Current Quarter)
- **Scale/Mode Abstraction**
  - Extract scale definitions into `scales.ts`.
  - Support Ionian, Dorian, Mixolydian, Aeolian.
  - API: `getScaleNotes(key: string, mode: Mode): Note[]`.
- **Duration & Dynamics API**
  - Finalize per-note duration + articulation interface.
  - Add legato/staccato envelope presets.
- **Candidate Strategy Interface**
  - Define `NextNoteStrategy` with `score(currentState) -> Candidate[]`.
  - Keep current step-based strategy as default implementation.

## 2. Harmony Awareness (Next Quarter)
- **Chord Timeline**
  - UI for entering chord progression (grid or text “Cmaj7 | Fmaj7 | …”).
  - Data model: timeline slices with chord quality + inversion.
- **Voice-Leading Heuristics**
  - Strategy uses current chord tone vs tension resolution.
  - Rule set: prefer 3rd/7th resolution, avoid parallel fifths when possible.
- **Adaptive Context**
  - Track melodic contour (uphill/downhill) and penalize repeated leaps.
  - Weight outputs from scale, chord, contour rules.

## 3. Advanced Strategies (Future)
- **Pattern Learning**
  - Collect anonymized user sequences (opt-in).
  - Train Markov / Transformer model for stylistic suggestions.
- **Style Packs**
  - Parameter presets (Jazz II-V-I, Pop Hooks, Game Loops).
  - Ability to mix rule-based + ML weighted outputs.

## 4. Rhythm & Arrangement
- **Rhythmic Templates**
  - Grid editor (1/8, 1/16) with stress accents.
  - Sync note suggestions to beat positions.
- **Instrument Layers**
  - Multiple tracks (melody, bass, pads).
  - Each track can request its own next-note strategy.

## 5. Export & Collaboration
- **Persistence**
  - Save/load sessions (localStorage + JSON export).
  - Snapshots for version history.
- **MIDI/MusicXML Export**
  - Map durations to ticks; include tempo/key metadata.
  - Validate with DAWs (Ableton, Logic).
- **Realtime Collaboration (Stretch)**
  - WebRTC or shared backend for co-editing.

## 6. Testing & Validation
- **Unit Tests**
  - Scale/mode correctness, candidate ordering, duration conversion.
- **Integration Tests**
  - Playwright suite for UI flows (select note → hear audio → adjust duration).
- **Musical QA**
  - Reference melodies to ensure strategies keep tonal center.
  - Solicit feedback from musicians each milestone.
