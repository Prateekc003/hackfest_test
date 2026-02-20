TO RUN---- npx serve .








# 🧠 NeuroLearn — Adaptive Learning for Neurodivergence

A hackathon-ready adaptive learning dashboard for neurodivergent learners (ADHD, Dyslexia, Autism, Dyscalculia).

---

## 🚀 Quick Setup (5 minutes)

### 1. Create a Firebase Project
1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"** → name it `neurolearn`
3. Disable Google Analytics (optional for hackathon)

### 2. Enable Authentication
1. In Firebase Console → **Authentication** → **Get started**
2. Enable **Email/Password** provider
3. Enable **Google** provider (add your support email)

### 3. Enable Firestore
1. **Firestore Database** → **Create database**
2. Start in **test mode** (for hackathon speed)
3. Choose any region

### 4. Paste your Firebase config
1. **Project Settings** (gear icon) → **Your apps** → **Add app** → Web (</>)
2. Register app, copy the `firebaseConfig` object
3. **Paste it** in BOTH files, replacing the placeholder:
   - `index.html` (around line 190)
   - `dashboard.html` (around line 360)

### 5. Deploy Firestore Rules (Optional but recommended)
```bash
npm install -g firebase-tools
firebase login
firebase init firestore
# paste content of firestore.rules when prompted
firebase deploy --only firestore:rules
```

### 6. Run Locally
```bash
# Option A: VS Code Live Server extension (easiest)
# Option B:
npx serve .
# Option C:
python3 -m http.server 8000
```

Open `http://localhost:8000` → you'll see the login page!

---

## 📁 File Structure

```
neurolearn/
├── index.html          # Login / Signup page
├── dashboard.html      # Main dashboard (Firebase connected)
├── firestore.rules     # Security rules
└── README.md
```

---

## ✨ Features

### Authentication
- ✅ Email + Password signup/login
- ✅ Google OAuth (one-click)
- ✅ Auto-redirect if already logged in
- ✅ Friendly error messages
- ✅ Neurodivergent profile selection on signup

### Dashboard — All Firebase Connected
- ✅ **Real-time streak tracking** — persists across sessions
- ✅ **Mood check-in** — saved to Firestore, adapts UI
- ✅ **Course progress** — tracked per user in Firestore
- ✅ **Focus timer** — completed sessions logged to Firestore
- ✅ **Accessibility settings** — saved per user, auto-applied on load
- ✅ **Calm Mode** toggle
- ✅ **Colour overlay** picker (5 options)
- ✅ **Dyslexia font** mode
- ✅ **Text-to-speech** integration (Web Speech API)
- ✅ **Reduce motion** mode
- ✅ **Course filtering** by profile (ADHD / Dyslexia / Autism)
- ✅ **Real-time Firestore listener** for live updates

### Firestore Data Model
```
users/{uid}
  ├── name, email, profiles[]
  ├── streak, bestStreak, lastActive
  ├── mood, focusMode, totalFocusMinutes
  ├── settings { dyslexiaFont, colorOverlay, reduceMotion, textToSpeech, lowContrast, calmMode }
  ├── progress { courseId: percentageInt }
  ├── moodLog/ (subcollection)
  │     └── { mood, timestamp }
  └── focusSessions/ (subcollection)
        └── { minutes, completedAt, mood }
```

---

## 🏆 Hackathon Pitch Points
- Neurodivergent learners make up ~15-20% of the population and are massively underserved by standard EdTech
- Fully personalised per-user — not one-size-fits-all
- Real-time data enables future ML-based adaptivity
- Accessibility-first design: dyslexia font, overlays, motion, TTS, contrast
- Mood-responsive lesson delivery
- Streak system builds positive reinforcement without shame

---

## 🔮 Extend It
- Add AI-powered content summarisation (Claude API)
- Add more courses as Firestore documents
- Build a parent/teacher analytics dashboard
- Add push notifications for streaks
- Add gamification badges
