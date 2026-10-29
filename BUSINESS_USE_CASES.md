# 💼 PromptShield — Business Use Cases Specification
**Project by:** Team ByteBusters (Lead Developer: Yashwanth Pathiwada)  
**Hackathon Deliverable:** Item 7 — Business Use Cases

---

## 📌 Executive Overview
This document outlines 6 real-world operational business use cases for PromptShield. It demonstrates how different demographic actors interact with the system to prevent fraud, report crimes, and protect their digital assets.

---

### 🔹 BUC-01: Analysis of Urgent Fake Bank KYC / PAN Suspension Smishing SMS
- **Primary Actor:** Senior Citizen / Digital Banking Customer (e.g., Rajesh Kumar, 62).
- **Trigger:** Receives SMS: *"Dear Customer, your SBI account will be blocked today. Update PAN immediately at http://bit.ly/sbi-pan-update"*.
- **Pre-Conditions:** User receives message and opens PromptShield.
- **Main Workflow:**
  1. User pastes SMS into PromptShield and clicks *Analyze*.
  2. Deterministic engine flags urgent deadline (*"blocked today"*), shortlink (*"bit.ly"*), and banking keyword (*"PAN"*).
  3. GenAI evaluates semantic intent: identifies credential harvesting impersonating State Bank of India.
  4. System computes **Risk Score of 94/100 (Red — Likely Scam)**.
  5. UI highlights the manipulative clauses in context and provides a clear explanation.
  6. UI renders checklist: *Do NOT click link; Do NOT enter OTP; Verify directly in official YONO app*.
- **Post-Conditions:** User refrains from clicking link and avoids financial compromise.
- **Business Value:** Prevents direct unauthorized banking debits and credential theft.

---

### 🔹 BUC-02: Detection of Telegram / YouTube "Part-Time Task" Job Scam
- **Primary Actor:** University Student / Job Seeker (e.g., Ananya Sharma, 20).
- **Trigger:** Unsolicited WhatsApp message offering ₹5,000/day for liking YouTube videos and joining a Telegram channel.
- **Pre-Conditions:** User is evaluating the offer and seeks verification before transferring money.
- **Main Workflow:**
  1. User pastes job offer text into PromptShield.
  2. System detects advance-fee/task pyramid fraud indicators (*"like YouTube videos"*, *"daily salary ₹5000"*, *"deposit required to unlock earnings"*).
  3. System assigns **Risk Score of 88/100 (Red — Likely Scam)**.
  4. Explainer reveals the deception tactic: scammers pay minor sums initially (₹150) before demanding deposits to unlock "commissions".
  5. Checklist instructs: *Block sender; Never pay money to receive wages; Report phone number*.
- **Post-Conditions:** Student declines the offer, saving semester funds.
- **Business Value:** Protects vulnerable young demographics from task-based financial scams.

---

### 🔹 BUC-03: Verification of Legitimate E-Commerce / Courier Delivery (False Positive Prevention)
- **Primary Actor:** E-Commerce Shopper / Professional (e.g., Vikram Malhotra, 34).
- **Trigger:** Automated SMS: *"Your BlueDart parcel #7392819 will be delivered today. Track at bluedart.com"*.
- **Pre-Conditions:** User wishes to confirm authenticity before contacting courier personnel.
- **Main Workflow:**
  1. User submits courier message for analysis.
  2. Deterministic engine confirms official domain (`bluedart.com`) and absence of urgent payment or credential requests.
  3. GenAI confirms transactional context with zero coercive triggers.
  4. System computes **Risk Score of 10/100 (Green — Safe)**.
  5. UI displays safe status with zero red flags.
- **Post-Conditions:** User receives package without unnecessary fear or delay.
- **Business Value:** Validates high model specificity; avoids false alarms on genuine commercial communications.

---

### 🔹 BUC-04: Detection of Fake Electricity Disconnection Extortion Threat
- **Primary Actor:** Small Business Owner / Residential Consumer.
- **Trigger:** SMS at 7:00 PM: *"Electricity power disconnected at 9:30 PM tonight due to unpaid bill. Immediately contact Officer at 9123456789"*.
- **Pre-Conditions:** User is startled by the imminent disconnection notice.
- **Main Workflow:**
  1. User analyzes message using PromptShield.
  2. Heuristic engine flags severe urgency (*"tonight 9:30 PM"*), disconnection threat, and unofficial personal mobile number.
  3. System flags **Risk Score of 92/100 (Red — Likely Scam)**.
  4. Checklist clarifies: *Government power boards never disconnect power via personal mobile SMS or ask for remote access apps (AnyDesk/TeamViewer)*.
- **Post-Conditions:** User checks billing status on the official electricity board portal; confirms zero arrears.
- **Business Value:** Neutralizes widespread extortion schemes targeting residential and commercial power consumers.

---

### 🔹 BUC-05: One-Click Generation of Cybercrime Complaint for Helpline 1930
- **Primary Actor:** Scam Target / Citizen Reporting Cybercrime.
- **Trigger:** Citizen identifies a confirmed scam and wants to file an official complaint.
- **Pre-Conditions:** PromptShield has analyzed a message and classified it as Suspicious or Likely Scam.
- **Main Workflow:**
  1. User scrolls to the *Official Cybercrime Report* section.
  2. System auto-compiles a standardized incident complaint containing:
     - Threat Classification
     - Sender Identification & Timestamp
     - Neutralized Evidence Text & Defanged URLs
     - PromptShield Analytical Verdict (Score & Red Flags)
  3. User clicks *Copy Official Incident Complaint*.
  4. Formatted text is copied to the clipboard, with one-click links to `cybercrime.gov.in` and Helpline `1930`.
- **Post-Conditions:** Law enforcement receives standardized, evidence-rich complaints.
- **Business Value:** Cuts grievance drafting time from 15 minutes to under 5 seconds.

---

### 🔹 BUC-06: Autonomous Heuristic Engine Fallback During Cloud AI Outage
- **Primary Actor:** Evaluation Jury / User with Poor Internet.
- **Trigger:** Upstream cloud LLM API (Gemini/OpenAI) experiences downtime or rate limits.
- **Pre-Conditions:** User submits a message during an active upstream API disruption.
- **Main Workflow:**
  1. User submits text for analysis.
  2. Backend FastAPI detects API timeout / error.
  3. Built-in Circuit Breaker activates seamlessly.
  4. System routes request to the *Deterministic Heuristic Core*.
  5. Heuristic engine scans 40+ rules and returns a complete `AnalyzeResponse` with `is_fallback: true`.
  6. UI renders accurate risk score, highlighted flags, and safety checklist without throwing a 500 error.
- **Post-Conditions:** 100% application uptime maintained during live evaluations and outages.
- **Business Value:** Guarantees zero-crash reliability during critical hackathon evaluations.
