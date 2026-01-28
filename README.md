# 🤖 AI Telegram Expense Tracker (n8n Powered)

**AI-powered expense tracking system** that works through **Telegram** and is fully automated using **n8n workflows**, **OpenAI**, and **Google Sheets**.

Track your expenses by simply sending a **text** or **voice message** — the system understands natural language and logs everything automatically.

---

## 🚀 Features

- 💬 Track expenses using **Telegram messages**
- 🎤 Supports **voice notes** (automatically transcribed)
- 🧠 AI understands natural language like:
  > *"I bought shoes from Nike yesterday for 12,000 LE"*
- 📅 Converts **relative dates** (today, yesterday, last week) into real calendar dates
- 🧾 Extracts:
  - Item
  - Price
  - Place
  - Date
- 📊 Automatically logs data into **Google Sheets**
- ⚙️ Fully automated using **n8n**

---

## 🧠 How the Workflow Works

### 1️⃣ Telegram Trigger
The workflow starts when a message is sent to the Telegram bot.

### 2️⃣ Message Type Detection (Switch Node)

| Message Type | Flow |
|-------------|------|
| **Text** | → Edit Fields → AI Agent |
| **Voice** | → Get File → Transcribe Recording → AI Agent |

---

### 3️⃣ AI Agent (Brain of the System)

The AI Agent:
- Understands what the user bought
- Detects price, item, store/place, and date
- Handles messy human language naturally

---

### 4️⃣ JavaScript Code Node #1 — Date Converter

Converts relative time expressions into real dates.

**Example Input:**
```
"I bought shoes yesterday"
```

**Converted To:**
```
Date: 2026-01-27
```

Handles:
- today
- yesterday
- last week
- specific phrases

---

### 5️⃣ JavaScript Code Node #2 — Data Structuring

Transforms AI output into structured fields:

| Field | Example |
|------|---------|
| Item | Shoes |
| Price | 12000 |
| Place | Nike |
| Date | 2026-01-27 |

---

### 6️⃣ Google Sheets Integration

The final structured data is automatically appended to a spreadsheet.

Your sheet becomes a full expense dashboard 📊

---

## 🛠 Tech Stack

- **n8n** — Workflow automation
- **Telegram Bot API**
- **OpenAI** — Natural language understanding
- **JavaScript (Code Nodes)** — Data processing
- **Google Sheets API** — Expense storage

---

## 🧩 Example User Message

```
I bought a jacket from Zara yesterday for 3,500 LE
```

### System Extracts:

| Item | Place | Price | Date |
|------|------|------|------|
| Jacket | Zara | 3500 | 2026-01-27 |

---

## 🎯 Why This Project is Powerful

This is not just a bot — it's an **AI-powered financial assistant** that:
- Understands human language
- Processes voice & text
- Structures financial data automatically
- Requires zero manual entry

---

## 👨‍💻 Author
**ENG Mohamed Magdy Elghandour**  
  AI Engineer specialized in AI Automation

