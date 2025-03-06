# 🚀 Telegram AI Assistant Automation using n8n

This repository showcases an intelligent automation workflow built using **n8n**, integrating **Telegram**, **OpenAI**, **Gmail**, and **Google Calendar**. The automation is designed to process incoming text and voice messages from Telegram, leverage **AI transcription and decision-making**, and interact with **email and calendar services** based on user prompts.

---

## 📋 Overview

This project demonstrates how **n8n**, a powerful no-code/low-code automation platform, can be used to build a conversational AI assistant that automates day-to-day tasks via **Telegram**. Users can send either text or voice messages to a Telegram bot, and based on the content, the system can:

- Read emails matching specific criteria.
- Send custom emails with dynamic content.
- Fetch Google Calendar events.
- Create new Google Calendar events.

---

## 🔗 Workflow Architecture

### 1. Telegram Trigger
The workflow starts with a **Telegram Trigger** node, listening for new messages (text or voice).

### 2. Message Type Detection
A **Switch Node** evaluates if the message is **text** or **voice**.

### 3. Voice Transcription (OpenAI Whisper)
If it's a voice message, the file is retrieved via **Telegram Get File**, then sent to **OpenAI Transcribe Recording (Whisper)** to convert speech to text.

### 4. Text Processing
For text messages (or transcribed voice messages), the content is processed using **n8n's AI Agent Node** (powered by OpenAI Chat models). This agent decides the required action based on the user's intent.

---

## 🤖 AI Agent & Toolset

The **AI Agent** is configured with the following tools:

### 1. 📧 Gmail: Read Emails
- Reads Gmail inbox based on user-defined criteria (like subject, sender, date, etc.).
- Provides a summarized response to the user via Telegram.

### 2. 📤 Gmail: Send Emails
- Composes and sends emails to a specified recipient with:
    - Custom subject line
    - Body content generated based on user input
    - AI-generated content if needed

### 3. 📅 Google Calendar: Read Events
- Fetches events from Google Calendar for a specified date or time range.
- Provides a summary of the events back to the user via Telegram.

### 4. 📆 Google Calendar: Create Events
- Creates new calendar events with:
    - Title
    - Date and Time
    - Description (optional)

---

## ⚙️ Key Technologies

| Technology | Purpose |
|---|---|
| **n8n** | Automation engine |
| **Telegram Bot API** | Message input/output |
| **OpenAI Whisper** | Voice-to-text transcription |
| **OpenAI GPT** | AI decision-making and content generation |
| **Gmail API** | Email reading and sending |
| **Google Calendar API** | Calendar event management |

---


## 📚 How to Use

### Prerequisites
- An **n8n** instance (self-hosted or cloud)
- Telegram Bot Token
- OpenAI API Key
- Google Cloud Project with Gmail and Calendar API enabled
- Service Account credentials for Google APIs

### Steps
1. Import the workflow into your n8n instance.
2. Set up environment variables for API keys and tokens.
3. Configure the Telegram Trigger node with your bot token.
4. Link your Gmail and Google Calendar nodes using OAuth or Service Account credentials.
5. Start the workflow and send messages to your Telegram bot to test.

---

## 🏁 Example Use Cases

| Scenario | Example Prompt |
|---|---|
| Read Emails | "Show me emails from John received today" |
| Send Email | "Send an email to hr@company.com with the subject 'Leave Request' and message 'I need leave for tomorrow'" |
| Read Calendar | "What are my meetings today?" |
| Create Event | "Add a meeting with the product team tomorrow at 3 PM" |

---

## 🔒 Security Considerations

- Always store API keys and credentials securely (use environment variables or n8n credentials manager).
- Ensure your Telegram bot token is kept private.
- Use **rate limiting** if exposing the bot to public users.

---


## 🌐 Links

- [n8n Documentation](https://docs.n8n.io)
- [OpenAI API Docs](https://platform.openai.com/docs/)
- [Telegram Bot API Docs](https://core.telegram.org/bots/api)
- [Google Calendar API Docs](https://developers.google.com/calendar)
- [Gmail API Docs](https://developers.google.com/gmail/api)

---
