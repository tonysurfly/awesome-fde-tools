# Research record

Decisions and corrections behind the catalog. Research proceeds in loops: discover candidates, compare neighboring tools, challenge claims, check primary sources, and cut entries that do not add enough.

## 2026-10-02 — external ecosystem catalog review

**Source.** A ~300-entry category-organized catalog of FDE and agent-ecosystem tooling (actuation, browser farms, RAG, LLM gateways, evals, observability, co-browse, field infrastructure, meta lists). Reviewed in full against the inclusion bar in [CONTRIBUTING.md](../CONTRIBUTING.md).

**Method.** Mapped every candidate to the field problems in the README. Kept entries that answer a distinct customer-delivery failure not already covered. Rejected category completeness, popularity, and general developer-stack essentials. Maintainer decision: familiar tools such as LiteLLM, Ollama, and n8n were cut even where a real field framing exists, because they add no discovery value.

### Added (5 entries, 61 → 66)

| Entry | Section | Why it earned the slot |
| --- | --- | --- |
| FDEOps | Carry context across the engagement (new section) | The only FDE-specific agent-skill pack found: 35 task skills plus a coordinator, npm-installable, with local per-customer engagement memory — answers land-to-close continuity, a failure none of the technical sections cover. Maturity evidence is documentation and repo structure only; revisit if maintenance stalls. |
| FastMCP | Build the missing integration | Distinct job from Airbyte Python CDK: exposing an action surface for agents over a customer system that has none, rather than extracting from it. |
| Snyk agent-scan | Prove the customer task works | Security evidence for third-party MCP servers, agent configs, and skills before they touch customer credentials. Complements MCP Inspector (functional protocol testing) with audit. |
| Datasette | Untangle workflows and records | Read-only explorable handoff over a customer extract; serves operations staff where qsv and VisiData serve the analyst. |
| marimo | Untangle workflows and records | Rerunnable, git-diffable discovery analysis. Jupyter stays excluded as general dev stack; marimo's mechanism (reactive execution, plain-Python storage) is the field-relevant difference. |

### Field references added (3)

