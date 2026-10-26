# 🌾 KrishiMitra – Digital Krishi Officer in Telugu

> **AI-Based Farmer Query Support and Advisory System**
> Smart India Hackathon 2025 · Problem Statement **SIH25076** · Team **CodeXplorers21** (Team ID 77763)

**🔗 Live prototype:** https://krishimitra-omega.vercel.app/

| | |
|---|---|
| **Theme** | Agriculture, FoodTech & Rural Development |
| **Category** | Software |
| **Prototype language** | Telugu (scalable to all Indian languages) |

---

## 📖 Overview

Many farmers in India prefer to communicate in their local language, but expert agricultural advice is mostly available in English or Hindi, or only during office hours. **KrishiMitra** bridges this gap by acting as a *Digital Krishi Officer* that farmers can talk to in their own language, using **voice, text, or images**.

The AI engine is designed to provide:

- 🐛 Organic pest-control suggestions
- 🌦️ Weather conditions and alerts
- 🏛️ Government subsidy information
- 📈 Market trends
- 🧑‍🌾 Escalation of complex queries to agriculture officers, plus a community of enthusiastic farmers

> *"KrishiMitra supports farmers throughout the crop cycle – from sowing to harvesting – by providing continuous monitoring and advisory."*

---

## ✨ Features

### Available in the current prototype
- 🔐 Simple login screen, or continue as guest
- 👋 Time-aware Telugu greeting (morning / afternoon / evening / night), spoken aloud
- 🎙️ **Voice input**: Telugu speech-to-text using the browser's Web Speech API (`te-IN`)
- ⌨️ **Text input**: type a question in Telugu
- 🖼️ **Image input**: upload a crop photo along with a question
- 🔊 **Voice output**: answers and prompts read aloud using browser text-to-speech
- 🌱 **Crop registration**: save crop name, growth stage, tasks and a photo
- 📋 **Crop dashboard**: view and delete registered crops (stored locally in the browser)
- 📱 Mobile-first responsive UI built with Tailwind CSS

### Planned (see architecture below)
- Real LLM-powered Q&A fine-tuned on agricultural data
- Crop-disease detection from images
- Context-aware advice (location, crop, season, farmer history)
- Expert escalation and validation loop
- Extension to other Indian languages

> ⚠️ **Note:** In the current prototype the answers to queries are **simulated** (a random Telugu sample response is returned after a short delay). The AI backend is part of the planned architecture.

---

## 🏗️ Technical Approach

### Frontend (App)
| Area | Technology |
|---|---|
| Framework | Next.js (React + TypeScript) |
| Styling | Tailwind CSS + Google Fonts (Inter) |
| State management | React Query (server state) |
| Speech (browser) | Web Speech API (TTS/STT fallback) |
| Hosting | Vercel (static + SSR) |

### Backend (Server)
| Area | Technology |
|---|---|
| Runtime | Node.js + TypeScript |
| Framework | Express / Next.js API routes |
| Auth | Firebase Auth |
| File uploads | Pre-signed URLs to AWS S3 |
| Hosting | Vercel |

### AI / LLM / NLP
| Area | Technology |
|---|---|
| Q&A (NLP) | LLM fine-tuned on agricultural datasets |
| Speech-to-Text | Whisper API |
| Text-to-Speech | ElevenLabs |
| Crop-disease image analysis | PyTorch model served via FastAPI |

### System flow

```
 Voice / Text / Image  ──►  Data ingestion & pre-processing
                                       │
                                       ▼
        ┌──────────────── AI-Powered Knowledge Engine ────────────────┐
        │  Speech-to-Text   │  LLM + fine-tuned Agri dataset  │  Computer Vision  │
        │   (Telugu)        │                                  │  (pest / disease) │
        └───────────────────────────┬──────────────────────────────────┘
                                    │        ▲
              Context awareness     │        │  Learning loop
       (location · crop/season ·    │        │  (real queries → feedback →
              farmer history)       ▼        │   expert validation)
                          Instant advice generation ──► Escalation to Agri officer
```

---

## 📁 Project Structure (prototype)

```
.
├── prototype.html     # Single-file Telugu demo UI (Tailwind via CDN, vanilla JS)
├── README.md
└── docs/
    └── CODEXPLORERS_PPT.pdf   # SIH 2025 idea submission deck
```

---

## 🚀 Getting Started

### Run the prototype locally

No build step is needed, as the prototype is a single HTML file.

```bash
# Clone the repository
git clone <your-repo-url>
cd krishimitra

# Option 1: open directly
open prototype.html            # macOS  (use `start` on Windows, `xdg-open` on Linux)

# Option 2: serve it locally (recommended for speech APIs)
python -m http.server 8000
# then visit http://localhost:8000/prototype.html
```

### Browser requirements
- **Chrome / Edge (desktop or Android)** is recommended. Voice input uses `webkitSpeechRecognition`, which is not supported in every browser.
- Telugu (`te-IN`) text-to-speech depends on the voices installed on your device.
- Internet access is needed to load Tailwind CSS and Google Fonts from their CDNs.

### Usage
1. Log in with any username and password, or tap **ప్రారంభించు** to continue as guest.
2. Choose **Voice**, **Text** or **Image** input and ask your question in Telugu.
3. Use **క్రాప్ రిజిస్ట్రేషన్** to add a crop, and see it on your dashboard.

> The login is a UI demo only and does not authenticate against a server. Crops are stored in `localStorage`.

---

## ✅ Feasibility & Viability

**Feasibility**
- *Technical:* uses AI/NLP, image recognition and open datasets; fast, low-cost, works on standard Android/iOS devices.
- *Operational:* farmers ask via voice, text or images; the system gives instant advisory and escalates complex queries.
- *Resource:* datasets, APIs and AI tools are available, and the team's skills match the requirements.

**Viability**
- 150M+ farmers prefer local languages, so adoption potential is high.
- Aligns with the Digital Agriculture Mission 2021–25.
- Scalable to multiple states and Indian languages.
- AI reports can be shared with agriculture officers for approval in critical cases.

---

## 🌍 Impact & Benefits

**Impact**
- 24×7 expert advice in the local language
- Bridges the gap between farmers and agriculture departments
- Supports farmers across the entire crop cycle (sowing → harvest)
- Encourages digital adoption in rural areas

**Benefits**
- Better crop management → higher yield and income
- Saves time and enables timely decisions
- Cost-effective
- Expandable as needs grow

---

## 🗺️ Roadmap

- [x] Telugu UI prototype with voice, text and image inputs
- [x] Crop registration and dashboard
- [ ] Connect real LLM for Telugu agricultural Q&A
- [ ] Whisper (STT) and ElevenLabs (TTS) integration
- [ ] PyTorch crop-disease model served via FastAPI
- [ ] Firebase Auth and S3 image uploads
- [ ] Live weather, subsidy and market-price data
- [ ] Expert escalation and feedback/learning loop
- [ ] Support for more Indian languages

---

## 📚 References & Resources

- [Plantix](https://plantix.net/en/)
- [mKisan Portal](https://mkisan.gov.in)
- [Google Translate Developer Docs](https://developers.google.com/translate)
- [Kaggle – All Agriculture-Related Datasets for India](https://www.kaggle.com/datasets/thammuio/all-agriculture-related-datasets-for-india)

---

## 👥 Team CodeXplorers21

| Name | Role |
|---|---|
|Nelakuditi Varshini | Team Leader |
| Parakala Lakshmi Hariti | Frontend Developer |

---

## 📄 License

Add a license of your choice (e.g. MIT) before publishing.
