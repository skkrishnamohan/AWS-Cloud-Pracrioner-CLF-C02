# Session 4 — Billing, Pricing, and Support (Domain 4, ~12%)

*Smallest domain on the exam — but everyone cares about the bill in real life.*

---

## 4.1 — AWS pricing models (especially compute)

### EC2 purchasing options

| Option | Plain English | Good when… |
|--------|---------------|------------|
| **On-Demand** | Pay by hour/second, no commitment | Short, unpredictable, dev/test |
| **Reserved Instances (RI)** | Commit 1 or 3 years for discount | Steady-state production |
| **Savings Plans** | Commit $/hour for 1 or 3 years; flexible across instance families | Like RI but more flexible |
| **Spot Instances** | Bid spare capacity; **can be interrupted** | Fault-tolerant, batch, stateless workers |
| **Dedicated Host** | Physical server for you (license/compliance) | Socket-level control, BYOL needs |
| **Dedicated Instance** | Single-tenant hardware, not full host visibility | Isolation without full host |
| **Capacity Reservations** | Reserve capacity in AZ without full RI discount model | You need capacity guarantee |

**Exam tips:**

- **Spot** = cheapest, interruptible.
- **Reserved / Savings Plans** = predictability + discount.
- **On-Demand** = most flexible, highest unit cost.

### Storage pricing ideas

- S3 cost drivers: storage class, requests, data transfer
- EBS: per GB-month + IOPS/throughput for some types
- Know **tiers/classes** matter — archive is cheaper than standard hot storage

### Data transfer (classic trick questions)

- **Into AWS** from internet — often **no charge** (check current docs; exam pattern favors “ingress free”).
- **Out to internet** — usually **charged**.
- **Between Regions** — typically **charged**.
- **Within same Region** (e.g. EC2 ↔ S3 same Region) — often **free or lower cost** than cross-Region.

Always read the scenario’s **Region** and **direction** (in vs out).

---

## 4.2 — Billing, budget, and cost management

| Tool | Purpose |
|------|---------|
| **AWS Pricing Calculator** | **Estimate** future costs before you build |
| **Cost Explorer** | **Visualize** historical spend, trends |
| **AWS Budgets** | **Alerts** when cost/usage exceeds threshold |
| **Cost and Usage Report (CUR)** | Detailed billing data export (often to S3) |
| **Cost allocation tags** | Attribute spend to team/project on bills |

### AWS Organizations

- **Consolidated billing** — one payer, many accounts
- **Volume discounts** can pool across accounts
- **RI benefits** can share within org (exam mentions RI flexibility / org behavior at high level)

**Marketplace** — third-party software; can affect governance and entitlements (also tied to partner ecosystem).

---

## 4.3 — Technical resources and support

### Where to get answers (self-service)

| Resource | What it is |
|----------|------------|
| **Documentation** | docs.aws.amazon.com |
| **AWS re:Post** | Community Q&A (replaced a lot of old forums patterns) |
| **Knowledge Center** | Short answers to common questions |
| **Prescriptive Guidance** | Architecture patterns and guides |
| **Whitepapers & blogs** | Deep dives (Well-Architected, security, etc.) |

### AWS Support plans (know the ladder)

From **basic** (free, account/billing only) up through paid plans — exam expects you to match **need → plan**:

| Plan (concept) | Who it fits |
|----------------|-------------|
| **Developer** | Experimental / single developer |
| **Business** | Production workloads; faster response |
| **Enterprise On-Ramp** | Mid-size production, subset of enterprise benefits |
| **Enterprise** | Mission-critical; TAM, fastest response |

**Basic** includes **Trusted Advisor** core checks and **Health Dashboard** — not the same as 24/7 technical support on production incidents.

### Operational help beyond support tickets

- **AWS Professional Services** — paid implementation help
- **Solutions architects** — AWS can advise on architecture (sales/account teams in real world)
- **AWS Partner Network (APN)** — partners (ISVs, system integrators) extend AWS
- **AWS Marketplace** — buy software that runs on AWS

### Monitoring cost and health

- **Trusted Advisor** — cost optimization, security, fault tolerance, performance checks
- **Health Dashboard** — AWS platform events affecting your resources
- **Health API** — programmatic health info

### Trust and Safety

Report **abuse** of AWS resources (spam, phishing hosted on AWS) → **AWS Trust and Safety** (know it exists for exam).

---

## Session 4 — money myths (false on exam)

- “Reserved Instances are only for one instance type forever” → **RI and Savings Plans have flexibility options** (read question carefully).
- “All data transfer is free inside AWS” → **cross-Region still costs**.
- “Support plan replaces CloudWatch” → **no** — different purposes.

**Homework:** Use **Pricing Calculator** for a tiny architecture (one EC2 + S3 + RDS). Compare On-Demand vs 1-year Reserved estimate.
