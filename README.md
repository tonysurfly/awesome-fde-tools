<p align="center">
  <img src="assets/hero.svg" alt="awesome-fde-tools: a mountain above the wordmark, with fde highlighted in violet." width="800">
</p>

<p align="center">
  <strong>Tools for the hard parts of forward deployed engineering.</strong><br>
  Customer-specific integrations, imperfect data, real permissions, and a result someone else can operate.
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="#contents"><img src="https://img.shields.io/badge/tools-66-8b65a5?style=flat-square" alt="66 curated tools"></a>
  <a href="#contents"><img src="https://img.shields.io/badge/field_problems-9-5b7285?style=flat-square" alt="9 field problems"></a>
  <a href="research/README.md"><img src="https://img.shields.io/badge/curated-2026--10--02-687b5b?style=flat-square" alt="Curated October 2, 2026"></a>
  <a href="CONTRIBUTING.md"><img src="https://img.shields.io/badge/PRs-welcome-8b65a5?style=flat-square" alt="Contributions welcome"></a>
</p>

A forward deployed engineer works beside the customer to turn an actual business workflow into working software. The awkward parts matter: two systems disagree about a record, consent expires halfway through a sync, or a retried write creates a second transaction.

This collection focuses on those problems. A tool earns its place through a specific field use and a meaningful difference from its neighbors. Familiar tools can qualify; popularity alone cannot. General developer-stack essentials are outside the scope.

## Contents

