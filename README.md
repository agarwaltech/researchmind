# 🔬 ResearchMind — Multi-Agent AI Research System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)
![MistralAI](https://img.shields.io/badge/Mistral_AI-F7572B?style=for-the-badge&logo=mistral&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-0A0A0F?style=for-the-badge&logoColor=white)

**Four specialized AI agents collaborate to deliver a polished research report on any topic.**

🚀 **[Live Demo → researchmind-f7q3fb2rjlwrx3webzdcwl.streamlit.app](https://researchmind-f7q3fb2rjlwrx3webzdcwl.streamlit.app)**

</div>

---

## ✨ What is ResearchMind?

ResearchMind is a **fully autonomous multi-agent research pipeline** built with LangChain, LangGraph, and Mistral AI. You give it a topic — it searches the web, scrapes deep content, writes a structured report, and even critiques its own output. All inside a sleek Streamlit UI.

No manual searching. No copy-pasting. Just results.

---

## 🤖 The 4-Agent Pipeline

```
User Input (Topic)
      │
      ▼
┌─────────────────┐
│  Search Agent   │  ← Tavily API: finds recent, reliable sources
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Reader Agent   │  ← Scrapes the most relevant URL for deep content
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Writer Chain   │  ← Drafts a structured research report
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Critic Chain   │  ← Reviews, scores, and gives improvement feedback
└─────────────────┘
         │
         ▼
  📄 Final Report + 🧐 Critic Feedback
```

| Agent | Role | Tool Used |
|---|---|---|
| 🔍 **Search Agent** | Finds recent web information on the topic | Tavily Search API |
| 📄 **Reader Agent** | Scrapes the most relevant URL for deeper content | BeautifulSoup |
| ✍️ **Writer Chain** | Drafts a structured, professional research report | Mistral AI LLM |
| 🧐 **Critic Chain** | Scores the report and gives honest feedback | Mistral AI LLM |

---

## 🖥️ UI Preview

> **Dark-themed, minimal, and professional** — built with custom CSS inside Streamlit.

- Real-time pipeline status cards (Waiting → Running → Done)
- Expandable raw agent outputs
- Rendered markdown research report
- One-click `.md` report download
- Critic feedback panel with score

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Streamlit + Custom CSS |
| **LLM** | Mistral AI (`mistral-small-2506`) |
| **Agent Framework** | LangGraph (`create_react_agent`) |
| **Chains** | LangChain Core (Prompt → LLM → Parser) |
| **Web Search** | Tavily API |
| **Scraping** | Requests + BeautifulSoup4 |
| **Deployment** | Streamlit Community Cloud |

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/agarwaltech/researchmind.git
cd researchmind
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Set up environment variables

Create a `.env` file in the root directory:

```env
TAVILY_API_KEY=tvly-your-key-here
MISTRAL_API_KEY=your-mistral-key-here
```

Get your keys here:
- Tavily: [app.tavily.com](https://app.tavily.com)
- Mistral: [console.mistral.ai](https://console.mistral.ai)

### 4. Run the app

```bash
streamlit run app.py
```

Open [http://localhost:8501](http://localhost:8501) in your browser.

---

## 📁 Project Structure

```
researchmind/
│
├── app.py              # Streamlit UI — pipeline visualization & results display
├── agents.py           # Agent builders, writer chain, critic chain
├── tools.py            # web_search (Tavily) and scrape_url (BS4) tools
├── requirements.txt    # All Python dependencies
└── .env                # API keys (local only — never commit this!)
```

---

## 📦 Requirements

```txt
streamlit
langchain
langchain-core
langchain-mistralai
langgraph
tavily-python
requests
beautifulsoup4
python-dotenv
rich
```

---

## ☁️ Deploy Your Own

1. Fork this repository
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Connect your GitHub repo
4. Add secrets in **Settings → Secrets**:

```toml
TAVILY_API_KEY = "tvly-xxxxxxxxxxxx"
MISTRAL_API_KEY = "xxxxxxxxxxxx"
```

5. Click **Deploy** — your app is live!

---

## 💡 Example Topics to Try

- `LLM agents and multi-agent systems 2025`
- `CRISPR gene editing latest breakthroughs`
- `Fusion energy progress and milestones`
- `Quantum computing breakthroughs in 2025`
- `Climate tech innovations 2025`

---

## 🗺️ Roadmap

- [ ] Add memory across research sessions
- [ ] Support multiple URLs in the Reader Agent
- [ ] Export report as PDF
- [ ] Add a chat interface to ask follow-up questions on the report
- [ ] Let users choose between different LLM providers

---

## 👨‍💻 Author

**Anshul Agarwal**
- GitHub: [@agarwaltech](https://github.com/agarwaltech)
- Live App: [researchmind-f7q3fb2rjlwrx3webzdcwl.streamlit.app](https://researchmind-f7q3fb2rjlwrx3webzdcwl.streamlit.app)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">

**Built with LangChain · LangGraph · Mistral AI · Streamlit**

⭐ Star this repo if you found it useful!

</div>
