# 🚀 AI Startup Idea Generator Chatbot

An AI-powered chatbot that generates complete startup concepts from a single domain prompt — covering ideas, market research, business strategy, and an investor pitch — all in one conversational interface.

---

## 📌 Overview

This project uses **CrewAI** to orchestrate a team of 4 specialized AI agents that collaborate sequentially to produce a full startup brief. The chatbot interface is built with **Gradio**, and the agents are powered by **OpenAI's LLM** backend.

Just type a domain like `fintech` or `healthcare` and get back a structured startup package instantly.

---

## 🏗️ Architecture

```
User Input (Gradio UI)
        │
        ▼
  CrewAI Crew  (last 3 turns of context)
  ┌─────────────────────────────────────────────┐
  │  Agent 1: Startup Idea Generator            │
  │  Agent 2: Market Researcher                 │
  │  Agent 3: Business Strategist               │
  │  Agent 4: Pitch Creator                     │
  └─────────────────────────────────────────────┘
        │
        ▼
   OpenAI LLM (executes each task)
        │
        ▼
  Formatted Response → Gradio Chatbot
```

### Agents & Tasks

| Agent | Goal | Output |
|---|---|---|
| Startup Idea Generator | Generate 2 innovative AI startup ideas | 2 ideas (max 30 words each) |
| Market Researcher | Analyze demand, users, and competitors | 3 bullet points |
| Business Strategist | Define revenue model, pricing, and growth | 3 bullet points |
| Pitch Creator | Craft a compelling investor pitch | 3-line pitch (problem → solution → vision) |

---

## ✨ Features

- 💬 Conversational chatbot with rolling 3-turn memory
- 🤖 4 specialized CrewAI agents working in sequence
- 📊 Market analysis and business strategy in one shot
- 🎤 Auto-generated investor pitch for every idea
- 🖥️ Clean Gradio UI with chat history and clear button

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| [CrewAI](https://github.com/joaomdmoura/crewAI) | Multi-agent orchestration |
| [OpenAI API](https://platform.openai.com/) | LLM backend for all agents |
| [Gradio](https://gradio.app/) | Web-based chatbot interface |

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/your-username/ai-startup-idea-generator.git
cd ai-startup-idea-generator
```

### 2. Install dependencies
```bash
pip install crewai==0.28.8 gradio==3.50.2 openai
```

### 3. Set your OpenAI API key
Open the notebook and replace the placeholder with your key:
```python
os.environ["OPENAI_API_KEY"] = "your-openai-api-key-here"
```
Or set it as an environment variable:
```bash
export OPENAI_API_KEY="your-openai-api-key-here"
```

### 4. Run the notebook
Open `AIStartupIdea.ipynb` in Jupyter and run all cells. A Gradio link will appear — open it in your browser.

---

## 💬 Usage

1. Launch the chatbot
2. Type a domain or problem space, e.g.:
   - `fintech`
   - `AI tools for teachers`
   - `mental health for Gen Z`
3. Get back a full startup brief including ideas, market research, business model, and pitch

---

## 📁 Project Structure

```
ai-startup-idea-generator/
│
├── AIStartupIdea.ipynb      # Main notebook
└── README.md                # This file
```

---

## ⚠️ Important Notes

- **Never commit your API key** to GitHub. Use environment variables or a `.env` file with `python-dotenv`.
- Each query makes 4 sequential LLM calls (one per agent), so response time depends on OpenAI API latency.
- Chat history is limited to the last 3 turns to keep context concise and costs low.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