- [global-fde/awesome-fde-resources](https://github.com/global-fde/awesome-fde-resources) — sibling list, broader mandate.
- [humanlayer/12-factor-agents](https://github.com/humanlayer/12-factor-agents) — production-agent principles.
- [NirDiamant/agents-towards-production](https://github.com/NirDiamant/agents-towards-production) — delivery patterns with code.

### Considered and cut

| Candidate | Decision | Reason |
| --- | --- | --- |
| LiteLLM | Cut | Customer-controlled model gateway is a real constraint, but the tool is now the default answer; no discovery value. |
| Ollama | Cut | Air-gapped demos are a real scenario; the tool is too well known for this list's bar. |
| n8n | Cut | Handoff-to-ops framing qualified under "familiar tools can qualify," but maintainer judged it popularity territory. |
| mcp-chrome | Cut | Strongest browser-actuation candidate (employee's logged-in session, no credential export), but the list deliberately has no browser-automation section; opening that door invites the farm and hype entries. |
| NeMo Guardrails / Guardrails AI / LLM Guard / Lakera | Cut | Runtime guardrails are a real job, but the current problem set ends at cutover evidence. Revisit if an operate-phase section ever opens. |
| E2B / Daytona | Cut | Agent code-execution sandboxes; relevant only when the shipped agent runs code, too narrow for current scope. |
| Webfuse | Cut | Maintainer's product. The footer already discloses the affiliation; listing it as an entry would read as self-promotion and undercut the curation bar. |
| Bruno | Cut | Git-native API collections are useful handoff artifacts, but mitmproxy, WireMock, and Mountebank cover the harder failures; convenience alone is below the bar. |
| DuckDB / Evidence | Cut | Laptop-scale analytics covered by qsv, VisiData, and Steampipe; BI reporting is not a listed failure. |
| Tailscale / ngrok / Cloudflare Tunnel | Cut | Well known; OpenZiti and Pomerium already cover the harder private-access failures. |

### Rejected by category

- **Generic collaboration and productivity** (Notion, Obsidian, Linear, Jira, Asana, Miro, Excalidraw, tldraw, Figma, Loom, Fireflies, Otter, Grain, Gong): not FDE-specific.
- **Product analytics and digital adoption platforms** (PostHog, Amplitude, Mixpanel, Heap, FullStory, Hotjar, Pendo, Whatfix, WalkMe, Appcues, Userpilot, Chameleon, Gainsight): vendor purchases, not field tools.
- **Voice agent platforms** (Retell AI, Vapi): product surface, out of scope.
- **iPaaS and unified APIs** (Zapier MCP, Pipedream, Workato, Make, Tray, MuleSoft, Merge, Paragon, Apideck, Codat, Composio, Arcade, MintMCP, Activepieces): platform purchases; Nango covers the per-customer OAuth failure code-first.
- **MCP plumbing and registries** (official SDKs, reference servers, protocol docs, mcp.so, Smithery, Glama, awesome-mcp-servers, MCP for Beginners): plumbing, curriculum, and unvetted discovery surfaces.
- **Browser farms and agent browsers** (Browserbase, Stagehand, Browser Use, Steel, Hyperbrowser, Scrapybara, Skyvern, Kernel, AgentQL, Scrapeless, Bright Data, Browserless, Chrome DevTools MCP, Vercel agent-browser, Playwright, Puppeteer, Selenium, Cypress, Crawlee): infrastructure purchases or well-known test tooling; no distinct customer failure versus existing entries.
- **Scraping and search APIs** (Firecrawl, Crawl4AI, Tavily, SerpAPI): RAG ingestion plumbing.
- **RAG and vector stack** (LangChain, LlamaIndex, Haystack, GraphRAG, txtai, all vector databases, embedding and reranker providers, Mem0): category dump; parsing needs already covered by Docling, pdfplumber, docTR, PaddleOCR, OCRmyPDF, and DocETL.
- **Additional parsers** (Unstructured, LlamaParse, Marker, MinerU, MarkItDown, PyMuPDF): redundant with the parsing entries above.
- **Agent frameworks** (CrewAI, AutoGen, Semantic Kernel, PydanticAI, Google ADK, OpenAI Agents SDK, Mastra, Dify, Langflow, Flowise, DSPy, Instructor, smolagents, mcp-agent): LangGraph covers the checkpoint/interrupt failure; more frameworks would be a popularity contest.
- **Extra orchestration** (Inngest, Prefect, Airflow, Dagster): covered by Temporal, Restate, DBOS, Windmill, and Hatchet.
- **Developer tools** (Open Interpreter, Aider, Continue, Cursor, Warp, GPT Researcher): general dev stack, excluded by rule.
- **LLM gateways and providers** (Portkey, Helicone, OpenRouter, Together, Fireworks, Groq, Kong, TrueFoundry, and all model platforms): purchasing decisions, not field failures.
- **Additional eval platforms** (Ragas, TruLens, Braintrust, LangSmith, Opik, HoneyHive, Galileo, Weave, Evidently, MLflow, LangWatch, Giskard, Deepchecks, Patronus, OpenAI Evals, lm-evaluation-harness): jobs covered by promptfoo, Inspect AI, DeepEval, Langfuse, and Phoenix.
- **General observability** (OpenTelemetry, OpenLLMetry, Grafana, Prometheus, Jaeger, SigNoz, Datadog, New Relic, Sentry, Honeycomb, Elastic, Highlight): general stack essentials.
- **Co-browse and remote support** (Surfly, Glance, Cobrowse.io, LivePerson CoBrowse, ScreenMeet, TeamViewer, AnyDesk, Librestream, Intercom, Zendesk): contact-center purchases.
- **Field infrastructure** (Docker, Podman, Kubernetes, Helm, Kustomize, Argo CD, Flux, Terraform, OpenTofu, Pulumi, Ansible, Crossplane, cloud CLIs, Vault, Infisical, Doppler, SOPS, External Secrets Operator, Sealed Secrets, password-manager CLIs, direnv, mise, asdf, Nix): general developer-stack essentials, explicitly out of scope.
- **Local LLM serving** (Ollama, vLLM, SGLang, llama.cpp, LM Studio, Jan, LocalAI, llamafile, Open WebUI, AnythingLLM, Text Generation Inference): model-serving choices, not listed failures.
- **Data stack and BI** (DuckDB, Polars, pandas, dbt, Airbyte platform, Fivetran, Meltano, Hightouch, Segment, RudderStack, ClickHouse, MotherDuck, Databricks, BigQuery, Metabase, Superset, Lightdash, Redash): field versions covered by qsv, VisiData, Steampipe, Recce, and SQLMesh.
- **API debugging utilities** (Postman, Hoppscotch, HTTPie, curl, httpbin, Webhook.site): obvious; mitmproxy, WireMock, and Mountebank cover the real failures.
- **FDE hiring and curriculum material** (libaice/Awesome-FDE, pierpaolo28/Awesome-FDE-Roadmap, YagyanshB google-fde-interview-guide, jiji262/fde-guide, FDE Academy article): interview preparation, off-mission.
- **CN-language practice material** (fdetoolkit, xdash FDE Guidance Book): genuine practice content; language barrier for this list's audience.
- **Vendor-tied skills** (databricks-agent-skills): platform-specific.
- **Adjacent awesome lists**: kept to one (agents-towards-production); awesome-harness-engineering, Awesome-Context-Engineering, and ai-engineering-field-guide cut to avoid list-ception. sindresorhus/awesome is meta-meta.

### Open follow-ups

- `docs/delivery-recipes.md` and `docs/engagement-brief.md` are linked from the README but do not exist yet.
- `tools/validate.py` and `tools/preview_readme.py` are referenced in CONTRIBUTING.md but do not exist yet; the `research/github-checks.json` refresh workflow has no tooling behind it.
