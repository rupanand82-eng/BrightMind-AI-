# EduSphere AI — Learn in 3D

EduSphere AI is a vibrant, interactive, AI-powered learning application designed to make complex science and logic concepts intuitive. It features high-fidelity 3D simulations, science models, logic animations, gamified achievements (streaks & energy points), and custom AI tutor explanations driven by Google's Gemini API.

## Features

- **3D Simulations & Interactivity**: Explore complex concepts (Biology, Physics, and Computer Science) in full-scale interactive 3D simulations using Three.js.
- **AI Tutor Explanation Box**: Get rich, context-aware answers to high-level questions from an embedded AI Tutor powered by standard server-side Gemini AI API integration.
- **Gamified Progress Tracking**: Earn energy points and track learning streaks synced to a secure backend.
- **Unified Authentication**: Sign in as a Guest or link your Google Account via Firebase Auth.
- **Digital Notepad & Study Utilities**: Write notes, save checklists, and run quick self-assessment queries.

---

## Tech Stack

- **Frontend**: React (v19), Vite, Tailwind CSS (v4), Motion (Framer Motion), Lucide Icons, Three.js
- **Backend/API Router**: Express.js
- **AI Engine**: `@google/genai` TypeScript SDK (Gemini)
- **Database & Auth**: Cloud Firestore, Firebase Authentication, and LocalStorage hybrid persistence
- **Serverless API Bridge**: Fully verified API routing wrapper optimized for Serverless cloud environments

---

## Local Development Setup

To run the application locally, follow these steps:

### 1. Prerequisites

Ensure you have **Node.js** (v18+) and **npm** installed on your local machine.

### 2. Install Dependencies

In the project root directory, run:
```bash
npm install
```

### 3. Environment Variables Configuration

Create a `.env` file in the root directory (based on `.env.example`) and fill in your details:
```env
# GEMINI_API_KEY: Required for Gemini AI API calls.
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"

# APP_URL: Optional for local server references, defaults to http://localhost:3000
APP_URL="http://localhost:3000"
```

### 4. Running the Development Server

Execute the development command to boot both Vite's asset compiler and the Express server:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your web browser.

---

## Vercel Serverless Deployment

This project is fully designed and optimized to be deployed seamlessly on **Vercel** with zero extra orchestration.

### How it works on Vercel:
- **Serverless API Layer**: The Express router lives in `/server.ts` and is exported as a handler via `/api/index.ts`. Vercel automatically maps requests prefixed with `/api` to compile and run this Express server as a **Serverless Function**.
- **Static Assets Routing**: The React/Vite bundle is compiled to a static `dist` folder. All non-API routes are automatically rewritten to serve `index.html`, delivering a flawless Single Page Application (SPA) experience.

### Deployment Guide:

1. **Connect to Vercel**: Import this codebase into your Vercel Dashboard from your GitHub/GitLab registry.
2. **Configure Environment Variables**:
   Add your environment secrets under Vercel Project Settings > **Environment Variables**:
   - `GEMINI_API_KEY`: Your official Google AI Studio / Google Cloud API key.
3. **Deploy**: Click the **Deploy** button. Vercel will auto-detect the configuration using our specified `vercel.json` routing configuration and build your fully functional full-stack applet.

---

## Project Structure

```text
├── .env.example            # Sample configuration file for secrets
├── vercel.json             # Vercel serverless routing rewrite rules
├── package.json            # Scripts and dependencies setup
├── server.ts               # Custom full-stack Express API router & local server
├── api/
│   └── index.ts            # Serverless API function entry-point for Vercel
├── src/
│   ├── App.tsx             # Parent hub component
│   ├── main.tsx            # App bootstrap mount point
│   ├── index.css           # Global stylesheet with Tailwind Custom Theme variables
│   ├── data.ts             # Study disciplines, scientific subjects, and lessons metadata
│   ├── components/         # Modular reusable learning widgets
│   │   ├── ThreeCanvas.tsx       # 3D interactive model stage (ThreeJS)
│   │   ├── AITutorBox.tsx        # Gemini AI prompt interaction box
│   │   ├── SimulationBox.tsx     # Active interactive subject controls
│   │   ├── DigitalNotepad.tsx    # Study notes, templates & checklists
│   │   ├── StreakCounter.tsx     # XP and daily energy booster trackers
│   │   └── ...                   # Additional interactive card widgets
│   └── utils/
│       ├── firebase.ts           # Firebase client setup
│       └── soundEngine.ts        # Custom synthesizer audio nodes
└── ...
```

Developed with 🪄 of high-fidelity interactive learning. Enjoy exploring EduSphere AI!