- [Carry context across the engagement](#carry-context-across-the-engagement) <sub>1 tool</sub>
- [Untangle workflows and records](#untangle-workflows-and-records) <sub>9 tools</sub>
- [Build the missing integration](#build-the-missing-integration) <sub>8 tools</sub>
- [Preserve access across systems](#preserve-access-across-systems) <sub>7 tools</sub>
- [Review data changes before cutover](#review-data-changes-before-cutover) <sub>9 tools</sub>
- [Reproduce hostile dependencies](#reproduce-hostile-dependencies) <sub>10 tools</sub>
- [Extract difficult customer inputs](#extract-difficult-customer-inputs) <sub>7 tools</sub>
- [Survive retries and human approvals](#survive-retries-and-human-approvals) <sub>6 tools</sub>
- [Prove the customer task works](#prove-the-customer-task-works) <sub>9 tools</sub>

Start with the failure you need to reproduce or the evidence you need to leave behind. These are alternatives to evaluate, not a stack to install in full.

## <img src="assets/icons/archive.svg" width="30" height="22" alt="">Carry context across the engagement

Keep discovery decisions, evidence, and agent behavior available at cutover and to the next engineer.

- <a href="https://github.com/suboss87"><img src="https://github.com/suboss87.png?size=48" width="20" height="20" alt="" title="suboss87 on GitHub"></a> **[FDEOps](https://github.com/suboss87/FDEOps)** `agent engagement skills`<br>
  Install task skills and a coordinator that give an AI coding agent an engagement workflow — discover, build, hand off — with a local per-customer memory so decisions and evidence survive between sessions.<br>
  <sub>Field note: Skills are instructions an agent executes. Review them before pointing them at customer material, and check data-handling rules: the local memory store holds customer context.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/clipboard-list.svg" width="30" height="22" alt="">Untangle workflows and records

Find where the work stalls and which records represent the same real-world thing.

- <a href="https://github.com/process-intelligence-solutions"><img src="https://github.com/process-intelligence-solutions.png?size=48" width="20" height="20" alt="" title="process-intelligence-solutions on GitHub"></a> **[PM4Py](https://github.com/process-intelligence-solutions/pm4py)** `process mining`<br>
  Discover process variants and check conformance from customer event logs. Useful when the workflow described in interviews differs from the paths cases actually take.<br>
  <sub>Field note: Needs usable case identifiers, activities, and timestamps. A diagram cannot repair an incomplete event log.</sub>

- <a href="https://github.com/moj-analytical-services"><img src="https://github.com/moj-analytical-services.png?size=48" width="20" height="20" alt="" title="moj-analytical-services on GitHub"></a> **[Splink](https://github.com/moj-analytical-services/splink)** `probabilistic linkage`<br>
  Link customer, supplier, or patient records across systems without a shared identifier. Fellegi–Sunter match weights and comparison charts make the matching decision inspectable.<br>
  <sub>Field note: Choose blocking rules and review borderline matches. A high match probability is not proof that two people are the same.</sub>

- <a href="https://github.com/dedupeio"><img src="https://github.com/dedupeio.png?size=48" width="20" height="20" alt="" title="dedupeio on GitHub"></a> **[dedupe](https://github.com/dedupeio/dedupe)** `human-labeled matching`<br>
  Train record matching with examples labeled by the customer's domain expert. Active learning helps turn their judgment about names, addresses, and duplicates into a repeatable matcher.<br>
  <sub>Field note: Choose this when labeled examples should drive the model; use Splink when you need its probabilistic diagnostics and SQL backends.</sub>

- <a href="https://github.com/OpenRefine"><img src="https://github.com/OpenRefine.png?size=48" width="20" height="20" alt="" title="OpenRefine on GitHub"></a> **[OpenRefine](https://github.com/OpenRefine/OpenRefine)** `operator-led cleanup`<br>
  Cluster inconsistent values, reconcile them against a reference service, and retain the cleanup operations. Useful when an operator must approve ambiguous spreadsheet corrections.<br>
  <sub>Field note: Interactive cleanup comes first. Export the settled rules and test them before turning the session into an unattended import.</sub>

- <a href="https://github.com/dathere"><img src="https://github.com/dathere.png?size=48" width="20" height="20" alt="" title="dathere on GitHub"></a> **[qsv](https://github.com/dathere/qsv)** `CSV investigation`<br>
  Inspect large customer CSVs, infer a JSON Schema, calculate statistics, and isolate malformed records through a CLI. Useful before trusting an export or writing ingestion code.<br>
  <sub>Field note: Memory use depends on the command and options. Cardinality, quantiles, and schema enums do not share streaming commands' constant-memory behavior.</sub>

- <a href="https://github.com/saulpw"><img src="https://github.com/saulpw.png?size=48" width="20" height="20" alt="" title="saulpw on GitHub"></a> **[VisiData](https://github.com/saulpw/visidata)** `jump-host data exploration`<br>
  Inspect, join, filter, and compare customer extracts in a terminal spreadsheet. Useful on a remote host where a desktop cleanup application cannot run.<br>
  <sub>Field note: An interactive investigation tool, not an unattended validator. Keep the final transformation rules and test inputs outside the session.</sub>

- <a href="https://github.com/marimo-team"><img src="https://github.com/marimo-team.png?size=48" width="20" height="20" alt="" title="marimo-team on GitHub"></a> **[marimo](https://github.com/marimo-team/marimo)** `rerunnable analysis notebooks`<br>
  Run discovery-week analysis as reactive notebooks stored as plain Python that git-diff cleanly and re-execute deterministically. Useful when the exploration behind a data decision must stay reviewable through handoff.<br>
  <sub>Field note: Reactivity removes stale-cell surprises but re-executes downstream cells on edit. Pin data snapshots when rerunning against changed customer data would confuse the record.</sub>

- <a href="https://github.com/turbot"><img src="https://github.com/turbot.png?size=48" width="20" height="20" alt="" title="turbot on GitHub"></a> **[Steampipe](https://github.com/turbot/steampipe)** `live API investigation`<br>
  Query customer SaaS and cloud accounts through SQL plugins without first building a warehouse. Useful for checking cross-system inventory and permission assumptions during discovery.<br>
  <sub>Field note: Plugin calls still need approved credentials and API budgets. Results are live or cached, not a durable historical replication pipeline.</sub>

- <a href="https://github.com/simonw"><img src="https://github.com/simonw.png?size=48" width="20" height="20" alt="" title="simonw on GitHub"></a> **[Datasette](https://github.com/simonw/datasette)** `explorable extract handoff`<br>
  Publish a customer extract or migration dataset as a read-only web UI and JSON API with faceted search. Useful when operations staff need to find and verify records without waiting for an application to be built.<br>
  <sub>Field note: A publishing layer, not a secured application. Put it behind the customer's access controls; the interface does not make a sensitive extract safe to expose.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/plug.svg" width="30" height="22" alt="">Build the missing integration

Handle customer-specific grants, extraction state, and legacy interfaces instead of assuming a ready-made connector.

- <a href="https://github.com/NangoHQ"><img src="https://github.com/NangoHQ.png?size=48" width="20" height="20" alt="" title="NangoHQ on GitHub"></a> **[Nango](https://github.com/NangoHQ/nango)** `OAuth lifecycle` `source-available`<br>
  Manage per-customer API connections, token refresh, and authenticated proxy requests. Useful when each customer grants access separately and revoked consent needs a visible reconnect path.<br>
  <sub>Field note: Free self-hosting covers Auth and Proxy. Broader production functions and syncs have different deployment and plan requirements.</sub>

- <a href="https://github.com/airbytehq"><img src="https://github.com/airbytehq.png?size=48" width="20" height="20" alt="" title="airbytehq on GitHub"></a> **[Airbyte Python CDK](https://github.com/airbytehq/airbyte-python-cdk)** `custom source connectors`<br>
  Build the source connector missing from a customer's Airbyte setup. HTTP streams, pagination, partitions, and incremental state give the next engineer a defined connector interface.<br>
  <sub>Field note: The connector SDK earns the slot, not a new platform installation. Test cursors, deleted records, and resumption after a partial sync.</sub>

- <a href="https://github.com/dlt-hub"><img src="https://github.com/dlt-hub.png?size=48" width="20" height="20" alt="" title="dlt-hub on GitHub"></a> **[dlt](https://github.com/dlt-hub/dlt)** `schema-aware loading`<br>
  Write custom extraction and incremental loads while making schema changes explicit through schema contracts. Freeze an agreed schema or define how unexpected rows and columns are handled.<br>
  <sub>Field note: Schema inference is not business approval. Decide whether drift should stop the load, evolve the schema, or reject data.</sub>

- <a href="https://github.com/apache"><img src="https://github.com/apache.png?size=48" width="20" height="20" alt="" title="apache on GitHub"></a> **[Apache Camel](https://github.com/apache/camel)** `legacy protocol routing`<br>
  Connect existing enterprise interfaces such as SFTP, JMS, and SOAP with routing, transformations, and error handling. Useful when the integration boundary is more than a JSON API.<br>
  <sub>Field note: Check the exact component and endpoint semantics. Route retries still need a business-level duplicate-write strategy.</sub>

- <a href="https://github.com/svix"><img src="https://github.com/svix.png?size=48" width="20" height="20" alt="" title="svix on GitHub"></a> **[Svix](https://github.com/svix/svix-webhooks)** `signed webhook delivery`<br>
  Deliver customer-facing webhooks with signatures, retries, attempt visibility, and recovery controls. Useful when a customer endpoint goes offline and needs a reliable way to catch up.<br>
  <sub>Field note: Delivery is at least once. Receivers must verify signatures and deduplicate; a successful HTTP response does not prove the business transaction completed.</sub>

- <a href="https://github.com/redpanda-data"><img src="https://github.com/redpanda-data.png?size=48" width="20" height="20" alt="" title="redpanda-data on GitHub"></a> **[Redpanda Connect](https://github.com/redpanda-data/connect)** `stream normalization`<br>
  Map and route heterogeneous messages through declarative pipelines and Bloblang. Useful when customer queues and webhook payloads need normalization rather than another batch ELT connector.<br>
  <sub>Field note: The successor to Benthos. Check the chosen components and edition; at-least-once stream delivery and logs do not provide per-record provenance.</sub>

- <a href="https://github.com/apache"><img src="https://github.com/apache.png?size=48" width="20" height="20" alt="" title="apache on GitHub"></a> **[Apache NiFi](https://github.com/apache/nifi)** `operator-visible dataflows`<br>
  Build queued flows with backpressure and searchable record provenance. Useful when customer operators need to inspect where an individual record went and why it stopped.<br>
  <sub>Field note: An operated service, not a laptop utility. Configure provenance retention and disk budgets; prefer the customer's existing installation when available.</sub>

- <a href="https://github.com/jlowin"><img src="https://github.com/jlowin.png?size=48" width="20" height="20" alt="" title="jlowin on GitHub"></a> **[FastMCP](https://github.com/jlowin/fastmcp)** `MCP server scaffolding`<br>
  Build an MCP server over a customer system that has no agent surface, with typed tools, auth middleware, and testing utilities instead of hand-written protocol plumbing. Useful when the integration deliverable is an action interface for agents rather than another extraction pipeline.<br>
  <sub>Field note: Wrapping a legacy API adds no authorization. Map tools to the customer's permission model and test denied calls, not only the happy path.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/shield-check.svg" width="30" height="22" alt="">Preserve access across systems

A valid OAuth token and an indexed document do not establish permission to perform the customer's action.

- <a href="https://github.com/authzed"><img src="https://github.com/authzed.png?size=48" width="20" height="20" alt="" title="authzed on GitHub"></a> **[SpiceDB](https://github.com/authzed/spicedb)** `relationship permissions`<br>
  Model resource sharing and inherited permissions across customer systems. ZedTokens let a subsequent check require permission data at least as fresh as a known relationship change.<br>
  <sub>Field note: You must synchronize source relationships. Default low-latency reads can be stale; test revocation using the required consistency level.</sub>

- <a href="https://github.com/cerbos"><img src="https://github.com/cerbos.png?size=48" width="20" height="20" alt="" title="cerbos on GitHub"></a> **[Cerbos](https://github.com/cerbos/cerbos)** `attribute-based policy`<br>
  Evaluate versioned policies against principals, resources, and actions. Its query-plan API helps filter a list of customer records according to the same policy used for individual checks.<br>
  <sub>Field note: Provide trustworthy identity and resource attributes. Cerbos is a policy decision point, not an importer for the customer's document ACLs.</sub>

- <a href="https://github.com/openfga"><img src="https://github.com/openfga.png?size=48" width="20" height="20" alt="" title="openfga on GitHub"></a> **[OpenFGA](https://github.com/openfga/openfga)** `testable sharing models`<br>
  Model inherited resource access and keep Check, ListObjects, and ListUsers assertions with fixture tuples. Useful for reviewing the customer's sharing rules before the integration goes live.<br>
  <sub>Field note: Source tuple synchronization remains your job. Higher-consistency reads bypass caches; they are not SpiceDB's write-token freshness mechanism.</sub>

- <a href="https://github.com/cedar-policy"><img src="https://github.com/cedar-policy.png?size=48" width="20" height="20" alt="" title="cedar-policy on GitHub"></a> **[Cedar](https://github.com/cedar-policy/cedar)** `embedded policy decisions`<br>
  Evaluate fine-grained policies in an application and validate them against a declared schema. Useful when customer authorization rules must remain separate from code without adding a policy server.<br>
  <sub>Field note: The application supplies authenticated principals, entities, and context. Schema validation cannot prove those inputs describe the right customer.</sub>

- <a href="https://github.com/pomerium"><img src="https://github.com/pomerium.png?size=48" width="20" height="20" alt="" title="pomerium on GitHub"></a> **[Pomerium](https://github.com/pomerium/pomerium)** `clientless internal-app access`<br>
  Put identity- and context-based access checks in front of a customer-facing internal web application. Useful when browser users need controlled access without a VPN client.<br>
  <sub>Field note: The proxy must be reachable. This is application access, not document ACL import or a network that needs no inbound service ports.</sub>

- <a href="https://github.com/openziti"><img src="https://github.com/openziti.png?size=48" width="20" height="20" alt="" title="openziti on GitHub"></a> **[OpenZiti](https://github.com/openziti/ziti)** `private-service reachability`<br>
  Connect customer services through identity-based networking with outbound service registration. Useful when a private customer service cannot expose an inbound listening port.<br>
  <sub>Field note: Requires an operated fabric and a tunneler or embedded SDK. Routers still need reachable endpoints; network access does not grant business-record permission.</sub>

- <a href="https://github.com/open-policy-agent"><img src="https://github.com/open-policy-agent.png?size=48" width="20" height="20" alt="" title="open-policy-agent on GitHub"></a> **[Conftest](https://github.com/open-policy-agent/conftest)** `delivery-config policy checks`<br>
  Test structured deployment and integration configuration with Rego assertions. Keep customer-specific rules for approved destinations, required settings, and forbidden configuration in the handoff checks.<br>
  <sub>Field note: Checks declared artifacts before use. It is not runtime authorization and cannot prove that the installed service follows its configuration.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/git-compare.svg" width="30" height="22" alt="">Review data changes before cutover

Leave evidence that a schema, migration, or transformation changed what the business intended.

- <a href="https://github.com/datacontract"><img src="https://github.com/datacontract.png?size=48" width="20" height="20" alt="" title="datacontract on GitHub"></a> **[Data Contract CLI](https://github.com/datacontract/datacontract-cli)** `producer-consumer contracts`<br>
  Lint and test a shared data contract with schema and quality expectations. Useful when the customer and implementation team need a runnable agreement at their data boundary.<br>
  <sub>Field note: A passing contract only proves its declared checks. Include ownership and the business assumptions behind required fields.</sub>

- <a href="https://github.com/unionai-oss"><img src="https://github.com/unionai-oss.png?size=48" width="20" height="20" alt="" title="unionai-oss on GitHub"></a> **[Pandera](https://github.com/unionai-oss/pandera)** `dataframe boundary checks`<br>
  Validate dataframe columns, types, and custom rules inside ingestion code. Turn the customer's input assumptions into executable checks and identifiable failures.<br>
  <sub>Field note: Fits code-level validation. Keep representative rejected rows and decide which failures quarantine data versus stop the job.</sub>

- <a href="https://github.com/frictionlessdata"><img src="https://github.com/frictionlessdata.png?size=48" width="20" height="20" alt="" title="frictionlessdata on GitHub"></a> **[Frictionless](https://github.com/frictionlessdata/frictionless-py)** `portable file contracts`<br>
  Describe and validate tabular drops with Table Schema and Data Package descriptors. Useful when the file, its schema, and a validation report must travel between teams.<br>
  <sub>Field note: Checks a portable file boundary; it does not replace dataframe rules or warehouse monitoring.</sub>

- <a href="https://github.com/DataRecce"><img src="https://github.com/DataRecce.png?size=48" width="20" height="20" alt="" title="DataRecce on GitHub"></a> **[Recce](https://github.com/DataRecce/recce)** `dbt change review`<br>
  Compare baseline and candidate dbt environments using lineage, schema, profiles, and query-result diffs. Give business owners concrete before-and-after evidence for a model change.<br>
  <sub>Field note: dbt-specific. Align source snapshots and time-dependent filters so the review does not mistake changing inputs for changed logic.</sub>

- <a href="https://github.com/erezsh"><img src="https://github.com/erezsh.png?size=48" width="20" height="20" alt="" title="erezsh on GitHub"></a> **[Reladiff](https://github.com/erezsh/reladiff)** `cross-database reconciliation`<br>
  Compare copied tables across database engines with hash-based segment checks, or use a join within one database. Useful for proving that a customer migration retained the expected values.<br>
  <sub>Field note: Align keys, precision, and snapshots. Engine support varies; two actively changing tables do not provide a consistent comparison.</sub>

- <a href="https://github.com/OpenLineage"><img src="https://github.com/OpenLineage.png?size=48" width="20" height="20" alt="" title="OpenLineage on GitHub"></a> **[OpenLineage](https://github.com/OpenLineage/OpenLineage)** `run-level provenance`<br>
  Emit run, job, and dataset metadata so a customer can trace which integration produced a downstream result. Useful when handoff requires more than a diagram of the intended pipeline.<br>
  <sub>Field note: A standard and instrumentation ecosystem, not an automatic lineage scanner. Coverage depends on the integrations and facets you emit.</sub>

- <a href="https://github.com/treeverse"><img src="https://github.com/treeverse.png?size=48" width="20" height="20" alt="" title="treeverse on GitHub"></a> **[lakeFS](https://github.com/treeverse/lakeFS)** `object-data rollback` `source-available`<br>
  Branch and version object-store datasets without copying every object's bytes. Test a customer data transformation on a branch, then retain a commit that can be compared or reverted.<br>
  <sub>Field note: Works for data routed through lakeFS, not arbitrary OLTP writes. Retention and garbage collection determine which old objects remain recoverable.</sub>

- <a href="https://github.com/SQLMesh"><img src="https://github.com/SQLMesh.png?size=48" width="20" height="20" alt="" title="SQLMesh on GitHub"></a> **[SQLMesh](https://github.com/SQLMesh/sqlmesh)** `isolated change and backfill plans`<br>
  Review SQL model changes as a plan against a named environment, then test affected models and backfill ranges in isolation. Useful when a warehouse change needs a controlled cutover.<br>
  <sub>Field note: Fits projects that use SQLMesh, not an add-on to any dbt project. Review engine-specific isolation and source snapshots before treating a preview as production evidence.</sub>

- <a href="https://github.com/sdv-dev"><img src="https://github.com/sdv-dev.png?size=48" width="20" height="20" alt="" title="sdv-dev on GitHub"></a> **[SDV](https://github.com/sdv-dev/SDV)** `synthetic customer fixtures` `source-available`<br>
  Generate tabular fixtures that reflect a customer's distributions and relationships without directly shipping the original rows. Useful when realistic test cases cannot use raw customer extracts.<br>
  <sub>Field note: Synthetic does not mean private. Review disclosure risk, business constraints, and the edition's supported models before sharing generated fixtures.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/unplug.svg" width="30" height="22" alt="">Reproduce hostile dependencies

Expired credentials, partial responses, rate limits, and unavailable test windows belong in the acceptance suite.

- <a href="https://github.com/microcks"><img src="https://github.com/microcks.png?size=48" width="20" height="20" alt="" title="microcks on GitHub"></a> **[Microcks](https://github.com/microcks/microcks)** `multi-protocol contract mocks`<br>
  Turn customer API artifacts into mocks and conformance checks across protocols including REST, SOAP, and asynchronous APIs. Useful before the real dependency or its sandbox is available.<br>
  <sub>Field note: Mock fidelity depends on the specification and examples. Confirm the business behavior against the real service during the customer test window.</sub>

- <a href="https://github.com/wiremock"><img src="https://github.com/wiremock.png?size=48" width="20" height="20" alt="" title="wiremock on GitHub"></a> **[WireMock](https://github.com/wiremock/wiremock)** `explicit failure scenarios`<br>
  Program dependency responses and stateful sequences such as an expired token followed by successful reconnect. Useful when the acceptance test needs a precise failure, not a random outage.<br>
  <sub>Field note: Fixtures describe intended behavior. Track which pagination, rate-limit, and error cases were confirmed with the real API.</sub>

- <a href="https://github.com/SpectoLabs"><img src="https://github.com/SpectoLabs.png?size=48" width="20" height="20" alt="" title="SpectoLabs on GitHub"></a> **[Hoverfly](https://github.com/SpectoLabs/hoverfly)** `capture then simulate`<br>
  Capture HTTP interactions through a proxy, export the simulation, and replay it without repeatedly calling a customer dependency. Stateful simulations preserve meaningful request sequences.<br>
  <sub>Field note: Capture needs the client traffic to pass through the proxy. Scrub credentials and customer payloads before sharing simulations.</sub>

- <a href="https://github.com/keploy"><img src="https://github.com/keploy.png?size=48" width="20" height="20" alt="" title="keploy on GitHub"></a> **[Keploy](https://github.com/keploy/keploy)** `application-call replay`<br>
  Record application traffic and dependency interactions to replay integration tests with captured mocks. Useful when a working customer path exists but its regression fixtures do not.<br>
  <sub>Field note: Check the capture mode, runtime support, and ability to instrument the caller. Recorded traffic can contain sensitive customer data.</sub>

- <a href="https://github.com/Shopify"><img src="https://github.com/Shopify.png?size=48" width="20" height="20" alt="" title="Shopify on GitHub"></a> **[Toxiproxy](https://github.com/Shopify/toxiproxy)** `network fault injection`<br>
  Inject latency, disconnects, and bandwidth constraints into TCP dependencies. Prove that a connector resumes or fails predictably when the network becomes unreliable.<br>
  <sub>Field note: Tests transport failure, not application-level permission errors or malformed JSON. Add those cases separately.</sub>

- <a href="https://github.com/schemathesis"><img src="https://github.com/schemathesis.png?size=48" width="20" height="20" alt="" title="schemathesis on GitHub"></a> **[Schemathesis](https://github.com/schemathesis/schemathesis)** `schema-driven edge cases`<br>
  Generate property-based API tests from OpenAPI or GraphQL schemas. Find invalid inputs and response-contract failures beyond the successful requests used in the demo.<br>
  <sub>Field note: Use an authorized test environment. Add explicit assertions for business rules and writes that the schema cannot describe.</sub>

- <a href="https://github.com/oasdiff"><img src="https://github.com/oasdiff.png?size=48" width="20" height="20" alt="" title="oasdiff on GitHub"></a> **[oasdiff](https://github.com/oasdiff/oasdiff)** `breaking API changes`<br>
  Compare OpenAPI revisions and report breaking changes before a customer integration is updated. Useful when an upstream team changes fields, required parameters, or response contracts.<br>
  <sub>Field note: Compares declared specifications. It cannot detect an undocumented change in the live API.</sub>

- <a href="https://github.com/mitmproxy"><img src="https://github.com/mitmproxy.png?size=48" width="20" height="20" alt="" title="mitmproxy on GitHub"></a> **[mitmproxy](https://github.com/mitmproxy/mitmproxy)** `inspect actual traffic`<br>
  Intercept and modify authorized HTTP traffic to diagnose undocumented headers, redirects, and payload behavior. Useful when the observed customer integration contradicts its documentation.<br>
  <sub>Field note: Requires permission and a compatible trust setup. TLS pinning and locked customer clients can prevent interception.</sub>

- <a href="https://github.com/pact-foundation"><img src="https://github.com/pact-foundation.png?size=48" width="20" height="20" alt="" title="pact-foundation on GitHub"></a> **[Pact](https://github.com/pact-foundation/pact-reference)** `consumer-driven contracts`<br>
  Capture the interactions a customer's consuming application relies on, then verify them against the provider. Useful when different customers depend on different parts of the same API.<br>
  <sub>Field note: Choose the language binding for the application. Contract verification is not provider functional testing or an end-to-end business acceptance test.</sub>

- <a href="https://github.com/mountebank-testing"><img src="https://github.com/mountebank-testing.png?size=48" width="20" height="20" alt="" title="mountebank-testing on GitHub"></a> **[Mountebank](https://github.com/mountebank-testing/mountebank)** `raw-protocol simulations`<br>
  Stub text or binary TCP exchanges when a customer vendor interface is not HTTP. SMTP capture can verify that the integration sent the expected message.<br>
  <sub>Field note: TCP fixtures need explicit message framing; SMTP capture does not stub responses. The repository documents a maintainer transition, so review required protocol support.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/files.svg" width="30" height="22" alt="">Extract difficult customer inputs

Keep the source evidence and test the failure cases before treating extracted content as a business record.

- <a href="https://github.com/docling-project"><img src="https://github.com/docling-project.png?size=48" width="20" height="20" alt="" title="docling-project on GitHub"></a> **[Docling](https://github.com/docling-project/docling)** `layout-aware parsing`<br>
  Convert customer documents into structured content with reading order and table information. Useful when plain-text extraction loses the columns or layout that carry the meaning.<br>
  <sub>Field note: Inspect representative files against the originals. OCR and layout models add runtime dependencies; successful conversion does not guarantee accurate fields.</sub>

- <a href="https://github.com/ucbepic"><img src="https://github.com/ucbepic.png?size=48" width="20" height="20" alt="" title="ucbepic on GitHub"></a> **[DocETL](https://github.com/ucbepic/docetl)** `document-to-record pipelines`<br>
  Define LLM-based map, reduce, resolve, and related operations over document collections. Useful for extracting domain-specific records when a format parser cannot express the task.<br>
  <sub>Field note: Different job from PDF parsing. Retain labeled examples and inspect the pipeline; generated validators and model outputs still need review.</sub>

- <a href="https://github.com/data-privacy-stack"><img src="https://github.com/data-privacy-stack.png?size=48" width="20" height="20" alt="" title="data-privacy-stack on GitHub"></a> **[Presidio](https://github.com/data-privacy-stack/presidio)** `PII detection and masking`<br>
  Detect and anonymize sensitive text before approved logs, fixtures, or model calls leave the customer environment. Add domain-specific recognizers for identifiers the defaults miss.<br>
  <sub>Field note: Detection has false positives and false negatives. Test customer-specific formats; a clean scan is not proof that a payload contains no sensitive data.</sub>

- <a href="https://github.com/jsvine"><img src="https://github.com/jsvine.png?size=48" width="20" height="20" alt="" title="jsvine on GitHub"></a> **[pdfplumber](https://github.com/jsvine/pdfplumber)** `geometry-based PDF tables`<br>
  Inspect characters, ruling lines, and cell boundaries with visual debugging. Useful for a customer's repeatable invoice or report layout where explicit geometry is preferable to a layout model.<br>
  <sub>Field note: Works best on machine-generated PDFs. It does not add OCR to scans; retain failing examples when tuning table rules.</sub>

- <a href="https://github.com/mindee"><img src="https://github.com/mindee.png?size=48" width="20" height="20" alt="" title="mindee on GitHub"></a> **[docTR](https://github.com/mindee/doctr)** `controllable local OCR`<br>
  Choose text-detection and recognition models for customer images and scans. Useful when OCR must stay inside a restricted environment and the parsing pipeline needs model-level control.<br>
  <sub>Field note: The current library uses PyTorch. Stage weights and dependencies locally, and test scan quality; OCR output is not a validated business record.</sub>

- <a href="https://github.com/PaddlePaddle"><img src="https://github.com/PaddlePaddle.png?size=48" width="20" height="20" alt="" title="PaddlePaddle on GitHub"></a> **[PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** `multilingual document recognition`<br>
  Run OCR and structured document parsing over customer scans with language- and layout-oriented models. Useful for mixed-language forms, tables, and formulas that need local processing.<br>
  <sub>Field note: Choose and test the specific model, language coverage, and hardware requirement. Lightweight OCR and vision-language variants have different operating costs.</sub>

- <a href="https://github.com/ocrmypdf"><img src="https://github.com/ocrmypdf.png?size=48" width="20" height="20" alt="" title="ocrmypdf on GitHub"></a> **[OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF)** `searchable scanned PDFs`<br>
  Add an OCR text layer to scanned PDFs so existing page-based records can be searched and copied. Useful when the deliverable must remain a PDF rather than become extracted JSON.<br>
  <sub>Field note: Stage OCR language data for isolated installs. Signed PDFs are refused by default; modifying an approved copy can invalidate its signature. This is not PDF malware sanitization.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/workflow.svg" width="30" height="22" alt="">Survive retries and human approvals

Persist the business process and design for the crash after a downstream write but before its acknowledgement.

- <a href="https://github.com/temporalio"><img src="https://github.com/temporalio.png?size=48" width="20" height="20" alt="" title="temporalio on GitHub"></a> **[Temporal](https://github.com/temporalio/temporal)** `long-running business workflows`<br>
  Persist workflows through crashes and long waits for customer approval. Signals, activities, and execution history help coordinate business steps across unreliable systems.<br>
  <sub>Field note: Fits a customer who can operate or approve the workflow service. Retried external activities still require idempotency or reconciliation.</sub>

- <a href="https://github.com/restatedev"><img src="https://github.com/restatedev.png?size=48" width="20" height="20" alt="" title="restatedev on GitHub"></a> **[Restate](https://github.com/restatedev/restate)** `keyed durable handlers` `source-available`<br>
  Journal durable handlers and keep state around customer-specific entities. Useful for serializing work on the same record and resuming multi-step integration calls after failure.<br>
  <sub>Field note: Has its own runtime. An external side effect can repeat before its result is journaled; invocation deduplication alone does not prevent that.</sub>

- <a href="https://github.com/dbos-inc"><img src="https://github.com/dbos-inc.png?size=48" width="20" height="20" alt="" title="dbos-inc on GitHub"></a> **[DBOS](https://github.com/dbos-inc/dbos-transact-py)** `Postgres-backed workflows`<br>
  Add durable workflows and queues through a library that checkpoints into PostgreSQL. Useful when the customer already has Postgres and an extra orchestration service is difficult to operate.<br>
  <sub>Field note: Completed steps are checkpointed; unfinished external calls may repeat. Exactly-once database transactions do not imply exactly-once API writes.</sub>

- <a href="https://github.com/windmill-labs"><img src="https://github.com/windmill-labs.png?size=48" width="20" height="20" alt="" title="windmill-labs on GitHub"></a> **[Windmill](https://github.com/windmill-labs/windmill)** `operator approval pages`<br>
  Suspend a script flow and expose approval or cancellation through generated resume URLs and a run interface. Useful when the customer's operator needs an explicit human gate around an integration step.<br>
  <sub>Field note: Treat resume URLs as bearer credentials and enforce the required approver checks. A visible run history is not a tamper-evident approval ledger.</sub>

- <a href="https://github.com/hatchet-dev"><img src="https://github.com/hatchet-dev.png?size=48" width="20" height="20" alt="" title="hatchet-dev on GitHub"></a> **[Hatchet](https://github.com/hatchet-dev/hatchet)** `per-customer execution budgets`<br>
  Use customer-keyed concurrency, fair scheduling, and rate limits to keep one backfill from monopolizing workers or exhausting an upstream API budget.<br>
  <sub>Field note: Adds an orchestration service. Configure keys, queue policy, and failure handling; cancellation cannot undo a remote write already committed.</sub>

- <a href="https://github.com/langchain-ai"><img src="https://github.com/langchain-ai.png?size=48" width="20" height="20" alt="" title="langchain-ai on GitHub"></a> **[LangGraph](https://github.com/langchain-ai/langgraph)** `persisted agent interruption`<br>
  Checkpoint an agent workflow and interrupt before a tool action for customer review. Resume the saved thread with an explicit decision rather than asking the model to remember an approval.<br>
  <sub>Field note: Production needs a persistent checkpointer. Resume restarts the node, so earlier side effects must be idempotent. Supply authorization and an approval record separately.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## <img src="assets/icons/list-checks.svg" width="30" height="22" alt="">Prove the customer task works

Test direct tool behavior, then the model's choices, then the resulting business state.

- <a href="https://github.com/modelcontextprotocol"><img src="https://github.com/modelcontextprotocol.png?size=48" width="20" height="20" alt="" title="modelcontextprotocol on GitHub"></a> **[MCP Inspector](https://github.com/modelcontextprotocol/inspector)** `direct protocol testing`<br>
  Exercise a customer MCP server's tools, resources, and prompts without an agent deciding what to call. Separate transport, authentication, and argument failures from model behavior.<br>
  <sub>Field note: Protocol success is not business authorization. Test denied access and actual side effects, including tools advertised as read-only.</sub>

- <a href="https://github.com/snyk"><img src="https://github.com/snyk.png?size=48" width="20" height="20" alt="" title="snyk on GitHub"></a> **[Snyk agent-scan](https://github.com/snyk/agent-scan)** `agent toolchain audit`<br>
  Scan MCP servers, agent configurations, and skills for excessive permissions, tool poisoning, and injection exposure before they touch customer credentials. Useful when a community MCP server for the customer's system needs a security answer before connection.<br>
  <sub>Field note: Covers known patterns, not the server's runtime behavior. Treat a clean scan as one input to the customer's security review, and re-scan on version changes.</sub>

- <a href="https://github.com/promptfoo"><img src="https://github.com/promptfoo.png?size=48" width="20" height="20" alt="" title="promptfoo on GitHub"></a> **[promptfoo](https://github.com/promptfoo/promptfoo)** `customer-case regressions`<br>
  Version customer examples and compare prompts or models with assertions and adversarial cases. Useful for turning acceptance examples into a rerunnable regression suite.<br>
  <sub>Field note: Keep a held-out case set. A text or model-graded answer can pass while the downstream record is wrong; check resulting state separately.</sub>

- <a href="https://github.com/UKGovernmentBEIS"><img src="https://github.com/UKGovernmentBEIS.png?size=48" width="20" height="20" alt="" title="UKGovernmentBEIS on GitHub"></a> **[Inspect AI](https://github.com/UKGovernmentBEIS/inspect_ai)** `task-level evaluation`<br>
  Define tasks, solvers, and scorers with execution logs for multi-step agent behavior. Useful when acceptance depends on completing a customer workflow rather than producing a plausible answer.<br>
  <sub>Field note: Supply the real task fixtures and business-state scorer. An evaluation framework cannot decide what the customer's successful outcome means.</sub>

- <a href="https://github.com/langfuse"><img src="https://github.com/langfuse.png?size=48" width="20" height="20" alt="" title="langfuse on GitHub"></a> **[Langfuse](https://github.com/langfuse/langfuse)** `production-case traces`<br>
  Capture model, retrieval, and tool-call traces, attach scores, and turn reviewed customer cases into datasets. Useful for connecting acceptance regressions to failures observed in the delivered application.<br>
  <sub>Field note: Control which customer payloads enter telemetry. Trace visibility and replay do not prove the final business state; deployment features vary by edition.</sub>

- <a href="https://github.com/Arize-ai"><img src="https://github.com/Arize-ai.png?size=48" width="20" height="20" alt="" title="Arize-ai on GitHub"></a> **[Phoenix](https://github.com/Arize-ai/phoenix)** `retrieval and trace experiments` `source-available`<br>
  Inspect OpenTelemetry-based AI traces and compare retrieval or response experiments over versioned examples. Useful for distinguishing an extraction or retrieval failure from a prompt change.<br>
  <sub>Field note: Configure approved telemetry storage and model endpoints. Evaluator scores need calibration; the source-available project is separate from the managed Arize platform.</sub>

- <a href="https://github.com/confident-ai"><img src="https://github.com/confident-ai.png?size=48" width="20" height="20" alt="" title="confident-ai on GitHub"></a> **[DeepEval](https://github.com/confident-ai/deepeval)** `Python task-regression checks`<br>
  Add LLM and agent metrics to Python test suites alongside customer fixtures. Useful when domain regression checks should run with the implementation's existing test code.<br>
  <sub>Field note: Many metrics use model judges and incur calls. Keep deterministic business-state assertions and validate graders against examples reviewed by the customer.</sub>

- <a href="https://github.com/NVIDIA"><img src="https://github.com/NVIDIA.png?size=48" width="20" height="20" alt="" title="NVIDIA on GitHub"></a> **[garak](https://github.com/NVIDIA/garak)** `model vulnerability probes`<br>
  Run selected probe and detector families against an approved model endpoint for injection, leakage, and other failure modes. Useful before exposing a customer-facing model workflow.<br>
  <sub>Field note: Scope the scan and call budget to a test environment. Detected failures need investigation; a clean scan is not a safety or authorization proof.</sub>

- <a href="https://github.com/microsoft"><img src="https://github.com/microsoft.png?size=48" width="20" height="20" alt="" title="microsoft on GitHub"></a> **[PyRIT](https://github.com/microsoft/PyRIT)** `multi-turn adversarial testing`<br>
  Orchestrate multi-turn red-team strategies against an authorized AI target. Useful for testing whether an agent can be steered away from the customer's approved behavior over several exchanges.<br>
  <sub>Field note: Use approved test data and targets, with request budgets and review. Attack outcomes do not replace tool-level access checks or a business acceptance suite.</sub>

<p align="right"><a href="#contents">Back to contents ↑</a></p>

## Field references

| Read | Why it belongs |
| --- | --- |
| <img src="https://www.google.com/s2/favicons?domain=ycombinator.com&amp;sz=64" width="16" height="16" alt=""> [The FDE playbook with Bob McGrew](https://www.ycombinator.com/library/Mt-the-fde-playbook-for-ai-startups-with-bob-mcgrew) | Customer discovery, embedded engineering, and deciding what field work should become a product capability. |
| <img src="https://www.google.com/s2/favicons?domain=palantir.com&amp;sz=64" width="16" height="16" alt=""> [The Ontology system](https://www.palantir.com/docs/foundry/architecture-center/ontology-system/) | An operational model that connects data, decisions, actions, and security. Foundry-specific context, not a required platform. |
| <img src="https://www.google.com/s2/favicons?domain=anthropic.com&amp;sz=64" width="16" height="16" alt=""> [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) | Tasks, trials, graders, and checking what happened after an agent acted. |
| <img src="https://www.google.com/s2/favicons?domain=github.com&amp;sz=64" width="16" height="16" alt=""> [awesome-fde-resources](https://github.com/global-fde/awesome-fde-resources) | FDE learning, practice write-ups, and case material. A sibling list with a broader mandate than this catalog. |
| <img src="https://www.google.com/s2/favicons?domain=github.com&amp;sz=64" width="16" height="16" alt=""> [12-factor-agents](https://github.com/humanlayer/12-factor-agents) | Principles for production-grade agent software; the discipline behind several entries here. |
| <img src="https://www.google.com/s2/favicons?domain=github.com&amp;sz=64" width="16" height="16" alt=""> [agents-towards-production](https://github.com/NirDiamant/agents-towards-production) | Practical patterns and code for taking agents from demo to production. |

Use the [delivery recipes](docs/delivery-recipes.md) to plan an acceptance test, and the [engagement brief](docs/engagement-brief.md) to agree on the customer outcome, constraints, owner, and product follow-up.

## How this list is curated

Research proceeds in loops: discover candidates with Grok, compare neighboring tools, challenge claims, check primary sources, and cut entries that do not add enough. The [research record](research/README.md) includes decisions and corrections. Listed capabilities come from documentation, not a claim that every tool has been deployed in a customer environment.

Most entries are open source. `source-available` marks restricted projects; verify the deployment edition you need. Avatars identify the maintaining GitHub account, not necessarily the project's logo. Website links use favicons.

Contributions should name the customer failure, show the documented mechanism that addresses it, and explain why the nearest listed alternative is insufficient. Read [CONTRIBUTING.md](CONTRIBUTING.md).

---

<p align="center">
  <a href="https://github.com/tonysurfly"><img src="https://github.com/tonysurfly.png?size=64" width="32" height="32" alt="Tony's GitHub avatar"></a><br>
  Maintained by <a href="https://github.com/tonysurfly">Tony</a> · <a href="https://www.webfuse.com">Webfuse</a>
</p>