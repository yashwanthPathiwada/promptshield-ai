# 🛠️ PromptShield — Complete Installation & Setup Guide
**Project by:** Team ByteBusters (Lead Developer: Yashwanth Pathiwada)  
**Hackathon Deliverable:** Item 5 — Installation Guide

---

## 📌 Overview
PromptShield is a production-ready, full-stack application comprising:
1. **Frontend:** React 18, Tailwind CSS, Vite Single Page Application (SPA).
2. **Backend:** FastAPI (Python 3.11+), Pydantic v2 schemas, Uvicorn ASGI server.
3. **Deployment Options:** Docker Multi-Stage Container (Recommended) OR Manual Local Development.

---

## 💻 System Prerequisites

| Dependency | Minimum Version | Recommended | Notes |
| :--- | :--- | :--- | :--- |
| **Python** | 3.10+ | 3.11 or 3.12 | Required for FastAPI backend |
| **Node.js** | 18.x+ | 20.x LTS | Required for React frontend build |
| **npm** | 9.x+ | 10.x+ | Included with Node.js |
| **Git** | 2.x+ | Latest | Version control |
| **Docker** | 20.x+ *(Optional)* | Latest Desktop | For single-command containerized run |

---

## 🚀 Option 1: Quick-Start with Docker (Recommended)

The project includes a multi-stage `Dockerfile` that packages both the frontend and backend into an optimized single container.

### Step 1: Clone the Repository
```bash
git clone https://github.com/yashwanthPathiwada/promptshield-ai.git
cd promptshield-ai
```

### Step 2: Build the Docker Image
```bash
docker build -t promptshield:latest .
```

### Step 3: Run the Container
```bash
docker run -p 8000:8000 --env-file backend/.env promptshield:latest
```

Open your browser and navigate to:
```
http://localhost:8000
```
*(The entire application, including UI and API endpoints, is live!)*

---

## ⚙️ Option 2: Manual Local Development Setup

If you wish to develop or modify the code locally, run the backend and frontend in separate terminals.

### Step 1: Clone the Repository
```bash
git clone https://github.com/yashwanthPathiwada/promptshield-ai.git
cd promptshield-ai
```

---

### Step 2: Backend Setup (FastAPI)

1. Open a terminal in the project root:
   ```bash
   cd backend
   ```

2. Create and activate a Python virtual environment:
   - **Windows (PowerShell):**
     ```powershell
     python -m venv venv
     .\venv\Scripts\Activate.ps1
     ```
   - **macOS / Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure Environment Variables:
   Copy the example environment file:
   ```bash
   cp .env.example .env
   ```
   Edit `.env` (optional AI keys):
   ```env
   # PromptShield Environment Configuration
   GEMINI_API_KEY=your_gemini_api_key_here
   OPENAI_API_KEY=your_openai_api_key_here
   ANTHROPIC_API_KEY=your_anthropic_api_key_here
   PORT=8000
   HOST=0.0.0.0
   ```
   > **Note:** If no AI keys are provided, PromptShield automatically runs in **Autonomous Deterministic Heuristic Mode** with zero crashes.

5. Start the FastAPI ASGI server:
   ```bash
   uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
   ```
   - API Docs will be available at: `http://localhost:8000/docs`
   - Health check: `http://localhost:8000/health`

---

### Step 3: Frontend Setup (React + Vite)

1. Open a **second terminal** and navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install Node dependencies:
   ```bash
   npm install
   ```

3. Launch the Vite development server:
   ```bash
   npm run dev
   ```

4. Open your browser at the Vite URL displayed (typically `http://localhost:5173`).

---

## 🧪 Option 3: Automated Script Execution (One-Click)

The repository provides shell scripts for automated startup:

- **Start Local Dev Server (Linux/macOS):**
  ```bash
  chmod +x dev.sh run.sh
  ./dev.sh
  ```
- **Windows PowerShell One-Liner (Build & Run Backend):**
  ```powershell
  cd frontend; npm run build; cd ..; uvicorn backend.main:app --reload --port 8000
  ```

---

## 🔍 Verifying the Installation

To verify that your installation is fully functional, run the automated test suite:

```bash
pytest tests/
```
Expected output:
```
tests/test_promptshield.py .... [100%]
===================== 4 passed in 0.42s =====================
```

---

## ❓ Troubleshooting & FAQs

### Q1: `uvicorn` is not recognized
- **Fix:** Ensure your virtual environment is activated (`.\venv\Scripts\Activate.ps1` on Windows) and `pip install -r backend/requirements.txt` was completed.

### Q2: Port 8000 is already in use
- **Fix:** Run on a different port:
  ```bash
  uvicorn backend.main:app --reload --port 8080
  ```

### Q3: Do I need an OpenAI or Gemini API key to run?
- **Answer:** **No.** PromptShield features an embedded **Deterministic Heuristic Engine** that runs offline with 0ms latency. Adding an API key simply enables semantic generative AI explanations.
