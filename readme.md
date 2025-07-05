# 🧠 Career Conversation Chatbot – Powered by OpenAI & Hugging Face

This project is a conversational chatbot designed to represent myself in a professional setting. It's deployed as a Hugging Face Space and uses OpenAI's GPT-4o-mini model to answer questions about my career, experiences and background.

[🔗 Live Demo on Hugging Face](https://huggingface.co/spaces/arnabmukherjee91/career_conversation)

---

## ✨ Features

- ✅ **Persona Simulation** – The bot responds, using my LinkedIn profile and a provided summary.
- 📥 **Contact Capture** – Users can leave their email, which is pushed via **Pushover notifications**.
- ❓ **Knowledge Gaps** – If the bot can't answer a question, it logs the query using Pushover.
- 📄 **Document Parsing** – Reads and processes resume from PDF (`linkedin.pdf`) and a written summary (`summary.txt`).
- 🤖 **Gradio Interface** – Easy-to-use chat UI powered by [Gradio](https://gradio.app/).

---

## 🏗️ How It Works

### 1. **Persona Setup**
The bot reads from two files:
- `me/summary.txt`: A text summary of some background.
- `me/linkedin.pdf`: LinkedIn profile exported as PDF.

It uses these to construct a detailed `system_prompt` to guide GPT-4o's behavior.

### 2. **Chat Function**
The chat loop:
- Sends user + history + system prompt to OpenAI.
- Responds using GPT-4o-mini.
- If tools like `record_user_details` or `record_unknown_question` are triggered, they are called automatically and the results added to the conversation.

### 3. **Logging Tools**
Two custom tools use the [Pushover API](https://pushover.net) to notify you in real-time:
- `record_user_details`: Stores user email, name, and notes.
- `record_unknown_question`: Logs unanswered questions.

### 4. **Email Automation Feature (July Update)**
This application implements an intelligent email automation pipeline using OpenAI agents and SendGrid for transactional email delivery. The core features include:
- Tool-Driven Workflow: The agent uses modular tools for each step in the email automation process.
- Subject Line Generation – A custom tool subject_writer generates attention-grabbing email subjects.
- HTML Conversion – The html_converter tool formats plain text or markdown into polished, responsive HTML.
- Email Dispatch – The send_html_email tool uses the SendGrid API to send emails to specified recipients.
- [🔗 Live Demo on Hugging Face](https://huggingface.co/spaces/arnabmukherjee91/career_bot)
  
  
---

## 📁 Folder Structure

- career_conversation_chatbot/
- │
- ├── app.py # Main app logic
- ├── requirements.txt # Python dependencies
- ├── README.md # This file!
- └── me/
- ├── summary.txt # written career summary
- └── linkedin.pdf # Exported LinkedIn profile

