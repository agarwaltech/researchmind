# 🔬 ResearchMind — Multi-Agent AI Research System

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Mistral AI](https://img.shields.io/badge/Mistral_AI-F7572B?style=flat-square&logo=mistral&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

Give it a topic — **ResearchMind** searches the web, scrapes the most relevant source, drafts a structured research report, and critiques its own output. Four specialized components run as a sequential pipeline inside a polished Streamlit UI.

---

## 🤖 The 4-Stage Pipeline

```
Topic → Search Agent → Reader Agent → Writer Chain → Critic Chain → Report + Feedback
```

| Stage | Role | How it's built |
|---|---|---|
| 🔍 **Search Agent** | Finds recent, reliable sources | LangChain `create_agent` + Tavily Search tool |
| 📄 **Reader Agent** | Picks the best URL and scrapes deep content | LangChain `create_agent` + BeautifulSoup scraper tool |
| ✍️ **Writer Chain** | Drafts a structured report (intro, key findings, conclusion, sources) | LCEL chain: `prompt \| llm \| StrOutputParser` |
| 🧐 **Critic Chain** | Scores the report 0–10 with strengths and improvement points | LCEL chain: `prompt \| llm \| StrOutputParser` |

The pipeline (`pipeline.py`) runs the stages sequentially, passing a shared `state` dictionary from one stage to the next.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Streamlit + custom CSS (dark theme) |
| **LLM** | Mistral AI — `mistral-small-2506` via `langchain-mistralai` |
| **Agents** | LangChain `create_agent` (tool-calling) |
| **Chains** | LangChain Core / LCEL (`prompt → llm → parser`) |
| **Web search** | Tavily Search API (top-5 results) |
| **Scraping** | Requests + BeautifulSoup4 (strips `script/style/nav/footer`, ~3k chars) |

> **Note:** orchestration is a hand-written sequential pipeline — there is **no LangGraph** in the codebase.

---

## ✨ App Features (Streamlit UI)

- Custom-CSS dark theme with a hero header and example topic chips.
- Live pipeline **status cards** (Waiting → Running → Done) driven by `session_state`.
- Expandable raw outputs for the Search and Reader stages.
- Final report rendered as native markdown, with a **one-click `.md` download**.
- A Critic feedback panel showing the score and verdict.

---

## 🚀 Run Locally

**Prerequisites:** Python 3.10+, a [Tavily API key](https://app.tavily.com), and a [Mistral API key](https://console.mistral.ai).

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Create a .env file in the project root
TAVILY_API_KEY=tvly-your-key-here
MISTRAL_API_KEY=your-mistral-key-here

# 3a. Run the Streamlit app
streamlit run app.py        # → http://localhost:8501

# 3b. …or run the pipeline from the terminal
python pipeline.py
```

---

## 📁 Project Structure

```
researchmind/
├── app.py            # Streamlit UI — pipeline visualization & results
├── pipeline.py       # Sequential 4-stage orchestrator (+ CLI entry point)
├── agents.py         # Agent builders + writer chain + critic chain + LLM setup
├── tools.py          # web_search (Tavily) and scrape_url (Requests + BS4) tools
├── requirements.txt
└── .env              # TAVILY_API_KEY, MISTRAL_API_KEY (not committed)
```

---

## 💡 Example Topics

`LLM agents and multi-agent systems 2025` · `CRISPR gene editing breakthroughs` · `Fusion energy progress` · `Quantum computing in 2025`

---

## 📄 License

MIT
