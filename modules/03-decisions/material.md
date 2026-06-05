# Material — Module 03: Architecture Decision Records

---

## Section 1: What an ADR Is — and Why It Matters for Data Systems

In 2011, Michael Nygard published a short blog post proposing a simple format for capturing architectural decisions in software projects. His argument was direct: architecture documentation that exists in a separate document nobody reads is worthless. The decision record should live in the codebase, version-controlled, readable by the people who will be affected by the decision.

The format spread through software engineering and has since become a standard practice in mature engineering organizations. For data systems specifically, ADRs solve a problem that is more acute than in application development: **data architectures change slowly, live for a long time, and are inherited by people who had no context when they were built.**

A microservice can be rewritten in a sprint. A data warehouse schema affects years of historical data, downstream models, reports, and contracts. A decision about partitioning strategy, storage format, or modeling approach made in 2021 will still be constraining a team in 2027. Without an ADR, that constraint looks like an accident. With one, it's a documented trade-off that the team can evaluate against current conditions.

### What an ADR is not

| Common misconception | Reality |
|---|---|
| An ADR is a design document | An ADR records a decision that was made — not a proposal for what to do |
| An ADR is for big decisions only | An ADR is for decisions that are hard to reverse and affect more than one component |
| An ADR needs approval before merging | An ADR is written by the architect, reviewed like code, merged when the decision is made |
| An ADR explains what we built | An ADR explains *why* we built it this way and *what we rejected* |
| ADRs go in Confluence / Notion | ADRs live in the code repository, in a `/decisions` folder, versioned alongside the code they explain |

---

## Section 2: The Anatomy of a Strong ADR

Every ADR has six required sections. None are optional. An ADR missing any section is incomplete.

### Structure

```
# ADR-[NNN]: [Short imperative title — what was decided]

**Status**: [Proposed | Accepted | Deprecated | Superseded by ADR-NNN]
**Date**: YYYY-MM-DD
**Deciders**: [Names or roles of people who made this decision]

## Context

[Describe the situation that required a decision. What problem exists?
What forces are at play? What does the system look like today?
Write this as a neutral description — not advocacy for the decision you made.
A reader with no context should understand the situation completely after
reading this section.]

## Decision Drivers

[Bullet list of the specific factors that shaped this decision.
These are the criteria you used to evaluate options.
Examples: cost constraints, team skill availability, compliance requirements,
operational complexity tolerance, delivery timeline, reversibility needs.]

## Options Considered

[For each option evaluated:]

### Option A: [Name]
[What it is, briefly. What it would mean in practice.
Why it was considered.]
- **Pro**: [specific benefit]
- **Pro**: [specific benefit]
- **Con**: [specific cost]
- **Con**: [specific cost]

### Option B: [Name]
[Same structure]

### Option C: [Name — if applicable]
[Same structure]

## Decision

[State what was decided in one sentence.
Then explain why — referencing the decision drivers and the options considered.
Do not introduce new reasoning here that wasn't in the decision drivers.
The decision should feel inevitable given the context and drivers.]

## Consequences

### Positive
- [Specific benefit that results from this decision]
- [Specific benefit]

### Negative
- [Specific cost or limitation that results from this decision]
- [Specific cost — be honest, these are the real costs accepted]

### Risks
- [Something that could go wrong given this decision — not mitigated, just named]

### Follow-on decisions required
- [What other decisions does this one trigger or require?]
```

---

## Section 3: The Decision Threshold — What Deserves an ADR?

The most common question about ADRs is: "do I write one for everything?"

No. An ADR for every configuration choice would create noise that makes the real decisions invisible. The threshold is clear: write an ADR when the decision meets **at least two** of these criteria:

| Criterion | Description |
|---|---|
| **Hard to reverse** | Undoing this decision requires significant effort — migration, replatform, schema change, or team coordination |
| **Cross-cutting** | Affects more than one component, team, or system boundary |
| **Trade-off-laden** | There are genuinely viable alternatives that were rejected for specific reasons |
| **Invisible in the code** | A future engineer reading the codebase cannot infer why this choice was made |
| **Compliance-relevant** | The decision has regulatory, security, or contractual implications |

### Examples: ADR or not?

| Decision | ADR? | Why |
|---|---|---|
| Use Delta Lake as the storage format for all Gold layer tables | **Yes** | Hard to reverse, cross-cutting, trade-off-laden (vs. Iceberg, Parquet), invisible in code |
| Partition the `orders` table by `order_date` | **No** | Reversible with a single migration, affects one table, not cross-cutting |
| Adopt a single-tenant warehouse model over multi-tenant | **Yes** | Hard to reverse, cross-cutting, compliance-relevant |
| Use UTC as the standard timezone for all timestamps | **Yes** | Invisible in code, cross-cutting, hard to reverse in historical data |
| Name staging tables with the prefix `stg_` | **No** | Convention, easily changed, affects only the transformation layer |
| Ingest PII data only in the Bronze layer and mask it in Silver | **Yes** | Compliance-relevant, cross-cutting, shapes every downstream pipeline |
| Use 7-day retention for raw event logs in S3 | **Maybe** | Depends on compliance requirements — if regulatory, yes; if just cost, probably no |

