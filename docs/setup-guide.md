# Step-by-Step Setup Guide

Follow this guide to deploy the **Customer Sentiment Analyzer & Emergency Alerter** workflow in your own n8n instance at zero cost.

## Prerequisites
- **n8n** (Self-hosted on Localhost/Docker or n8n Cloud)
- **Google Account** (for Google Forms & Google Sheets)
- **Google AI Studio API Key** (Free Tier)
- **Telegram Account** (for instant mobile alerts)

---

## Step 1: Configure Google Forms & Sheets
1. **Input Form & Sheet:**
   - Create a Google Form with three fields: `Customer Name`, `Email`, and `Review / Feedback`.
   - Link the form to a Google Sheet (default tab: `Form responses 1`).
2. **Analytics Log Sheet:**
   - Create a separate Google Sheet (or a new tab) named `Customer Analytics Log`.
   - Add the exact following column headers in Row 1:
     `Timestamp` | `Customer Name` | `Email` | `Review` | `Sentiment` | `Score` | `Urgency`

---

## Step 2: Get Your Free Gemini API Key
1. Go to [Google AI Studio](https://aistudio.google.com/).
2. Generate a free API key and copy it for n8n configuration.

---

## Step 3: Set Up the Telegram Alert Bot
1. Open Telegram and search for **`@BotFather`**.
2. Send `/newbot`, follow the instructions to name your bot, and copy the **HTTP API Token**.
3. Open your newly created bot's chat and click **Start**.
4. Search for **`@userinfobot`** on Telegram, send any message, and copy your numeric **Chat ID**.

---

## Step 4: Import & Configure the n8n Workflow
1. Open your n8n canvas, click the menu icon (`...`), and select **Import from File**.
2. Upload `workflows/customer-sentiment-analyzer.json`.
3. Update the credentials and placeholders in each node:
   - **Google Sheets Trigger:** Connect your Google OAuth2 credential and paste your Input Google Sheet URL.
   - **Message a model (Google Gemini):** Add your Gemini API Key credential and ensure the model is set to `models/gemini-3-flash-preview`.
   - **Send a text message (Telegram):** Add your Telegram Bot API Token credential and replace `YOUR_TELEGRAM_CHAT_ID` with your numeric Chat ID.
   - **Append row in sheet (Google Sheets):** Connect your Google Sheets credential and select your `Customer Analytics Log` spreadsheet.

---

## Step 5: Test & Activate
1. Submit a test entry through your Google Form (e.g., *"The service was very bad."*).
2. Click **Execute Workflow** in n8n to verify:
   - Negative reviews trigger an immediate Telegram message.
   - All reviews (Positive, Neutral, Negative) are appended to the `Customer Analytics Log` sheet.
3. Toggle the workflow status to **Active** in the top-right corner to run it automatically every minute.