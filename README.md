# 🚨 AI Customer Sentiment Analyzer & Emergency Alerter

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google%20Gemini-3%20Flash%20Preview-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white)
![Telegram Bot](https://img.shields.io/badge/Telegram-Instant%20Alerts-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-CX%20Analytics-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Cost](https://img.shields.io/badge/Operating%20Cost-$0%20%2F%20Zero--Cost-brightgreen?style=for-the-badge)

A **100% zero-cost, real-time Customer Experience (CX) automation system** built with **n8n** and **Google Gemini API**. It captures incoming customer feedback, performs deterministic AI sentiment classification, triggers instant **Human-in-the-Loop (HITL)** emergency alerts on Telegram for negative reviews, and logs all structured metrics into Google Sheets for CX analytics.

---

## 🎥 Live Video Walkthrough

Watch the full end-to-end live demonstration of the workflow in action:

[![Watch the Demo Video](https://img.youtube.com/vi/R_kQBFPZDQk/maxresdefault.jpg)](https://youtu.be/R_kQBFPZDQk?si=BCn-4X_eLFvuAjVa)

👉 **[Click here to watch the full demo on YouTube](https://youtu.be/R_kQBFPZDQk?si=BCn-4X_eLFvuAjVa)**

---

## 🎯 Business Problem & Solution

### The Problem
Businesses collecting customer feedback via forms or surveys often discover critical complaints hours or days later. Meanwhile, relying on AI to automatically reply to angry customers risks hallucinated refund promises, robotic tone, and brand damage.

### The Solution
- **Instant AI Triage:** Every new review is analyzed within seconds using `gemini-3-flash-preview` to extract **Sentiment**, **Score (1–5)**, and **Urgency**.
- **Human-in-the-Loop Escalation:** Negative reviews (`Sentiment: Negative`) bypass automated replies and immediately fire an **Emergency Alert** to the support team's Telegram with customer contact details for rapid human resolution.
- **Centralized CX Reporting:** Every single review (Positive, Neutral, and Negative) is parsed and appended to a structured **Customer Analytics Log** in Google Sheets.
- **Zero-Cost Architecture:** Built entirely on free-tier tools (self-hosted n8n, Google AI Studio Free Tier, Google Sheets, and Telegram Bot API).

---

## 🏗️ System Architecture

```mermaid
flowchart LR
    A[Google Form Submission] --> B[Google Sheets Trigger]
    B --> C[Google Gemini AI<br/>Sentiment & Urgency JSON]
    C --> D{Switch Node<br/>Contains 'Negative'?}
    C --> E[Google Sheets<br/>Customer Analytics Log]
    D -- Yes --> F[Telegram Bot<br/>Emergency Human Alert]
    D -- No --> G[Logged Only]
```

---

## 📸 Live System Proof

### 1. n8n Automation Workflow
End-to-end pipeline handling polling, Gemini JSON extraction, conditional routing, Telegram alerting, and parallel Google Sheets logging.
![n8n Workflow Canvas](assets/workflow-canvas.png)

### 2. Real-Time Telegram Emergency Alert
Instant mobile notification delivered to the CX team whenever a negative review is detected.
![Telegram Emergency Alert](assets/telegram-alert-demo.jpg)

### 3. Automated CX Analytics Log
Structured sentiment scores and urgency levels automatically recorded for reporting and trend tracking.
![Google Sheets Analytics Log](assets/analytics-sheet-log.png)

---

## 📂 Repository Structure

```text
ai-customer-sentiment-emergency-alerter/
├── assets/
│   ├── workflow-canvas.png          # Full n8n workflow screenshot
│   ├── telegram-alert-demo.jpg      # Live Telegram emergency notification proof
│   └── analytics-sheet-log.png      # Structured Google Sheets log output
├── data/
│   ├── sample-reviews.csv           # Sample customer feedback input
│   └── gemini-output-example.json   # Deterministic JSON output from Gemini
├── docs/
│   ├── setup-guide.md               # Step-by-step deployment instructions
│   └── prompt-engineering.md        # JSON prompt design & HITL architecture notes
├── workflows/
│   └── customer-sentiment-analyzer.json  # Sanitized, import-ready n8n workflow
├── .env.example                     # Required environment variables template
├── .gitignore                       # Security rules to exclude secrets & raw backups
└── README.md                        # Project overview & documentation
```

---

## 🚀 Quick Start

1. **Clone this repository:**
   ```bash
   git clone [https://github.com/fhm16/ai-customer-sentiment-emergency-alerter.git](https://github.com/fhm16/ai-customer-sentiment-emergency-alerter.git)
   ```
2. **Import the Workflow into n8n:**
   - Open n8n and import `workflows/customer-sentiment-analyzer.json`.
3. **Connect Your Free-Tier Credentials:**
   - **Google Sheets:** Connect OAuth2 credentials for both the Input Form Sheet and the Analytics Log Sheet.
   - **Google Gemini:** Add your free API key from [Google AI Studio](https://aistudio.google.com/).
   - **Telegram:** Add your Bot Token from `@BotFather` and set your target `Chat ID`.
4. **Activate:** Toggle the workflow to **Active** in n8n.

👉 For detailed configuration steps, read the **[Step-by-Step Setup Guide](docs/setup-guide.md)** and **[Prompt Engineering Notes](docs/prompt-engineering.md)**.

---

## 🛡️ Security & Privacy Best Practices
- All sensitive API keys, OAuth tokens, Spreadsheet IDs, and Telegram Chat IDs have been sanitized from `workflows/customer-sentiment-analyzer.json`.
- `.gitignore` is pre-configured to prevent accidental commits of `.env` files or raw local workflow exports.

---

## 📬 Contact & Connect

- **GitHub:** [@fhm16](https://github.com/fhm16)
- **Email:** [ferdoushasanmaruf16@gmail.com](mailto:ferdoushasanmaruf16@gmail.com)
