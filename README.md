# Hi, I'm Mehdi Amine 👋

**AI & Data Engineering student @ EMSI (Casablanca)** — I build LLM-based systems: tool-using agents, RAG pipelines and real-time voice agents.

🔎 Looking for a **6-month end-of-studies internship (PFE)** in Generative AI / Data Engineering — on-site or remote, from **March 2027**.

---

## 🛠️ Tech stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat&logo=langgraph&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat&logo=ollama&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat&logo=apachekafka&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Spark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat&logo=apacheairflow&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=flat&logo=minio&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

| Domain | Tools |
|---|---|
| **LLM / Agents** | LangChain, LangGraph, tool calling, RAG, ChromaDB (vector store), Ollama (local LLMs) |
| **Voice AI** | SIP / Janus gateway, aiortc (WebRTC), speech-to-text → LLM → text-to-speech pipeline |
| **Data Engineering** | Kafka, Spark Structured Streaming, Airflow DAGs, MinIO (Medallion: bronze / silver / gold), web scraping (Selenium, Playwright) |
| **Data Science** | scikit-learn pipelines, cross-validation, data cleaning (imputation, outliers, encoding), Plotly |
| **Backend & DB** | FastAPI (SSE streaming), Django, REST APIs, PostgreSQL, SQL / PL/SQL, NoSQL |
| **DevOps** | Docker, Docker Compose, Git, Linux |

---

##  What I've built

###  Tool-using LLM support agent — 
LangChain / LangGraph agent that **reads and updates support tickets in PostgreSQL** through typed tools, exposed via Telegram.
- **Security enforced in code, not in the prompt**: the caller's identity is captured by closure inside each tool, and every SQL query uses bound parameters — a user can never reach another user's data, whatever the prompt says.
- **Two-bot architecture** separating privileged and non-privileged paths, plus **one-time-code (OTP) authentication** persisted in the database.
- Tested against a real PostgreSQL instance (17 test cases, incl. prompt-injection attempts).

###  real-time telephone voice agents — 
Three business agents (**retail, banking, insurance**) sharing one pipeline:
`SIP call → Janus → aiortc (RTP audio) → speech-to-text → LLM agent + tools → text-to-speech → caller`
- **Plug-in contract**: each business agent is a module exposing 5 names, so a new domain plugs in without touching the pipeline.
- **Real-time constraints**: sentence-level chunking of the LLM response (speak while generating), **barge-in** (caller can interrupt the agent), thread-safe audio handling.
- **Latency observability**: RTP frames (20 ms) used as a clock to timestamp turns and break down end-to-end latency (STT finalisation / first LLM token / first TTS sentence).

###  — multi-agent data-science platform — 
Natural-language platform that automates the data lifecycle with **9 specialised agents orchestrated by LangGraph** (shared `AgentState`):
`Router → Collect (upload / 3-level scraping) → Lake (fuzzy-dedup merge) → Explore (quality score) → Clean → Features → Visualise → Advise (RAG) → Export`
- **Cleaning**: adaptive median / KNN imputation, IQR outlier handling, SMOTENC rebalancing; features via scikit-learn `Pipeline`.
- **Model recommendation by RAG** over a **ChromaDB** collection of 43 ML algorithms, validated with 5-fold cross-validation.
- **Local LLM via Ollama** (no cloud dependency, data stays on-premise).
- **FastAPI backend with Server-Sent Events** for real-time streaming, React frontend.
- **75 automated tests** — 100 % passing, 62 % coverage.

### Big Data architecture for media trend analysis — 
End-to-end **batch + streaming** pipeline:
`Scrapers (BBC, Hespress) → Airflow → Kafka → Spark Structured Streaming → MinIO (bronze → silver → gold) → PostgreSQL → Grafana`
- Airflow-orchestrated batch ingestion, Kafka topics for streaming, Medallion architecture on object storage.
- Fully containerised with **Docker Compose**.

###  Vehicle price prediction — *academic project*
ML regression model trained locally and served through a Django web app.

---


🌍 Arabic (native) · French (fluent) · English (advanced)
