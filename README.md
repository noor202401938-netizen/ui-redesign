# TutorMate Debate UI/UX Redesign

An interactive, responsive screen-by-screen prototype redesign for the **TutorMate AI Student Debate Arena** (formerly CleverBuddy in TutorMigo).

## 🚀 Live Prototype & Deliverables

- **Main Interactive Prototype:** Open [`index.html`](./index.html) in any browser (no installation or dependencies needed).
- **Standalone Individual Screens:** Explore [`screens/`](./screens/) for isolated views of all 13 screens.
- **Design Specification & Evaluation Report:** See [`DESIGN_ASSIGNMENT_REPORT.md`](./DESIGN_ASSIGNMENT_REPORT.md).

---

## 📱 Features & Highlights

1. **5-Step Setup Sequence:**
   - **Step 1:** Select Grade Band (`K–5`, `6–8`, `9–12`)
   - **Step 2:** Choose or Enter Topic (Curated questions + Custom topic live validator + Surprise Me)
   - **Step 3:** Pick Your Side (For vs. Against with explicit opposition disclaimer)
   - **Step 4:** Set Debate Length (Quick 2 rounds vs. Full 3 rounds)
   - **Step 5:** Communication Mode (Type for free vs. Voice match credit calculator)
   - **Review & Launch:** Confirmation summary card with inline edit links

2. **Dedicated Round 1 Debate Screens:**
   - **Text Debate Mode:** Argument composer, starter sentence chips, and live word counter (40–120 words target).
   - **Voice Debate Mode:** Live mic stage, sound waveform animation, and real-time speech-to-text transcript.

3. **Left-Side Dotted Menu (`⋮`):**
   - Seamlessly toggle between Text and Voice debate on the fly inside the debate arena without losing match progress.

4. **Complete Arena Lifecycle:**
   - Round 1 (Opening Stance) → Round 2 (Closing Rebuttal with audio speech playback) → AI Judge Verdict (Trophy, 3 scoring criteria, written commentary, and XP/coin rewards).

5. **Responsive Supervisor HUD:**
   - Switch between **Desktop (Fit Screen)**, **Tablet (820px)**, **Mobile (410px)**, and **1280px Frame**.
   - Jump to any screen via dropdown or navigate with keyboard left/right arrow keys (`←` / `→`).

---

## 🛠️ Tech Stack

- **HTML5 & Vanilla CSS/JavaScript** (Zero build dependencies, portable across any browser)
- **Typography:** Atkinson Hyperlegible & Fredoka (via Google Fonts)
- **Speech API:** Web Speech API (SpeechSynthesis) for interactive AI voice playback