When in doubt: write the ADR. The cost of writing an unnecessary ADR is low. The cost of not writing a necessary one compounds over years.

---

## Section 4: Two Complete ADR Examples

### ADR-001: Use Delta Lake as the Default Table Format for All Gold Layer Tables

**Status**: Accepted
**Date**: 2023-08-14
**Deciders**: Data Platform Team Lead, Senior Data Engineer, Head of Data

---

#### Context

The data platform team is building the Gold layer of a medallion architecture on Databricks running on AWS S3. The team needs to choose a table format for all Gold layer tables — the layer consumed by BI tools, data scientists, and external reporting systems. The current Bronze and Silver layers use plain Parquet with no table format layer.

Three engineers have active Databricks certifications. The organization has a 2-year Databricks enterprise contract with Delta Lake included at no additional cost. Data scientists use Databricks notebooks as their primary analysis environment. The BI team uses Tableau connecting via Databricks SQL.

#### Decision Drivers

- Team expertise: 3 of 4 engineers have Databricks and Delta Lake production experience
- Databricks contract: Delta Lake is included in the existing license; other formats require additional tooling
- ACID transactions: Gold layer tables are updated in-place by monthly restatement jobs; plain Parquet cannot support concurrent reads during updates
- Time-travel: The audit team has requested 30-day historical snapshots for compliance without storing full copies
- Schema evolution: product taxonomy changes 3–4 times per year and requires non-breaking column additions

#### Options Considered

##### Option A: Delta Lake
An open-source storage layer that brings ACID transactions, schema enforcement, and time-travel to Parquet files on object storage.
- **Pro**: Native Databricks support, included in current license, team expertise
- **Pro**: ACID transactions solve the concurrent read/write problem for restatement jobs
- **Pro**: Time-travel satisfies audit requirements without duplicate storage
- **Pro**: Schema evolution handles taxonomy changes safely
- **Con**: Vendor alignment — Delta Lake is driven by Databricks; migrating away requires converting all Gold tables
- **Con**: Delta log files add metadata overhead and require periodic VACUUM operations

##### Option B: Apache Iceberg
An alternative open table format with broader ecosystem support (Spark, Flink, Trino, Snowflake, Athena).
- **Pro**: True vendor-neutral — compatible with multiple compute engines
- **Pro**: Better partition evolution capabilities than Delta Lake
- **Con**: No team expertise; ramp-up time estimated at 6–8 weeks
- **Con**: Not included in Databricks license; requires additional tooling configuration
- **Con**: Databricks support for Iceberg is read-only in the current contract tier

##### Option C: Plain Parquet
No table format layer — files stored directly as Parquet on S3.
- **Pro**: Maximum simplicity; no format-specific tooling required
- **Pro**: Readable by any Spark, Athena, or Presto job without configuration
- **Con**: No ACID transactions — concurrent reads during restatement jobs produce inconsistent results
- **Con**: No time-travel — 30-day audit requirement cannot be met without storing full copies
- **Con**: Schema evolution requires manual coordination and risky in-place rewrites

#### Decision

Adopt Delta Lake as the default table format for all Gold layer tables.

Given the team's existing expertise, the included licensing, and the Gold layer's specific requirements (ACID transactions for monthly restatements, time-travel for audit compliance, schema evolution for taxonomy changes), Delta Lake is the only option that satisfies all three requirements without additional cost or ramp-up time. Iceberg's superior portability is a meaningful advantage in principle but not in practice for a team with a 2-year Databricks contract and no engine diversity today.

#### Consequences

**Positive**
- Monthly restatement jobs can run with MERGE operations without locking out concurrent reads
- 30-day audit snapshots available via `VERSION AS OF` queries at no additional storage cost
- Schema changes can be deployed without pipeline downtime

**Negative**
- All Gold layer tables are now Delta format — migrating to a different compute engine (e.g., Snowflake, Trino) requires converting Delta tables, which is a significant migration effort
- VACUUM jobs must be scheduled and monitored to prevent unbounded Delta log growth

**Risks**
- Databricks contract renewal may change the licensing terms for Delta Lake features; this should be verified at each renewal

**Follow-on decisions required**
- ADR for VACUUM and OPTIMIZE scheduling policy for Gold layer tables
- Decision on whether Silver layer tables should also migrate to Delta (separate ADR recommended)

---

### ADR-002: Adopt a Single-Tenant Warehouse Model Over Multi-Tenant

**Status**: Accepted
**Date**: 2024-01-22
**Deciders**: Head of Data, Data Architect, Legal/Compliance

---

#### Context

The data platform serves three internal consumer groups: the BI team (30 analysts), the Data Science team (8 engineers), and the Product Analytics team (5 engineers). Each team has different access requirements, query patterns, and data sensitivity levels. The platform currently uses a single Snowflake account with shared compute and shared storage, with access control managed via Snowflake roles.

