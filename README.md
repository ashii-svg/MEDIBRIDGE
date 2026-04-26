# MEDIBRIDGE
# MediBridge 2026

> **AI-powered healthcare communication platform for patients with speech and hearing disabilities.**

MediBridge uses real-time American Sign Language (ASL) recognition, speech-to-text, and an AI doctor chat room to bridge the communication gap between differently-abled patients and medical professionals.

---

##  Features

### Live ASL Recognition
- Real-time 21-point hand skeleton tracking using **MediaPipe Hands**
- Precision geometric classifier for the full **A–Z ASL alphabet**
- Color-coded skeleton overlay (red wrist · blue fingertips · green knuckles)
- Stability buffer — requires consistent gesture across multiple frames before committing
- AI-enhanced second-opinion analysis for ambiguous gestures
- ASL alphabet tracker that lights up each detected letter

###  Speech to Text (STT)
- Patient voice captured via browser **Web Speech API**
- Transcribed text sent directly to the doctor's chat room
- Works entirely in the browser — no external service needed

###  Doctor Chat Room
- Live two-way text chat with **Dr. Anonymous**
- AI-generated clinically appropriate responses
- Quick symptom shortcuts (pain, dizzy, emergency, breathing issue, etc.)
- ASL transcription can be forwarded to the doctor in one tap

###  Text to Speech (TTS)
- Doctor's reply is automatically **spoken aloud** in a natural voice
- Replay button to hear the last reply again
- Uses browser Web Speech API with smart voice selection

### ASL Translation History
- Full log of every detected gesture
- Confidence scores and timestamps
- Audio playback for each logged letter
- Clearable history table

---

## Live Demo

> **[medibridge.github.io/medibridge](https://ashii-svg.github.io/MEDIBRIDGE)**


---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Hand Tracking | MediaPipe Hands (Google) |
| ASL Classifier | Custom geometric landmark classifier |
| AI Doctor Replies | Anthropic API (claude-sonnet) |
| Speech to Text | Web Speech API |
| Text to Speech | Web Speech Synthesis API |
| Frontend | Vanilla HTML, CSS, JavaScript |
| Fonts | DM Sans + DM Serif Display (Google Fonts) |
| Hosting | GitHub Pages |

---

## 📖 How to Use

### ASL Live Tracking
1. Click **Live Tracking** in the nav bar
2. Allow camera access when prompted
3. Click **Start Detection**
4. Hold your hand up to the camera and form ASL letters
5. The skeleton overlay appears in real time
6. Detected letters build up in the transcription box
7. Click **Send to Doctor ↗** to forward to the chat room

### Voice Input
1. Go to **Doctor Chat**
2. Tap **Tap to Speak** and speak your message
3. Click **Send Voice ↗** to send to the doctor

### Doctor Chat
1. Go to **Doctor Chat** tab
2. Type directly, use voice input, or send your ASL transcription
3. The doctor's AI reply appears and is spoken aloud automatically
4. Use quick symptom buttons for fast communication

---

##  ASL Classifier — How It Works

The classifier uses **21 MediaPipe hand landmarks** and measures:
- **Finger extension** — whether each fingertip is above its MCP knuckle
- **Normalized distances** — thumb-to-fingertip distances relative to palm size
- **Lateral spread** — how far apart fingertips are from each other
- **Curl depth** — how tightly fingers are folded into the palm

Each ASL letter has a unique geometric signature. For example:

| Letter | Key Rule |
| C | All fingers bent ~45°, moderate thumb-index gap (0.28–0.78 norm) |
| O | All tips pinching to thumb tip, TI distance < 0.25 |
| L| Index up + thumb horizontal — checks both extension AND direction |
| D | Index up + thumb-middle circle (TM < 0.28) |
| F | Index-thumb pinch tight + middle/ring/pinky erect |
| E | All 4 fingers curled, tips at MCP level, thumb tucked |
| V | Index+middle up, spread wide (IM > 0.18) |
| R | Index+middle up but crossed (IM < 0.13) |

A 12-frame stability buffer prevents false positives — the same letter must be detected consistently before it's committed.

---

##  Setup & Installation

MediBridge is a **single HTML file** — no build tools, no npm, no server required.

### Run Locally
```bash
git clone https://github.com/your-username/medibridge.git
cd medibridge
# Open index.html in Chrome
open index.html
```

### Deploy to GitHub Pages
1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Source: **Deploy from branch → main → / (root)**
4. Your site is live at `https://your-username.github.io/medibridge`

>  **Camera & microphone** access requires either `localhost` or `https://`. GitHub Pages provides HTTPS automatically.

---

##  Use Case

MediBridge was designed for **differently-abled patients** in healthcare settings who:
- Are deaf or hard of hearing
- Have speech impairments
- Cannot communicate verbally with medical staff

The platform allows them to sign in ASL or speak, and have their message delivered clearly to a doctor — with the doctor's reply spoken back to them.

---

##  Privacy

- **No video is stored or transmitted** — only hand landmark coordinates are processed
- Camera feed stays local in your browser
- Voice recognition runs on-device via the browser API
- No user data is logged or saved between sessions

---

##  Project Structure

```
medibridge/
├── index.html        # Entire application (self-contained)
└── README.md         # This file
```

---

## Acknowledgements

- [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) — Google's hand tracking model
- [DM Sans & DM Serif Display](https://fonts.google.com) — Google Fonts
- ASL alphabet reference — standard American Sign Language fingerspelling

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

<p align="center">Built for the differently-abled. © 2026 MediBridge.</p>
