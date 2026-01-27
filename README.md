# Telegram-AI-Expense-Tracker-n8n-Powered
AI-Powered Expense Tracking System With a Telegram Interface, Built Using n8n Workflows, OpenAI, and Google Sheets
AI Expense Tracking System
An AI-powered financial automation system that allows users to log expenses using Telegram (text or voice messages).
The system understands natural language, structures financial data, and automatically stores it in Google Sheets for tracking and analysis.
This project represents a production-style AI data extraction and processing pipeline, not just a simple bot.
🚀 Project Overview
This system works as an intelligent personal finance assistant that can understand messages like:
“Spent 250 EGP on dinner”
“دفعت 100 جنيه مواصلات”
Voice note saying the same thing
The system processes the message, extracts financial data, normalizes it, and logs it into a structured database.
⚙️ Workflow Architecture
Built using n8n, the workflow handles both text and voice inputs.
🔹 Step 1 — Telegram Trigger
The workflow starts when the user sends a message to the Telegram bot.
🔀 Step 2 — Message Type Detection (Switch Node)
Message Type
Workflow Path
Text
→ Edit Fields → AI Agent
Voice
→ Get File → Transcribe Recording → AI Agent
✏️ Text Message Flow
نسخ التعليمات البرمجية

Telegram Trigger
   → Switch (Text)
      → Edit Fields
         → AI Agent
The Edit Fields node prepares message data before AI processing.
🎤 Voice Message Flow
نسخ التعليمات البرمجية

Telegram Trigger
   → Switch (Voice)
      → Get File
         → Transcribe Recording
            → AI Agent
Voice messages are converted into text before AI analysis.
🤖 AI Agent — Financial Data Extraction Engine
At the core of the system is a specialized AI Financial Data Extraction Agent.
This is not a chatbot.
It is a structured data processor.
🎯 Agent Role
The AI is instructed to:
Convert user expense messages into structured JSON data.
It processes:
Text input
Transcribed voice input
📜 Agent Rules & Constraints
To ensure reliable automation:
Output MUST be valid JSON only
No conversational text
No markdown formatting
Missing values must be "null"
Must extract:
Merchant
Price
Item
Date
Currency
📅 Dynamic Date Awareness
The system provides today's real date dynamically:
نسخ التعليمات البرمجية

Today's Date: {{ $now }}
This helps the AI interpret:
User Says
Converted To
yesterday
Actual calendar date
today
Current date
last week
Calculated date
🧱 Required AI Output Structure
نسخ التعليمات البرمجية
Json
{
  "expense_details": {
    "merchant": "string",
    "price": number,
    "item": "string",
    "date": "YYYY-MM-DD",
    "currency": "string"
  },
  "original_query": "string"
}
🧩 Intelligent Data Processing Layer (JavaScript)
After AI extraction, two JavaScript nodes refine the data.
📅 JavaScript Node #1 — Smart Date Conversion
Converts relative time expressions into exact dates.
Example
User:
“I bought shoes from Nike yesterday for 12,000 LE”
Before:
نسخ التعليمات البرمجية

date: "yesterday"
After:
نسخ التعليمات البرمجية

date: "2026-01-26"
✔ Ensures accurate financial reporting
✔ Removes time ambiguity
🧱 JavaScript Node #2 — Expense Structuring Engine
Breaks down the sentence into fully separated financial fields.
Input Sentence
“I bought shoes from Nike yesterday and the price was 12,000 LE”
Final Structured Output
نسخ التعليمات البرمجية
Json
{
  "item": "Shoes",
  "brand": "Nike",
  "amount": 12000,
  "currency": "LE",
  "category": "Shopping",
  "date": "2026-01-26",
  "description": "Bought shoes from Nike"
}
🧠 Why This Layer Matters
Feature
Benefit
Date normalization
Enables monthly & yearly analysis
Field separation
Clean database structure
AI + Code logic
Higher reliability
Standardized records
Ready for dashboards
📊 Database Layer — Google Sheets
All processed expenses are automatically appended.
Date
Amount
Currency
Category
Description
Supports:
Monthly tracking
Spending analysis
Budget monitoring
Financial reports
🔬 Full Intelligence Flow
نسخ التعليمات البرمجية

User (Telegram)
   → Message Type Detection
      → AI Financial Extraction Agent
         → JS Date Normalization
            → JS Data Structuring
               → Google Sheets Database
🛠 Tech Stack
Tool
Role
n8n
Workflow engine
Telegram Bot API
User interface
OpenAI
Language understanding
Transcription AI
Voice → Text
JavaScript Nodes
Data normalization
Google Sheets API
Expense database
🧠 Engineering Value
This system combines:
AI Understanding Layer
+
Prompt Engineering Control
+
JavaScript Logic Processing
+
Structured Data Storage
Result:
A reliable AI-to-database financial automation system.
🎯 Use Cases
Personal finance tracking
AI automation portfolio project
Smart assistant systems
Expense monitoring
Budget awareness
🔮 Future Improvements
Budget alerts
Monthly AI reports
Spending dashboards
Category-based analytics
Telegram commands for stats
🏗 Project Type
AI Expense Tracking System
A scalable AI-powered financial data extraction and automation pipeline.
