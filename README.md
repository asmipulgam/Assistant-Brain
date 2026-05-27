<div align="center">

![Assistant Brain Demo](assets/demo.gif)

[![Python](https://img.shields.io/badge/python-3.11+-blue?logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![LangGraph](https://img.shields.io/badge/built%20with-LangGraph-purple)](https://github.com/langchain-ai/langgraph)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-red?logo=streamlit)](https://streamlit.io)

# 🧠 Assistant Brain
### A personal life operating system powered by agentic AI

*Stop managing your life. Let your Assistant Brain handle it.*

</div>

---

## What is this?

**Assistant Brain** is a multi-agent AI system that autonomously manages your emails, tracks job applications, monitors research papers, and delivers a personalized daily briefing so you can focus on what actually matters.

Built with **LangGraph** and **LangChain**, a supervisor agent orchestrates specialized sub-agents that reason, act, and self-correct across real-world tools like Gmail, Google Calendar, and live web search all backed by a vector memory store that learns your preferences over time.

---

## Features

| Agent | What it does |
|---|---|
| 📧 Email Agent | Reads inbox, categorizes, flags urgent, drafts replies |
| 🔍 Job Hunter Agent | Searches LinkedIn/Handshake, matches your resume, drafts cover letters |
| 📚 Research Agent | Monitors ArXiv/Scholar, summarizes papers, builds your knowledge base |
| 📅 Planner Agent | Extracts deadlines from emails, builds a priority-ranked daily plan |
| ☀️ Morning Briefing | Combines all agents into a 5-minute daily summary |

---

## Architecture

```
You
 │
 ▼
Supervisor Orchestrator (LangGraph)
 ├── Email Agent ──────── Gmail API
 ├── Job Hunter Agent ─── LinkedIn + Handshake
 ├── Research Agent ───── ArXiv + Google Scholar
 ├── Planner Agent ────── Google Calendar API
 └── Morning Briefing ─── All of the above
          │
          ▼
   Vector Memory (ChromaDB)
   Long-term preference store
```

---

## Tech Stack

- **Agent Framework** — LangGraph, LangChain
- **LLM** — Claude (Anthropic) / GPT-4o
- **Memory** — ChromaDB (vector store)
- **Tools** — Gmail API, Google Calendar API, Tavily Search, ArXiv API
- **UI** — Streamlit
- **Voice** — gTTS / ElevenLabs
- **Infra** — Docker, GitHub Actions CI/CD

---

## Quick Start

### 1. Clone the repo
```bash
git clone https://github.com/asmipulgam/assistant-brain.git
cd assistant-brain
```

### 2. Set up environment
```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Configure API keys
```bash
cp .env.example .env
# Fill in your API keys in .env
```

```env
ANTHROPIC_API_KEY=your_key_here
GMAIL_CLIENT_ID=your_key_here
GMAIL_CLIENT_SECRET=your_key_here
GOOGLE_CALENDAR_ID=your_key_here
TAVILY_API_KEY=your_key_here
```

### 4. Run the app
```bash
streamlit run app.py
```

---

## Project Structure

```
assistant-brain/
├── agents/
│   ├── email_agent.py
│   ├── job_hunter_agent.py
│   ├── research_agent.py
│   ├── planner_agent.py
│   └── briefing_agent.py
├── tools/
│   ├── gmail.py
│   ├── calendar.py
│   ├── search.py
│   └── arxiv.py
├── memory/
│   └── vector_store.py
├── config/
│   └── settings.py
├── tests/
│   └── test_tools.py
├── assets/
│   └── demo.gif
├── app.py
├── main.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

---

## Example Usage

```python
from agents.briefing_agent import MorningBriefingAgent

agent = MorningBriefingAgent()
briefing = agent.run()
print(briefing)

# Output:
# ☀️ Good morning, Asmi!
# 📧 You have 3 urgent emails — 1 from Prof. Zhang (reply drafted)
# 💼 2 new RA openings match your profile — cover letters ready
# 📚 1 new paper on distributed databases — summary saved
# 📅 Today: DSA assignment due 5pm, Meeting at 3pm
```

---

## Roadmap

- [x] Email Agent
- [x] Job Hunter Agent
- [x] Research Agent
- [x] Morning Briefing
- [ ] Finance Tracker Agent
- [ ] Health & Habit Logger
- [ ] WhatsApp/Slack integration
- [ ] Mobile app (React Native)

---

## Contributing

Contributions are welcome! Please read `CONTRIBUTING.md` first.

```bash
# Run tests
pytest tests/

# Lint
flake8 .
```

---

## License

MIT License — see `LICENSE` for details.

---

<div align="center">


⭐ Star this repo if you find it useful!
</div>
