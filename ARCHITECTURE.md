# 🏗️ PromptShield — System Architecture Specification
**Project by:** Team ByteBusters (Lead Developer: Yashwanth Pathiwada)  
**Hackathon Deliverable:** Item 4 — Architecture Diagram

---

## 📌 High-Resolution Architecture Diagram

![PromptShield Architecture Diagram](architecture_diagram.png)

*(The high-resolution diagram `architecture_diagram.png` is committed directly in the repository root).*

---

## 🔄 Interactive Component Architecture (Mermaid)

GitHub natively renders the flowchart below in your browser:

```mermaid
flowchart TD
    subgraph Client["1. Client Presentation Layer (React 18 + Tailwind CSS + Vite)"]
        UI_Input["User Input Area<br/>(SMS / Email / Job / Chat)"]
        UI_Meter["Dynamic Risk Gauge<br/>(0–100 Color Coded)"]
        UI_Highlight["Interactive In-Context<br/>Red-Flag Highlighter"]
        UI_Checklist["Actionable Safety Protocol<br/>(Do's & Don'ts Checklist)"]
        UI_1930["1-Click 1930 Cybercrime<br/>Incident Report Generator"]
        UI_Storage[("Browser LocalStorage<br/>(Zero-Server Privacy History)")]
    end

    subgraph Gateway["2. API Gateway & Controller Layer (FastAPI ASGI + Uvicorn)"]
        API_Sanitize["Input Sanitizer & Unicode Normalizer"]
        API_Router["FastAPI Route Controller<br/>(/analyze, /samples, /health)"]
        API_Static["Static Files Handler (/assets)"]
    end

    subgraph DualEngine["3. Dual-Engine Intelligence Core"]
        direction TB
        subgraph EngineHeuristic["Engine 1: Deterministic Heuristic Core (Offline)"]
            RegexRules["Regex Threat Matcher<br/>(Urgency, KYC, OTP, APKs)"]
            DomainCheck["Shortlink & Domain Verifier<br/>(bit.ly, unverified domains)"]
            ScoreCalc["Heuristic Scoring Engine (< 50ms)"]
        end

        subgraph EngineGenAI["Engine 2: Cognitive Generative AI Reasoner (Cloud)"]
            LLM_Caller["GenAI Orchestrator<br/>(Gemini 1.5 / Claude / GPT)"]
            JSON_Schema["Pydantic Strict JSON Schema Validator"]
            SemanticEval["Cognitive Social Engineering Deconstructor"]
        end

        CircuitBreaker{"Circuit Breaker & Fallback<br/>(API Timeout / Rate Limit?)"}
    end

    subgraph OutputSynthesis["4. Synthesis & Explainability Layer"]
        RiskNormalizer["Unified Risk Normalizer (0-100)"]
        QuoteMatcher["Exact Text Span Offset Mapper"]
        ComplaintCompiler["1930 Cybercrime Complaint Synthesizer"]
    end

    %% Data Flow Connections
    UI_Input -->|"HTTP POST /analyze (JSON)"| API_Sanitize
    API_Sanitize --> API_Router
    API_Router --> RegexRules
    API_Router --> LLM_Caller

    LLM_Caller --> JSON_Schema
    JSON_Schema -->|"Valid JSON"| SemanticEval
    JSON_Schema -->|"Error / Timeout"| CircuitBreaker
    CircuitBreaker -->|"Auto Fallback"| ScoreCalc

    RegexRules --> DomainCheck
    DomainCheck --> ScoreCalc

    ScoreCalc --> RiskNormalizer
    SemanticEval --> RiskNormalizer

    RiskNormalizer --> QuoteMatcher
    QuoteMatcher --> ComplaintCompiler

    ComplaintCompiler -->|"JSON Response"| UI_Meter
    ComplaintCompiler --> UI_Highlight
    ComplaintCompiler --> UI_Checklist
    ComplaintCompiler --> UI_1930
    ComplaintCompiler --> UI_Storage
```

---

## 🧱 Architectural Layer Breakdown

### 1. Presentation Layer (React 18 + Tailwind CSS + Vite)
- Single Page Application (SPA) providing sub-second load times.
- Component-driven architecture using Lucide React icons.
- Local-first architecture: past threat scans are preserved in browser `localStorage`, ensuring zero server-side exposure of private user communications.

### 2. API Gateway & Controller Layer (FastAPI + Python 3.11)
- Asynchronous ASGI architecture powered by Uvicorn, capable of serving high-throughput concurrent requests.
- Input sanitization strips invisible zero-width characters and homoglyph lookalikes before engine evaluation.
- Serves both API endpoints (`/analyze`, `/samples`, `/health`) and mounts compiled frontend static assets (`/assets`) from a unified port.

### 3. Dual-Engine Intelligence Core
- **Engine 1 (Deterministic Heuristic):** 40+ pre-compiled regular expressions evaluating urgency triggers, financial bait, credential theft, and suspicious URL shorteners in under 50ms without external network requests.
- **Engine 2 (Cognitive GenAI Reasoner):** Multi-model support (Gemini 1.5 Flash, Claude 3.5 Sonnet, GPT-4o-mini) translating subtle manipulation patterns into structured JSON.
- **Circuit Breaker:** If a cloud AI API call experiences rate limits or times out, the system automatically degrades to the Deterministic Heuristic Core with zero user interruption.

### 4. Output Synthesis & National Defense Integration
- Normalizes disparate indicators into a unified 0–100 risk score.
- Maps extracted quotes back to character index offsets in the original text to generate interactive highlight spans.
- Formats evidence directly for India's National Cybercrime Portal (`cybercrime.gov.in`) and National Helpline (`1930`).