Legal has flagged that some Gold layer tables contain aggregated customer behavioral data that, while not PII itself, is considered commercially sensitive. Product Analytics requires access to raw-level event data that BI should not see. Data Science requires ML feature tables that are not relevant to other teams.

Two architecture models are under consideration for organizing tenant isolation.

#### Decision Drivers

- Access control: teams should not be able to query each other's sensitive data without explicit grants
- Cost attribution: leadership has requested per-team compute cost visibility
- Operational complexity: the platform team has 2 engineers and cannot maintain 3 separate Snowflake accounts
- Compliance: no legal requirement for physical isolation — logical isolation via RBAC is sufficient
- Onboarding: new teams should be addable without creating new infrastructure

#### Options Considered

##### Option A: Single-tenant (one account, per-team databases and warehouses)
All teams share one Snowflake account. Isolation is achieved through separate databases per consumer group and dedicated virtual warehouses per team for compute cost visibility.
- **Pro**: One billing account, one set of credentials, one monitoring surface
- **Pro**: Cross-team joins remain possible when explicitly granted — useful for federated models
- **Pro**: New teams onboarded by creating a database + warehouse + role set, no new infrastructure
- **Con**: A misconfigured grant can expose one team's data to another — requires governance discipline
- **Con**: Physical isolation is not achievable — if required by compliance in the future, migration is necessary

##### Option B: Multi-tenant (separate Snowflake account per team)
Each consumer group gets its own Snowflake account. Data shared across teams via Snowflake Secure Data Sharing.
- **Pro**: True physical isolation — accounts cannot access each other's data by default
- **Pro**: Separate billing per account is automatic
- **Con**: Cross-team queries require Data Sharing setup, which adds operational overhead and latency
- **Con**: Maintaining 3+ Snowflake accounts (provisioning, monitoring, upgrades, credential rotation) with a 2-person platform team is operationally unsustainable
- **Con**: Onboarding a new team requires provisioning a new account — 3–5 day lead time

#### Decision

Adopt a single-tenant model with per-team databases and dedicated virtual warehouses for compute isolation.

Physical isolation via separate accounts exceeds the compliance requirement (legal confirmed RBAC is sufficient) and is operationally infeasible for a 2-person platform team. The single-account model provides the required logical isolation and per-team cost visibility without creating unsustainable operational overhead. The risk of misconfigured grants will be mitigated through automated access review tooling (scheduled quarterly).

#### Consequences

**Positive**
- Per-team cost attribution via dedicated virtual warehouses satisfies leadership's reporting requirement
- Access control is manageable and auditable within one account
- Cross-team data sharing (when authorized) does not require infrastructure changes

**Negative**
- Physical data isolation is not achieved — if a compliance requirement for physical isolation emerges (e.g., due to regulatory change or enterprise customer requirement), migration to multi-tenant is a significant effort
- RBAC governance discipline is mandatory — a single misconfigured role can expose data across teams. This is an ongoing operational risk, not a one-time migration

**Risks**
- Snowflake account compromise would expose all teams' data simultaneously — single failure domain
- Compliance requirements may change; this decision should be reviewed annually against current legal guidance

**Follow-on decisions required**
- ADR for role naming convention and grant management policy
- Decision on process for requesting cross-team data access

---

## Section 5: How to Review Someone Else's ADR

Reading and improving ADRs is as important as writing them. When you review an ADR, you are not approving or rejecting the decision — you are checking whether the record is honest, complete, and useful to a future reader who has no context.

### A structured review checklist

| Section | What to check |
|---|---|
| **Context** | Could someone with no knowledge of the system understand the situation? Is the context neutral — not pre-arguing for the eventual decision? |
| **Decision Drivers** | Are the drivers specific? Are they the *actual* reasons, or are they post-hoc rationalizations? Are any important drivers missing? |
| **Options Considered** | Are all options treated with equal rigor? Is there a straw man (an option described so poorly it couldn't win)? Were any obvious options omitted? |
| **Decision** | Does the decision follow logically from the drivers? Does it introduce new reasoning not in the drivers section? |
| **Consequences — Negative** | Are the negative consequences honest? If the negative section is empty or has only trivial items, the ADR is advocacy, not a record. |
| **Follow-on decisions** | Are there obvious downstream decisions triggered by this one that aren't mentioned? |

### How to write feedback

Feedback on an ADR should be specific and reference evidence. Avoid general comments.

**Weak feedback**: "The options section could be more detailed."

**Strong feedback**: "Option B (Apache Iceberg) is described as having 'limited ecosystem support,' but Iceberg has native connectors for Spark, Flink, Trino, Athena, and Snowflake — that characterization appears inaccurate and would lead a future reader to discount Iceberg unfairly. Please verify and revise."

**Weak feedback**: "You should add negative consequences."

**Strong feedback**: "The Consequences section lists three positive outcomes but no negative ones. At minimum, the Delta Lake vendor lock-in (all Gold tables require conversion to migrate away from Databricks) should be documented as a consequence. That's a real and significant cost that the team accepted."
