# 🌟 PromptShield — Comprehensive Feature Specification
**Project by:** Team ByteBusters (Lead Developer: Yashwanth Pathiwada)  
**Hackathon Deliverable:** Item 6 — Feature List

---

## 📌 Executive Summary of Capabilities
PromptShield bridges the "Explainability Gap" in modern cybersecurity. Rather than offering a binary "spam vs. not spam" tag, it empowers citizens with transparent cognitive explanations, contextual red-flag highlighting, dynamic risk metrics, actionable checklists, and official cybercrime reporting.

---

## 🛡️ Category 1: Threat Ingestion & Parsing
- **Multi-Vector Input Support:** Accepts pasted SMS texts, emails, WhatsApp messages, Telegram task offers, and delivery notifications up to 10,000 characters.
- **Unicode & Zero-Width Sanitization:** Automatically normalizes homoglyph/lookalike characters (e.g. Cyrillic `а` substituted for Latin `a`) and strips zero-width hidden spaces used to evade spam filters.
- **One-Click Quick Presets:** Includes 5 built-in benchmark test scenarios (Fake Bank KYC, Telegram Job Scam, Electricity Disconnection, Courier Smishing, Genuine Courier Alert) for instantaneous evaluator testing.

---

## ⚙️ Category 2: Dual-Engine Threat Intelligence
- **Engine 1: Deterministic Heuristic Core:**
  - Evaluates 40+ pre-compiled regular expressions and keyword taxonomies in under 50ms.
  - Detects urgency triggers, deadline coercion, OTP traps, unauthorized banking demands, shortlinks (`bit.ly`, `tinyurl`), and spoofed telecom sender prefixes.
  - Operates 100% offline with zero cloud dependency.
- **Engine 2: Cognitive Generative AI Reasoner:**
  - Integrates Gemini 1.5 Flash, Claude 3.5 Sonnet, or OpenAI GPT-4o-mini for deep semantic intent classification.
  - Evaluates social engineering vectors: Authority Impersonation, Artificial Scarcity, Fear Extortion, and Greed Traps.
- **Circuit Breaker & Fallback Guardrail:**
  - Strict Pydantic JSON schema enforcement prevents LLM hallucinations.
  - Automatically falls back to the deterministic heuristic engine if the cloud LLM times out or hits API rate limits.

---

## 📊 Category 3: Explainable Risk Scoring & Visualization
- **Dynamic 0–100 Color-Coded Risk Gauge:**
  - 🟢 **Safe (0–30):** Legitimate transactional or personal communication; zero manipulative indicators.
  - 🟡 **Suspicious (31–69):** Ambiguous origin, unverified external links, or mild unsolicited offers.
  - 🔴 **Likely Scam (70–100):** High-severity credential harvesting, UPI payment fraud, or legal arrest threats.
- **Interactive In-Context Red-Flag Highlighter:**
  - Directly highlights deceptive words and phrases within the user's original message.
  - Hovering or clicking any highlighted flag displays a dedicated popover explaining the exact psychological or technical trap.
- **Threat Vector Categorization:**
  - Automatically classifies messages into recognized threat types: *Banking & KYC Phishing, Task & Employment Fraud, Utility Extortion, Courier/Parcel Smishing, or UPI QR Deception*.

---

## 📋 Category 4: Actionable Defense & Incident Response
- **Interactive Safety Protocol:**
  - **What To Do Next:** Step-by-step tickable checklist (e.g., *Freeze netbanking, report sender phone number, verify via official bank app*).
  - **What NOT To Do:** Critical prohibitions (e.g., *Never share OTP, never click shortlinks, never enter UPI PIN to receive funds*).
- **1-Click National Cybercrime Portal Report (Helpline 1930):**
  - Auto-compiles an official incident complaint formatted according to Indian Cyber Crime Reporting standards (`cybercrime.gov.in` / National Helpline `1930`).
  - Automatically extracts and defangs suspicious URLs and sender phone numbers.
  - One-click copy button copies the ready-to-file complaint to the clipboard.
- **Hyperlink Neutralizer:**
  - Deactivates live hyperlinks in suspicious messages to prevent accidental clicks that trigger drive-by malware.

---

## 🔒 Category 5: Privacy & Ethical Architecture
- **Zero-Storage Server Stance:**
  - User messages are processed ephemerally in RAM and are never written to server disks or databases.
  - Full compliance with the Digital Personal Data Protection (DPDP) Act 2023 and GDPR privacy tenets.
- **Local-First History Drawer:**
  - Past scan results are saved strictly inside the user's browser `localStorage`.
  - Users can view, re-inspect, or permanently clear their local scan history at any time.

---

## 📚 Category 6: Citizen Scam Awareness Hub
- **Interactive Educational Knowledge Base:**
  - Built-in guides deconstructing the 6 most prevalent modern Indian cyber fraud patterns:
    1. *Bank KYC & Account Block Smishing*
    2. *YouTube Like / Telegram Task Job Traps*
    3. *Electricity Bill & Utility Disconnection Extortion*
    4. *India Post / Courier Redirection Scams*
    5. *UPI QR Code "Scan to Receive Money" Fraud*
    6. *"Digital Arrest" Fake Police Video Call Extortion*
