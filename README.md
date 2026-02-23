🧠 Decision Fatigue Guard

Decision Fatigue Guard is a privacy-first Chrome extension for Gmail that detects cognitive overload in real time and visually reduces decision stress while it’s happening.
The extension calculates a Decision Load Score (DLS) based on user interaction patterns and applies adaptive UI interventions — entirely on the user’s device, with no backend, no tracking, and no data scraping.

🚩 Problem Statement

While managing emails, users make dozens of micro-decisions such as opening, replying, deleting, undoing, and switching contexts. Over time, this leads to decision fatigue, resulting in slower responses, errors, and increased stress.

Most productivity tools react after overload occurs.
Decision Fatigue Guard identifies overload in real time — before productivity drops.

💡 Solution Overview

Decision Fatigue Guard:

Continuously tracks interaction metadata (never email content)

Computes a real-time Decision Load Score (DLS: 0–100)

Predicts overload risk using an on-device machine learning model

Dynamically modifies Gmail’s UI to reduce cognitive effort

✨ Key Features

✅ Real-time Decision Load Score (DLS)

🟢🟡🔴 Color-coded states: GREEN / AMBER / RED

🤖 On-device Machine Learning (TensorFlow.js)

🔒 Privacy-first (no network requests, no content access)

🎯 UI interventions (guarded actions, simplified UI)

📥 Decision Inbox (“Decide later” support)

🧪 Developer Mode for demos and testing

📊 Decision Load States
State	DLS Range	Meaning
🟢 GREEN	0–29	Normal workload
🟡 AMBER	30–60	Rising cognitive load
🔴 RED	61–100	High overload
⚠️ Early Warning Rule

The system promotes RED state when:

ML overload risk > 65%, and

DLS ≥ 45

🤖 Machine Learning (On-Device)

Framework: TensorFlow.js

Model: Logistic Regression

Training: Local only (no server)

Input Features

Events per minute

Undo rate

Indecision time

Context switching frequency

Output

Overload risk probability (%)

Users can also provide manual feedback using “I feel overloaded” to improve model accuracy over time.

🔐 Privacy by Design

This extension does NOT:

Read email subject or body

Store sender or recipient details

Send data to any server

Only anonymous interaction metadata is stored locally using chrome.storage.local.

🛠 Tech Stack

Chrome Extension (Manifest V3)

TypeScript

Vite (Build Tool)

TensorFlow.js (On-device ML)

MutationObserver (Gmail DOM detection)

CSS Interventions (UI adaptation)

Chrome Storage API (Local persistence)

📁 Project Structure
public/
  ├─ manifest.json
  ├─ icons/

src/
  ├─ content/
  │   ├─ gmailObserver.ts
  │   ├─ eventCapture.ts
  │   ├─ uiOverlay.ts
  │   ├─ interventions.ts
  │   └─ styles.css
  │
  ├─ background/
  │   ├─ service_worker.ts
  │   ├─ model.ts
  │   └─ storage.ts
  │
  ├─ shared/
  │   ├─ dls.ts
  │   ├─ featureEngineering.ts
  │   └─ types.ts
  │
  └─ index.ts

tests/

tests/
🚀 Installation & Setup
Prerequisites

Node.js 18+

Google Chrome

Steps
npm install
npm run build

Open chrome://extensions

Enable Developer Mode

Click Load unpacked

Select the dist/ folder

Open Gmail → Extension activates automatically

🧪 Demo Tips (Hackathons)

Enable Dev Mode in the extension panel

Use Simulate Overload to quickly trigger AMBER → RED

Demonstrate real-time Gmail UI changes

Highlight privacy-first + on-device ML clearly

⚠️ Limitations (MVP)

Gmail DOM may change occasionally

Model accuracy improves with continued usage

UI interventions are intentionally non-destructive

🔮 Future Enhancements

Personalized DLS baselines per user

Calendar and task integration

Long-term fatigue analytics

Cross-app support (Docs, Slack, Outlook)

⭐ Why This Project Stands Out

Real-time cognitive load detection

On-device ML with zero data leakage

Privacy-first by design

Practical UX interventions, not just analytics
