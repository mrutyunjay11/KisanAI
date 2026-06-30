# 🌾 KisanAI — Smart Farming Assistant for Indian Farmers

KisanAI is a production-grade, crop-agnostic AI agent built for the **Google × Kaggle 5-Day AI Agents Intensive** Capstone Project. It combines real-time weather data, live mandi prices via Gemini Search Grounding, and safety-guided pest advice in a lightweight, pure client-side web application.

## 🚀 Key Features

- **Live Mandi Prices** — Uses Gemini 2.5 Flash with Google Search Grounding to fetch current APMC rates in Gujarat in real-time
- **Local Weather Tools** — Integrates Open-Meteo API for real-time weather forecasts based on the user's profile location
- **Farmer Memory** — Persists the farmer's name, crop type, location, and conversation history using browser localStorage
- **Pest & Disease Advisor** — Guided diagnostic steps tailored to the active crop (Yellow Rust on Wheat, Whiteflies on Cotton, etc.)
- **Safety Guardrails** — Prevents unsafe pesticide recommendations and redirects health-related queries to doctors
- **Analytics Panel** — Tracks real-time tool usage, API status, and agent telemetry

## 📂 Project Structure
├── index.html               # Main KisanAI web app (HTML5, Vanilla CSS, JS)
├── KisanAI_Notebook.ipynb   # Jupyter Notebook to run inside Kaggle
└── README.md                # Project documentation

## 🛠️ Setup & Local Execution

No complex installation or package builders required.

**1. Clone the repository:**
```bash
git clone https://github.com/mrutyunjay11/KisanAI.git
cd KisanAI
```

**2. Add your Gemini API Key:**
- Open `index.html` in your browser (double-click it)
- Click the Settings gear icon (⚙️) in the top-right corner
- Enter your free Gemini API key from [Google AI Studio](https://aistudio.google.com)

**Or run a local HTTP server:**
```bash
python3 -m http.server 8080
```
Then open `http://localhost:8080` in your browser.

**3. Run on Kaggle:**
- Open `KisanAI_Notebook.ipynb` in a Kaggle Notebook
- Attach the `kisanai` dataset (contains `index.html`)
- Add your Gemini API key as a Kaggle Secret named `GEMINI_API_KEY`
- Click "Run All"

## 🤖 Model Fallback System

To survive API quota exhaustion or server spikes, KisanAI employs an automated fallback pipeline across multiple Gemini models, switching automatically if one hits rate limits.

## 🏗️ Architecture
Farmer Types Query (English / Hindi / Gujarati)
│
Agent Core — Intent Detection
│
Live Tool Calls
┌────────────────┬────────────────┐
▼                ▼                ▼
[Weather API]  [Gemini Grounding]  [Pest/Schemes]
(Open-Meteo)     (Google Search)    (Structured AI)
└────────────────┼────────────────┘
▼
Farmer Memory ➔ Safety Guardrails
│
Multi-Model Fallback Chain
│
Personalized Output

## 🛡️ Built For

This project was built for India's 140M+ farmers, designed to be lightweight enough to run on any basic mobile browser with zero installation required.

## 📜 License

CC BY-SA 4.0
