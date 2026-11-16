# Prompt Engineering & Human-in-the-Loop Architecture

## 1. Structured JSON Prompt Design
To enable reliable conditional routing inside n8n without parsing errors, the Google Gemini node (`models/gemini-3-flash-preview`) is instructed to act as a deterministic classifier rather than a conversational chatbot.

### Production Prompt Used:
```text
You are an expert Customer Experience Analyst. Analyze the customer review provided below. Output ONLY a valid JSON object without any markdown tags (do not use ```json) or extra text.
The JSON must contain exactly these three keys:

"sentiment": (Positive, Neutral, or Negative)

"score": (Number from 1 to 5)

"urgency": (High, Medium, or Low. If Negative, it MUST be High)
Customer Review: {{ $json['  Review / Feedback  '] }}