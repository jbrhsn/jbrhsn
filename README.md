<div align="center">

# Jabirhusain KP

### Data Engineer — Platform Architecture & Applied AI Delivery

**Enterprise-scale data platforms &nbsp;·&nbsp; Applied autonomous AI systems**

Bangalore, India

[![LinkedIn](https://img.shields.io/badge/LinkedIn-jabirhusain-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/jabirhusain)
[![GitHub](https://img.shields.io/badge/GitHub-jbrhsn-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jbrhsn)
[![Website](https://img.shields.io/badge/Website-jabirhusain.in-111827?style=for-the-badge&logo=googlechrome&logoColor=white)](https://jabirhusain.in)
[![Portfolio](https://img.shields.io/badge/Portfolio-portfolio.jabirhusain.in-111827?style=for-the-badge&logo=googlechrome&logoColor=white)](https://portfolio.jabirhusain.in)

</div>

---

## About

Data Engineer (official title; current specialization: Azure) at IBM, on the Heineken global retail & beverages account since June 2022 — with applied AI systems engineering, built on IBM's Consulting Advantage (ICA) platform, as a differentiating second strength.

Selected outcomes across ~4 years on the account:
- An 80% cut in monitoring-dedicated headcount allocation (1.0 -> 0.2 FTE) across 200+ daily pipelines, from a self-designed Python-based alerting system that eliminated manual tracker-sheet monitoring.
- ~€1,000/month in storage cost savings from a solo-built Z-Ordering/VACUUM optimization initiative, and — as a separate, unlinked, billing-confirmed outcome — a >50% reduction in Databricks compute cost from a job-cluster right-sizing/idle-termination change.
- 50-75 engineering hours/month recaptured, combined, by two internal AI assistants I solo-built (DRS Operations Helper, DRS User Story Generator) — recognized by the client in a town hall — and, separately, 20-30 engineering hours/month recaptured by a third assistant ("Databricks Transform Expert") I later built to accelerate a gold-layer migration.
- That migration itself: 112 legacy notebooks consolidated into 6 SQL-based Delta Live Tables pipelines, delivered solo in 240 hours against a 324-hour internal estimate — cutting the pipeline count from 12 (each running 1-2 hours) to 6 (each now running 45-60 minutes).
- A Microsoft Graph API ingestion consolidation that cut runtime from 6-8 hours to 3 hours, with zero high-priority incidents in the 3 months since deployment (down from 3-4/month).
- A ~50% reduction in Azure platform-monitoring effort (40 -> 20 hours/month) after taking over ownership of the DataOps Observability Platform roughly 6 months into its build.

Outside IBM, I design custom multi-agent frameworks in LangGraph as personal projects (see below) — working through architectural trade-offs around context length, cost boundaries, state machines, and data security, rather than wrapping a single API call.

```text
Jun 2022   ->   Associate System Engineer (graduate hire); ~2.5-month training
                v  program, then allocated to the Heineken account (Aug 2022)
Jun 2023   ->   Promoted to Associate Data Engineer (Heineken account)
                v  DataOps ownership, optimization initiatives, two internal
                   AI assistants built on IBM Consulting Advantage
Jan 2025   ->   Promoted to Data Engineer (Heineken account); specialization: Azure
                v  Platform reliability, gold-layer migration, a third internal
                   AI assistant, and DataOps Observability Platform ownership
```

---

## Featured Projects (self-engineered)

*Personal engineering work, built independently outside of IBM employment - not professional/job experience.*

### Aria - Multi-Agent Discord Bot

[![Repo](https://img.shields.io/badge/GitHub-aria__multi__agent__bot-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jbrhsn/aria_multi_agent_bot)
&nbsp;`LangGraph` &nbsp;`Python` &nbsp;`sqlite-vec` &nbsp;`Docker` &nbsp;`discord.py`

A config-driven fleet of LangGraph agents in a single Discord bot, exposing **5 personal-assistant agents** (Goal, Learning, Health, Finance, Research). *(Single-operator system.)*

- **YAML config-driven engine** - every agent is an instance of one shared `ReActAgent` engine, described declaratively in a YAML file, backed by per-user SQLite (relational) and `sqlite-vec` (semantic vector) storage.
- **Agent loop** - `Decide -> Plan -> Execute <-> Tools -> Evaluate -> Final`, a LangGraph state machine, with tool-call budgets and evaluation-loop caps.
- **Key architecture** - auto-generated typed CRUD tools per table (search/get/list/insert/update/delete) parsed from each agent's schema at startup; multi-tenant isolation (separate SQLite files per user, WAL mode, async per-user write locks); fail-fast Pydantic config; TTL+LRU agent caching; SQLite authorizer blocking DDL; prompt-injection redaction.
- **Tech** - Python 3.12+, LangGraph, discord.py, sqlite-vec, uv, Docker/Docker Compose.
- **Testing** - 248 tests, ~91% coverage, fully offline (mocks requests/OpenAI/ChatOpenAI/TavilyClient); gated by `ruff` lint/format.

### resume_writer (Agentic-CV-Expert) - Council of Experts Resume Orchestrator

[![Repo](https://img.shields.io/badge/GitHub-resume__writer-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jbrhsn/resume_writer)
&nbsp;`LangGraph` &nbsp;`Python` &nbsp;`FastAPI` &nbsp;`Pydantic` &nbsp;`tectonic`

A multi-agent resume generator built on LangGraph. Takes a candidate profile and a job description, and a "council" of four persona agents (CEO, Hiring-Manager, Recruiter, ATS Specialist) plans, writes, and critiques a resume until it clears their score gates. *(Single-operator system.)*

- **Workflow** - three phases: parallel extraction (`analyze_jd` + `parse_profile` -> `gap_analysis`), parallel four-persona council planning joined by a conflict-resolution step into a final plan, and a write-and-refine loop (`initial_write` -> evaluator nodes -> `edit_resume`) capped at 3 cycles.
- **Score gates** - CEO >= 80, Hiring-Manager >= 80, Recruiter >= 85 (defined in `config.py`).
- **Output formats** - Markdown (zero-loss), LaTeX (LLM conversion), PDF (via the `tectonic` engine).
- **Tech** - Python 3.12+, LangGraph, Pydantic structured outputs (7 schemas), OpenRouter for LLM access, FastAPI web UI with SSE live progress.
- **Testing** - 51 passing tests, fully network-free (LLM stubbed via `FakeLLM`).

---

## Enterprise Impact - IBM / Heineken

| Initiative | Outcome |
| --- | --- |
| **Automated Pipeline Alerting** (SAP DI + ADF + Databricks, 200+ daily pipelines) | Eliminated manual tracker-sheet monitoring; cut monitoring-dedicated headcount allocation 80% (1.0 -> 0.2 FTE) |
| **Storage & Compute Optimization** (Z-Ordering/VACUUM across ~40+ systems, ~80 bronze/silver directories; job-cluster right-sizing/idle-termination) | ~&euro;1,000/month in storage cost savings; separately, &gt;50% reduction in Databricks compute cost - both billing-confirmed, unlinked outcomes |
| **Infrastructure Resilience Automation** (failure-aware Logic App retry orchestrator for ADF failures) | Replaced a fully manual re-trigger process; team-estimated 2-3 hours saved per failure occurrence, and ~6-7 hours of SLA-timing improvement |
| **Internal AI Assistants - Associate tier** (DRS Operations Helper + DRS User Story Generator, IBM Consulting Advantage) | 50-75 engineering hours/month recaptured, combined; client formally recognized the team in a town hall |
| **Gold-Layer Migration** (112 legacy notebooks -> 6 SQL-based DLT pipelines, solo) | 240 hours delivered vs. a 324-hour internal estimate; 12 pipelines (1-2 hrs each) consolidated to 6 pipelines (45-60 min each) |
| **Internal AI Assistant - "Databricks Transform Expert"** (IBM Consulting Advantage, solo, built to accelerate the migration above) | 20-30 engineering hours/month recaptured (kept separate from the two Associate-tier assistants above); caught a non-deterministic deduplication bug during migration reconciliation |
| **Microsoft Graph API Ingestion Consolidation** (solo, Azure AD entities) | Runtime cut from 6-8 hours to 3 hours; zero high-priority incidents in the 3 months since deployment (down from 3-4/month) |
| **DataOps Observability Platform** (ownership taken over ~6 months into its build) | ~50% reduction in Azure platform-monitoring effort (40 -> 20 hours/month) |

---

## Working Style

- **Client-facing communication** - presents architecture proposals and analysis directly to the client; 
- **Self-directed upskilling** - independently learned Power BI to deliver a dashboard in the absence of a dedicated BI resource on the team; self-taught prompt engineering and applied AI/RAG fundamentals while building the AI assistants.
- **Architecture governance** - solo-designed solutions (retry orchestrator, cluster right-sizing, currency-ingestion pipeline, Graph API consolidation, Collibra migration, observability-platform work) consistently reviewed and approved by architects/team lead before production.

---

## Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**Data Platform & Engineering**

![Azure Databricks](https://img.shields.io/badge/Azure%20Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Delta Live Tables](https://img.shields.io/badge/Delta%20Live%20Tables-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Unity Catalog](https://img.shields.io/badge/Unity%20Catalog-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Azure Data Factory](https://img.shields.io/badge/Azure%20Data%20Factory-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Azure Logic Apps](https://img.shields.io/badge/Azure%20Logic%20Apps-0066FF?style=flat-square&logo=microsoftazure&logoColor=white)
![Azure Data Lake Storage](https://img.shields.io/badge/Azure%20Data%20Lake%20Storage-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![SAP Data Intelligence](https://img.shields.io/badge/SAP%20Data%20Intelligence-0FAAFF?style=flat-square&logo=sap&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Collibra](https://img.shields.io/badge/Collibra-00A19A?style=flat-square&logoColor=white)
![Microsoft Graph API](https://img.shields.io/badge/Microsoft%20Graph%20API-0078D4?style=flat-square&logo=microsoft&logoColor=white)

**Applied GenAI & AI Infrastructure**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![CrewAI](https://img.shields.io/badge/CrewAI-FF6B6B?style=flat-square&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![sqlite-vec](https://img.shields.io/badge/sqlite--vec-003B57?style=flat-square&logo=sqlite&logoColor=white)
![OpenRouter](https://img.shields.io/badge/OpenRouter-000000?style=flat-square&logo=openai&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![IBM Consulting Advantage](https://img.shields.io/badge/IBM%20Consulting%20Advantage-052FAD?style=flat-square&logo=ibm&logoColor=white)

**Microsoft Fabric & Analytics**

![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-117865?style=flat-square&logo=microsoft&logoColor=white)
![Azure Cost Monitor API](https://img.shields.io/badge/Azure%20Cost%20Monitor%20API-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Azure Log Analytics API](https://img.shields.io/badge/Azure%20Log%20Analytics%20API-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

---

## Certifications

| Credential | Issuer | Status | Valid Until |
| --- | --- | --- | --- |
| **Databricks Certified Data Engineer Professional** | Databricks Academy | Active | 26 Jan 2027 |
| **Databricks Certified Generative AI Engineer Associate** | Databricks Academy | Active | 20 Jul 2028 |
| **Microsoft Certified: Azure AI Engineer Associate** | Microsoft | Active | 29 Jun 2027 |
| **Microsoft Certified: Fabric Analytics Engineer Associate** | Microsoft | Active | 08 Apr 2027 |
| watsonx Orchestrate Practitioner Advanced | IBM | Active | 06 Apr 2027 |
| PCEP-30-02 - Certified Entry-Level Python Programmer | Python Institute | Active | No expiration |
| Microsoft Certified: Azure Data Engineer Associate | Microsoft | **Expired** | 21 Jan 2026 |

---

## Education

| Degree | Institution |
| --- | --- |
| **Master of Computer Applications (MCA)** | Cochin University of Science and Technology (CUSAT), Kochi |
| **BSc in Computer Science** | Sri C Achutha Menon Government College, Thrissur |

---

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-jabirhusain-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/jabirhusain)
[![GitHub](https://img.shields.io/badge/GitHub-jbrhsn-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jbrhsn)
[![Website](https://img.shields.io/badge/Website-jabirhusain.in-111827?style=flat-square&logo=googlechrome&logoColor=white)](https://jabirhusain.in)

</div>
