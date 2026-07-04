<div align="center">

# Jabirhusain KP

### Data &amp; AI Engineer

**Enterprise-scale data platforms &nbsp;·&nbsp; Applied autonomous AI systems**

Bengaluru, India &nbsp;·&nbsp; Open to remote-first, Bengaluru hybrid, and Kochi hybrid roles

[![LinkedIn](https://img.shields.io/badge/LinkedIn-jabirhusain-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/jabirhusain)
[![GitHub](https://img.shields.io/badge/GitHub-jbrhsn-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jbrhsn)
[![Website](https://img.shields.io/badge/Website-jabirhusain.in-111827?style=for-the-badge&logo=googlechrome&logoColor=white)](https://jabirhusain.in)

</div>

---

## About

Engineer operating at the convergence of enterprise-scale data platforms and applied autonomous AI systems. 4+ years at IBM on the Heineken global retail &amp; beverages engagement, fast-tracked from Graduate Data Engineer to Data Engineer in under four years via two merit promotions.

I work across the full depth of the stack &mdash; from low-level Delta Lake file-layout tuning on a ~6 PB lakehouse to high-level multi-agent GenAI architecture with LangGraph. Rather than wrapping APIs, I design custom self-engineered systems and reason through the trade-offs around context length, cost boundaries, state machines, and data security.

Beyond individual contribution, I act as an architectural decision-maker and standards driver on the account &mdash; owning code reviews as a quality gatekeeper, coordinating cross-functional stakeholder alignment, and championing tooling adopted beyond original team scope. Cost-consciousness is a design discipline: every significant project ships with a measurable FinOps outcome attached.

```text
Jun 2022   ->   Joined IBM as Graduate Data Engineer
                v  [merit fast-track + rapid upskilling]
Jun 2023   ->   Promoted to Associate Data Engineer
                v  [senior-level responsibilities]
Jan 2025   ->   Data Engineer (Heineken Account)
                v  DataOps observability, advanced FinOps, code-review
                   ownership, architectural decisions, production
                   enterprise GenAI + Data tooling.
```

---

## Featured Projects (self-engineered)

### Aria &mdash; Config-Driven Multi-Agent AI Platform

[![Repo](https://img.shields.io/badge/GitHub-aria__multi__agent__bot-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jbrhsn/aria_multi_agent_bot)
&nbsp;`LangGraph` &nbsp;`Python` &nbsp;`sqlite-vec` &nbsp;`Docker` &nbsp;`discord.py`

A self-engineered production-grade AI platform running **5 specialized autonomous agents** (Goal, Learning, Research, Health, Finance) through a single Discord bot. *(Single-operator system &mdash; production-grade engineering, not production traffic or scale.)*

- **YAML config-driven engine** &mdash; every agent is an instance of one shared `ReActAgent`, described declaratively; runtime-injected prompts and tools minimize context bloat, drop token overhead, and neutralize hallucinations. Adding a new agent is mostly writing a YAML file.
- **Auto-generated typed CRUD** &mdash; a generator parses each agent's `CREATE TABLE` schema at startup and emits six typed tools per table, so the data model *is* the tool surface.
- **ReAct state graph** &mdash; `Decide -> Plan -> Execute <-> Tools -> Evaluate -> Final`, a synchronous LangGraph run made concurrent per user via `asyncio.to_thread` and per-user async locks, with a self-evaluation node scoring output across five vectors (feasibility, completeness, accuracy, safety, clarity) under explicit tool-call budgets and evaluation-loop caps.
- **Hybrid memory** &mdash; `sqlite-vec` (`vec0`) for relational + semantic storage with KNN retrieval, a self-optimization pass (near-dup detection, Union-Find clustering, LLM merge), and a self-growing cross-agent knowledge base.
- **Multi-tenant isolation &amp; safe concurrency** &mdash; per-user relational and vector DBs, WAL mode, fail-fast Pydantic config, SQLite authorizer, prompt-injection redaction.
- **Delivery** &mdash; installable `aria` package, multi-stage Docker build + `docker-compose` (non-root), verified by a fully offline suite of **248 tests at ~91% coverage**, `ruff`-gated on every change.

### resume_writer (Agentic-CV-Expert) &mdash; Agentic Resume Orchestrator

`LangGraph` &nbsp;`Python` &nbsp;`FastAPI` &nbsp;`Pydantic` &nbsp;`tectonic`

A self-engineered LangGraph orchestration system that simulates a hiring committee across four adversarial personas &mdash; CEO, Senior Hiring Manager, Recruiter, and ATS Specialist &mdash; producing job-tailored resumes through recursive multi-perspective critique. *(Single-operator project &mdash; production-grade engineering.)*

- **14-node graph** &mdash; parallel extraction (`analyze_jd` + `parse_profile` -> `gap_analysis`), parallel four-persona planning joined by a `plan_conflict_resolution` mediator feeding a `final_plan` blueprint, and a score-gated self-correction loop (CEO &gt;= 80, Senior &gt;= 80, Recruiter &gt;= 85) capped at 3 editing cycles.
- **Per-task model routing** &mdash; five task classes (analysis, planning, writing, evaluation, LaTeX export), each independently retargetable via `RW_*_MODEL` over OpenRouter.
- **Structured output contract** &mdash; seven Pydantic-typed schemas via `.with_structured_output()`, eliminating regex post-processing.
- **Multi-format export &amp; web UI** &mdash; Markdown -> LaTeX -> PDF (compiled by `tectonic`, degrading gracefully), plus a FastAPI single-page UI streaming live per-node progress over Server-Sent Events.
- **Reliability &amp; testability** &mdash; `safe_invoke` with exponential backoff, dependency-injected `NodeDeps`, verified by a fully network-free suite of **51 tests** (LLM stubbed via `FakeLLM`). Self-reported at 60-120s per full loop with sub-1% hallucination rate *(not third-party audited)*.

---

## Enterprise Impact &mdash; IBM / Heineken

| Initiative | Outcome |
| --- | --- |
| **DataOps Observability Platform** (built from scratch, 200+ pipelines) | 80% cut in daily manual monitoring (1.0 FTE -> 0.2 FTE); adopted as the account-wide standard |
| **FinOps &amp; Performance Tuning** (Job Compute migration, Z-Ordering) | ~50% compute cost reduction · ~30% storage reduction · &euro;1,000+/month recurring savings |
| **Infrastructure Resilience Automation** (Logic App retry orchestrator) | Eliminated a major class of transient-failure tickets; preserved downstream SLAs |
| **Enterprise AI Assistants** (3 domain-specialized tools on IBM ICA) | 50-60 engineering hours/month recaptured; scaled org-wide by the IBM Data Service Line |
| **Multi-Billion Record Recovery** (200M-2B row tables) | 70% compute savings &amp; 30% effort savings vs. a full rerun; SLA timelines preserved |

---

## Leadership &amp; Governance (IC-level)

- **Enterprise data governance** &mdash; function-backed Row-Level Security (RLS) views over Silver Delta tables; driving migration toward Attribute-Based Access Control (ABAC) in Databricks Unity Catalog.
- **Engineering governance** &mdash; code-quality gatekeeper owning PySpark and SQL code reviews; coordinates CI/CD rollouts via Azure DevOps Pipelines.
- **Architectural decision-making** &mdash; Unity Catalog adoption strategy, compute-tier selection, and data-layout standards on the client engagement.
- **Standards adoption &amp; mentorship** &mdash; formalized observability and AI-tooling standards beyond team scope; mentors junior engineers on lakehouse internals and optimization patterns.

---

## Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**Data Platform &amp; Engineering**

![Azure Databricks](https://img.shields.io/badge/Azure%20Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD4?style=flat-square&logo=delta&logoColor=white)
![Unity Catalog](https://img.shields.io/badge/Unity%20Catalog-FF3621?style=flat-square&logo=databricks&logoColor=white)
![Azure Data Factory](https://img.shields.io/badge/Azure%20Data%20Factory-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![SAP Data Intelligence](https://img.shields.io/badge/SAP%20Data%20Intelligence-0FAAFF?style=flat-square&logo=sap&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Azure DevOps](https://img.shields.io/badge/Azure%20DevOps-0078D7?style=flat-square&logo=azuredevops&logoColor=white)

**Applied GenAI &amp; AI Infrastructure**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![sqlite-vec](https://img.shields.io/badge/sqlite--vec-003B57?style=flat-square&logo=sqlite&logoColor=white)
![OpenRouter](https://img.shields.io/badge/OpenRouter-000000?style=flat-square&logo=openai&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)

**Microsoft Fabric &amp; Analytics**

![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-117865?style=flat-square&logo=microsoft&logoColor=white)
![Azure Monitor](https://img.shields.io/badge/Azure%20Monitor-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

---

## Certifications

| Credential | Issuer | Status | Valid Until |
| --- | --- | --- | --- |
| **Databricks Certified Data Engineer Professional** | Databricks | Active | Jan 2027 |
| **Microsoft Certified: Azure AI Engineer Associate** | Microsoft | Active | Jun 2027 |
| **Microsoft Certified: Fabric Analytics Engineer Associate** | Microsoft | Active | Apr 2027 |
| Microsoft Certified: Azure Data Engineer Associate (DP-203) | Microsoft | Retired | Jan 2026 |

---

## Education

| Degree | Institution | Timeline |
| --- | --- | --- |
| **Master of Computer Applications (MCA)** | Cochin University of Science and Technology (CUSAT), Kochi | 2020 &ndash; 2022 |
| **BSc in Computer Science** | Sri C Achutha Menon Government College, Thrissur | 2015 &ndash; 2018 |

---

<div align="center">

*Targeting Senior Data Engineer · Data Platform Engineer · AI Infrastructure Engineer · AI Engineer (IC track)*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-jabirhusain-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/jabirhusain)
[![GitHub](https://img.shields.io/badge/GitHub-jbrhsn-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jbrhsn)
[![Website](https://img.shields.io/badge/Website-jabirhusain.in-111827?style=flat-square&logo=googlechrome&logoColor=white)](https://jabirhusain.in)

</div>
