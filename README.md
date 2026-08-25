# Sabit Shaiholla

**AI/LLM Engineer · Forward Deployed Engineer**

Almaty, Kazakhstan · [sabit-shaiholla.github.io](https://sabit-shaiholla.github.io) · [LinkedIn](https://www.linkedin.com/in/sabit-shaiholla/) · [saba.shaiholla@gmail.com](mailto:saba.shaiholla@gmail.com)

On the work side I've built enterprise RAG over internal knowledge: 100+ code repositories, 1000+ Confluence pages and 5000+ internal documents, most of it scanned PDFs and badly formatted DOCX where top-k retrieval breaks down. The pipeline runs an automated RAGAS evaluation loop (faithfulness 0.89, answer relevance 0.92 on a 15K-query benchmark), and for the messy-document part I use agents that decide what to read themselves instead of trusting nearest-neighbour search.

On the serving side: deployed Kimi-K2.6 on-premise with SGLang (MoE, 100+ tokens/sec throughput, 52% lower TTFT than baseline) and GPT-OSS 120B with vLLM. Also built a marketplace for AI agent skills on APM (Agent Package Manager) — skills as installable packages with versions and dependency resolution, instead of being copied between projects by hand.

Background: Spring Boot microservices, event-driven backends, edge/IoT systems, plus a stretch leading a team of 10 on platforms with 3M+ MAU. A lot of my work is customer-facing — working out what they actually need before anything gets built.

Code here, reasoning on [my site](https://sabit-shaiholla.github.io/portfolio/).

---

## Currently

- Agentic document search on Google ADK + Gemini 3 Flash: the agent navigates files with tools instead of an embedding index.
- Evaluation in the loop: OpenEvals graders as agent reflection steps, groundedness scoring, self-correcting retrieval. Posts on both below.

---

## Selected work

### [Agentic File Query](https://github.com/sabit-shaiholla/agentic-file-query) · [write-up](https://sabit-shaiholla.github.io/portfolio/agentic-file-query/)

An agent that explores a document folder itself rather than trusting nearest-neighbour search on pre-embedded chunks. It runs a Scan → Deep Dive → Backtrack loop over nine filesystem and vector tools (`scan_folder`, `grep_search`, `semantic_search`, `parse_file`, …), so it can follow references and retry when retrieval misses something.

`Google ADK` · `Gemini 3 Flash` · `Docling` · `pgvector` / `DuckDB` · `FastAPI`

### [Corrective RAG + OpenEvals](https://github.com/sabit-shaiholla/corrective-rag-openevals) · [write-up](https://sabit-shaiholla.github.io/portfolio/corrective-rag-openevals/)

RAG pipeline that grades every retrieved document for relevance before using it. The score routes the agent into Correct / Incorrect / Ambiguous branches, falling back to web search if nothing passes the threshold. OpenEvals graders run inside the agent loop as reflection steps, not just offline tests.

`LangGraph` · `Gemini 2.5 Flash` · `Ollama` (Qwen 2.5 7B) · `OpenEvals` · `Tavily`

### [Gemini File Search Tool](https://github.com/sabit-shaiholla/gemini-api-file-search-tool) · [live demo](https://filequerysystem.duckdns.org/) · [write-up](https://sabit-shaiholla.github.io/portfolio/gemini-api-file-search-tool/)

Managed RAG end to end: upload a PDF, get answers with grounding metadata pointing at source chunks. Runs on an Oracle Cloud always-free instance behind Nginx + Let's Encrypt, with CI pushing releases. Setup documented [step by step](https://sabit-shaiholla.github.io/portfolio/oracle-cloud-setup-gemini-tool/).

`Gemini File Search API` · `Streamlit` · `Nginx` · `GitHub Actions`

### Agent Skill Marketplace, on APM

Marketplace for AI agent skills built on APM (Agent Package Manager): skills as packages you can install, with versions and dependency resolution. Not public, no repo to link.

`Agent Package Manager` · `Python`

### [Premier League Match Prediction](https://github.com/sabit-shaiholla/pl-football)

Selenium scraper that gets past FBREF's 403s, 584 engineered features across 17 statistical categories, six seasons of matches. Reaches 61.2% test accuracy on three-way Win/Draw/Loss against a 33.3% baseline. The scraper broke after OPTA removed the advanced tables in Jan 2026, but the datasets are in the repo, so the modelling still runs.

`Python` · `scikit-learn` · `Selenium` · `pandas`

<details>
<summary><b>More</b></summary>

| Project | What it is | Stack |
|---|---|---|
| [iot-edge-latency](https://github.com/sabit-shaiholla/iot-edge-latency) | Measures latency and QoS trade-offs across Raspberry Pi, EC2, local VM, and AWS Greengrass nodes using Aruco-marker video as ground truth | Python, OpenCV, AWS Greengrass, MQTT |
| [ecommerce-microservices](https://github.com/sabit-shaiholla/ecommerce-microservices) | Event-driven e-commerce platform: service discovery, distributed tracing, Keycloak auth | Spring Boot, Kafka, Eureka, Zipkin, Keycloak |
| [football-oracle](https://github.com/sabit-shaiholla/football-oracle) | AI-driven player analytics with JWT auth, generated reports, and SonarQube in CI | Spring Boot, React, PostgreSQL, Vertex AI |
| [ai-llm-tutorials](https://github.com/sabit-shaiholla/ai-llm-tutorials) | Hands-on notebooks working through LLM mechanics and RAG patterns | Python, Jupyter |

</details>

---

## Writing

<!-- BLOG-POST-LIST:START -->
- **[Beyond RAG: Building an AI Agent That Explores Documents Like a Human Researcher](https://sabit-shaiholla.github.io/portfolio/agentic-file-query/)** <sub>Feb 2026</sub>
- **[How I Setup Oracle Cloud Always Free Instance for Gemini API File Search Tool](https://sabit-shaiholla.github.io/portfolio/oracle-cloud-setup-gemini-tool/)** <sub>Nov 2025</sub>
- **[Revolutionizing RAG: Why Gemini File Search Tool is the great RAG-as-a-Service](https://sabit-shaiholla.github.io/portfolio/gemini-api-file-search-tool/)** <sub>Nov 2025</sub>
- **[Enhancing LLM Agent Reliability with Corrective RAG and OpenEvals](https://sabit-shaiholla.github.io/portfolio/corrective-rag-openevals/)** <sub>May 2025</sub>
<!-- BLOG-POST-LIST:END -->

→ [All posts](https://sabit-shaiholla.github.io/portfolio/) · [TIL notes](https://sabit-shaiholla.github.io/til/) · [RSS](https://sabit-shaiholla.github.io/index.xml)

---

## Stack

| | |
|---|---|
| **Languages** | Python · Java · Go |
| **AI / LLM** | Google ADK · LangChain · LangGraph · Pydantic-AI · PyTorch · Vertex AI · SageMaker · Gemini API |
| **Model serving** | vLLM · SGLang · self-hosted inference (embeddings → 120B) |
| **LLM Ops** | OpenEvals · LangSmith · Langfuse · MLflow · Kubeflow |
| **Backend** | Spring Boot · Quarkus · FastAPI · gRPC · GraphQL |
| **Data & Messaging** | Kafka · RabbitMQ · Spark · PostgreSQL · pgvector · DuckDB · Elasticsearch |
| **Platform** | Docker · Kubernetes · AWS · GCP · Azure · Oracle Cloud · GitHub Actions · Grafana |

---

<sub>Open to AI/LLM and forward-deployed engineering roles. Email is fastest: [saba.shaiholla@gmail.com](mailto:saba.shaiholla@gmail.com).</sub>
