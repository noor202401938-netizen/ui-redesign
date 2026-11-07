# TutorMate Debate UI/UX Redesign — Complete Screen-by-Screen Flow & Debate Arena Specification

> **Course / Supervisor Assignment Deliverable**  
> **Product:** TutorMate AI (Debate Experience)  
> **Interactive Prototype:** Open [`index.html`](file:///d:/tutormate-ui-redesign/index.html) directly in any web browser.  
> **Standalone Individual Screens:** Explore [`screens/`](file:///d:/tutormate-ui-redesign/screens/) for isolated screen-by-screen views.

---

## 1. Executive Summary & Design Challenge

### Core Objective
Transform the Debate UI experience so students can quickly understand how to start a debate, choose their grade band (**K–5, 6–8, 9–12**), select or enter their topic and side, set the debate length, decide whether to use voice, and engage in a structured debate match through **Opening**, **Closing**, and **AI Judge Verdict** rounds with dedicated **Text Mode** and **Voice Mode** screens, plus a **left-side dotted menu (`⋮`)** to switch modes anytime.

### The Problems With the Original Software (Identified from Screenshots)
From reviewing the live application ([Screenshot 1: `tutormigo.ai/debate`](file:///C:/Users/sm/.gemini/antigravity/brain/tempmediaStorage/media_1794059646941_e407eff5.png) and [Screenshot 2: `tutormigo.ai/debate/1495`](file:///C:/Users/sm/.gemini/antigravity/brain/tempmediaStorage/media_1794059646972_592a857c.png)):
1. **Cluttered Setup:** All configuration options (grade bands, topic list, sides, rounds, voice toggle) were presented simultaneously on a single crowded 2-column page.
2. **Hidden Next Step:** The "Your match" box looked like a disabled input field, and the Start button sat below the fold with no clear guidance on missing criteria.
3. **Muddled Modality in the Arena:** Text and voice debate were not cleanly separated into tailored experiences, leaving students unsure whether they should speak or type.
4. **No On-the-Fly Mode Switching:** If a student was in a noisy classroom or had microphone trouble, there was no quick way to toggle between speaking and typing inside the round.
5. **Disconnected Arena:** Students jumped into a debate without a clear sense of the three-phase progression (**Opening → Closing → Verdict**).

---

## 2. Complete 13-Screen Guided Flow Architecture

The redesign implements a **5-step guided setup journey** followed by mode-aware debate screens:

```
[1. Welcome & Splash]
       ↓  (Start a debate)
[2. Step 1 of 5 · Grade Band] (K–5 Elementary | 6–8 Middle School | 9–12 High School)
       ↓  (Next)
[3. Step 2 of 5 · Pick Topic] (Grade-tailored topics + Custom Topic input + Surprise Me)
       ↓  (Next)
[4. Step 3 of 5 · Pick Side] (For vs Against + TutorMate opposing side notice)
       ↓  (Next)
[5. Step 4 of 5 · Debate Length] (Quick 2 rounds vs Full 3 rounds)
       ↓  (Next)
[6. Step 5 of 5 · Type or Speak] (Typing: Free vs Voice: +2 credits/round with live balance)
       ↓  (Next)
[7. Ready to Start · Review] (Confirmation card with inline "Change" links for all settings)
       ↓  (Enter Debate Arena)
       ├─────────────────────────────────┬─────────────────────────────────┐
       ▼ (if Type chosen)                 ▼ (if Voice chosen)               │
[8. Round 1: Opening (Text Mode)]   [9. Round 1: Opening (Voice Mode)]      │
 (Composer + Starter chips + Word     (Live Mic stage + Sound waveform +    │ (Dotted '⋮' Menu
  counter: 40–120 words target)        Speech-to-text transcript buffer)    │  on left switches
       └─────────────────────────────────┬─────────────────────────────────┘   between modes)
                                         ↓  (Argue / Release Mic)
[10. Debate · Round 2 (Closing)] (Opening Transcript + TutorMate Audio Rebuttal + Closing Composer)
                                         ↓  (Argue / Release Mic)
[11. AI Judge Verdict] (Winner Trophy, 3 Evaluative Scorecards, Judge Commentary, XP/Coin Rewards)
                                         ↓  (View Dashboard)
[12. Voice Focus · Live Mic Stage] (Detailed live recording waveform, speech-to-text preview)
                                         ↓  (Done Speaking)
[13. Home · Debates Dashboard] (Active match "Keep going" card + Past debate outcome badges)
```

---

## 3. Screen-by-Screen Breakdown & Key Features

### Screen 1 · Welcome Splash (`01-start.html`)
* **Hero Banner:** Welcoming illustration, headline *"Sharpen Your Critical Thinking with TutorMate"*, and clear summary of the learning benefits.
* **Call to Action:** Prominent 3D-styled **"Start a debate"** button that immediately launches the setup wizard.

### Screen 2 · Step 1 of 5: Select Your Grade Band (`02-grade-band.html`)
* **Single Unified Choice:** Three distinct interactive cards without duplicate controls:
  1. **K–5 · Elementary School:** Fun, creative questions (*"Kids should have classroom pets"*, *"Recess should be an hour long"*).
  2. **6–8 · Middle School (Default):** Critical thinking on school life & tech (*"Homework should be banned"*, *"School should start later in the morning"*).
  3. **9–12 · High School:** Advanced civic & policy questions (*"Standardized tests should be abolished"*, *"Social media harms teen mental health"*).
* **Next Action:** Carries the chosen grade band to Screen 3, automatically loading that grade's curated debate questions.

### Screen 3 · Step 2 of 5: Pick a Topic (`03-topic.html`)
* **Live Grade Filter:** Grade switcher pill at top allows browsing other grades on the fly.
* **Surprise Me Button:** Shuffles random curated debate questions for undecided students.
* **Custom Topic Input:** Immediate inline validation badge (*"✓ Ready to use"*) as soon as 8 characters are entered.

### Screen 4 · Step 3 of 5: Pick Your Side (`04-side.html`)
* **For vs. Against Cards:** Clear colored indicators for **For (In favor)** and **Against (Opposed)**.
* **Tutor Opposition Notice:** Clear, explicit disclaimer: *"TutorMate will argue the opposite side to give you a true debate challenge."*

### Screen 5 · Step 4 of 5: Set Debate Length (`05-length.html`)
* **Quick Debate (2 Rounds):** Opening Stance + Closing Rebuttal (Approx. 5–7 mins).
* **Full Debate (3 Rounds):** Opening Stance + Cross-Examination + Closing Rebuttal (Approx. 10–12 mins).

### Screen 6 · Step 5 of 5: Type or Speak (`06-modality.html`)
* **Clear Modality Choice:**
  * **Type Your Arguments (Free):** 0 credits consumed, ideal for quiet classrooms or library study.
  * **Speak with Voice (+2 credits/round):** Full speech recognition and spoken audio feedback with live credit calculation (`4 credits total` for 2 rounds) and visible student balance.

### Screen 7 · Ready to Start Review (`07-ready-review.html`)
* **Summary Confirmation Card:** Lists Grade Band, Topic, Side, Length, and Modality in one clean card.
* **Smart Routing:** Clicking **"Enter Debate Arena"** automatically routes the student to **Screen 8 (Text Mode)** if they chose typing, or **Screen 9 (Voice Mode)** if they chose voice!

### Screen 8 · Debate Round 1: Opening (Text Debate Mode) (`08-debate-round1-text.html`)
* **Left-Side Dotted Menu (`⋮`):** Allows instant switching to Voice Mode anytime.
* **3-Phase Stepper:** `● Opening (Active)` — `○ Closing (Pending)` — `○ Verdict (Pending)`.
* **Starter Sentence Prompt Chips:** *"I believe this because…"*, *"The strongest reason is…"*, *"From my own experience…"*.
* **Dedicated Text Composer:** Large multi-line argument box with auto-focus and live word count validator (`0 words · aim for 40–120 words`, turning green `#1B7340` when met).
* **Action:** **"Argue (Submit Stance) ›"** advances to Round 2 Closing.

### Screen 9 · Debate Round 1: Opening (Voice Debate Mode) (`09-debate-round1-voice.html`)
* **Left-Side Dotted Menu (`⋮`):** Allows instant switching to Text Mode anytime (ideal if in a noisy room).
* **3-Phase Stepper:** `● Opening (Active)` — `○ Closing (Pending)` — `○ Verdict (Pending)`.
* **Live Voice Stage:**
  - `⏱ 60s remaining` round countdown timer.
  - Animated sound waveform bars (`||||||||||||||||||`).
  - Circular **HOLD TO ARGUE** mic button with pulsing active state.
  - Real-time Speech-to-Text transcript display box with live spoken word count.
* **Action:** **"Submit Spoken Argument ›"** advances to Round 2 Closing.

### Screen 10 · Debate Round 2: Closing & Rebuttal (`10-debate-round2.html`)
* **Left-Side Dotted Menu (`⋮`):** Toggle between typing or speaking your closing rebuttal.
* **Full Transcript Context:** Displays the student's opening stance and TutorMate's AI counter-argument with a working **"🔊 Listen"** speech synthesis button.
* **Closing Rebuttal:** Hold-to-speak or type a closing rebuttal refuting the AI's points.

### Screen 11 · The AI Judge Verdict (`11-verdict.html`)
* **Winner Trophy Banner:** `🏆 You Won This Debate!` with animated reward pills (`⭐ +50 XP` and `🪙 +15 Coins`).
* **3-Dimension Evaluative Scorecard:**
  1. **Logic & Structure:** `9.0 / 10` with visual progress bar.
  2. **Evidence & Examples:** `8.5 / 10` with visual progress bar.
  3. **Rebuttal Strength:** `9.2 / 10` with visual progress bar.
* **Impartial Written Commentary:** Constructive feedback detailing what worked and tips for future rounds.
* **Collapsible Transcript Drawer:** Lets students and teachers review turn-by-turn debate records.

### Screen 12 · Voice Focus: Live Mic Stage (`12-voice-focus.html`)
* Dedicated voice experience showcasing sound wave animation, live audio visualizer, push-to-talk mic state, and live speech-to-text transcript buffer.

### Screen 13 · Home: Debates Dashboard (`13-debates-dashboard.html`)
* **Active Match Card:** *"Homework should be banned"* with quick **"Keep going ›"** resumption.
* **Past Debates Roster:** Historical debates with win/loss badges, scores, round duration, and grade band tags.

---

## 4. Left-Side Dotted Menu (`⋮`) Specification

The left side of the debate header features an accessible kebab menu (`⋮`):
* **Placement:** Located directly adjacent to the top-left Leave/Close button.
* **Flyout Options:**
  1. `✍️ Text Debate` — Switch to typing composer with starter sentence chips.
  2. `🎙️ Voice Debate` — Switch to live mic stage with sound waveform and speech recognition.
* **State Preservation:** Switches seamlessly between Screen 8 and Screen 9 without losing the student's selected topic, side, or active match progress.

---

## 5. Acceptance Criteria Compliance Checklist

| Assignment Requirement | Redesign Implementation | Status |
|---|---|:---:|
| **1. Obvious Step Progression** | 5 setup steps (`Grade Band → Topic → Side → Length → Modality`) + 3-state round stepper (`Opening → Closing → Verdict`). | **PASSED** ✅ |
| **2. Grade Band (K–5, 6–8, 9–12)** | Dedicated Step 1 with single unified card selection (`K–5`, `6–8`, `9–12`) and rich preview cards. | **PASSED** ✅ |
| **3. Separate Round 1 Screens** | Tailored **Screen 8 (Text Mode)** and **Screen 9 (Voice Mode)** automatically chosen based on user setup selection. | **PASSED** ✅ |
| **4. Left-Side Dotted Menu (`⋮`)** | Header kebab button opens flyout to toggle between Text and Voice debate on the fly. | **PASSED** ✅ |
| **5. Clear Selection Feedback** | High-contrast blue highlight (`#2457D6`) on chosen cards, plus explicit review summary before launch. | **PASSED** ✅ |
| **6. Tutor Argues Opposite Side** | Explicit callout on Screen 4: *"TutorMate will argue the opposite side to challenge you."* | **PASSED** ✅ |
| **7. Voice & Text Debate Actions** | Working push-to-talk mic button, starter sentence chips, live word counter (40–120 words), and TTS audio playback. | **PASSED** ✅ |
| **8. Visible Credit Math** | Screen 6 breaks down exact credit pricing: `Free (0 credits)` for Typing vs `+2 credits/round` for Voice with live balance check. | **PASSED** ✅ |
| **9. Custom Topic Usability** | Positioned directly under suggested topics with 8-character threshold and instant `✓ Ready to use` badge. | **PASSED** ✅ |
| **10. Complete Round Lifecycle** | Dedicated Opening, Closing, and AI Judge Verdict screens with scores, constructive feedback, and XP/coin rewards. | **PASSED** ✅ |
| **11. Responsive & Accessible** | Interactive device switcher for Desktop (Fit Screen), Tablet (820px), and Mobile (410px) with full keyboard arrow navigation. | **PASSED** ✅ |

---

## 6. Supervisor Testing Guide

1. Open [`index.html`](file:///d:/tutormate-ui-redesign/index.html) in Chrome, Edge, or Safari.
2. In Screen 6 (Type or Speak):
   - Choose **"Type Your Arguments"** → Notice Screen 7 routes directly into **Screen 8: Round 1 (Text Mode)** with the text composer and sentence chips.
   - Or choose **"Speak with Voice"** → Notice Screen 7 routes directly into **Screen 9: Round 1 (Voice Mode)** with the live mic stage, waveform, and speech recognition.
3. In Round 1 (either mode):
   - Click the **three-dotted menu (`⋮`)** on the top-left side next to the close button.
   - Select the other mode and watch it smoothly switch between Text Debate and Voice Debate on the fly!
4. Test live speech synthesis:
   - On Round 2, click **"🔊 Listen"** on TutorMate's counter-argument to test real browser speech audio.
