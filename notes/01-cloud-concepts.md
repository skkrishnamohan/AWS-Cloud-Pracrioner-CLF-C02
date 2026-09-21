# Session 1 — Cloud Concepts (Domain 1, ~24%)

*Today’s theme: why cloud, how AWS thinks about design, moving workloads, and money.*

---

## 1.1 — Benefits of the AWS Cloud

**Instructor opener:** “On-prem is like owning a generator. Cloud is like plugging into the grid — you scale up when you need to.”

### Value proposition (what to say in an interview or exam)

- **Agility** — launch resources in minutes, not months of procurement.
- **Elasticity** — scale out/in automatically (e.g. Auto Scaling) instead of buying peak capacity year-round.
- **High availability** — design across multiple AZs; AWS builds the physical redundancy, you design the architecture.
- **Global reach** — deploy close to users via Regions and edge networks.
- **Variable vs fixed cost** — shift capital expense (data centers) toward operational expense (monthly usage).

### Benefits tied to global infrastructure

- **Speed of deployment** — same APIs worldwide.
- **Global reach** — customers in Mumbai and Montreal can both get low latency if you place resources thoughtfully.

**Exam tip:** When a question asks “why move to cloud?” look for agility, elasticity, global scale, and paying for usage — not “AWS eliminates all security work” (it doesn’t).

---

## 1.2 — Design principles: AWS Well-Architected Framework

Six **pillars** — memorize these; they appear constantly:

| Pillar | Plain English |
|--------|----------------|
| **Operational excellence** | Run and monitor systems to deliver business value; learn from ops events. |
| **Security** | Protect data and systems; apply least privilege; automate security. |
| **Reliability** | Recover from failure; meet demand; test recovery. |
| **Performance efficiency** | Use the right resource types and sizes; evolve with demand. |
| **Cost optimization** | Avoid paying for unused capacity; use pricing models wisely. |
| **Sustainability** | Minimize environmental impact of cloud workloads (newer pillar — still on CLF-C02). |

**Well-Architected Tool** — AWS gives you a structured review against these pillars (management/governance category).

**Remember:** Pillars overlap. “Use Auto Scaling” hits performance *and* cost. “Encrypt data” hits security *and* reliability.

---

## 1.3 — Migration to the AWS Cloud

### Why migrate?

- Reduce data center footprint
- Faster innovation
- Better disaster recovery options
- Sometimes: regulatory or geographic requirements met via Regions

### AWS Cloud Adoption Framework (CAF)

High-level **perspectives** help organizations plan transformation (people, process, technology). For the exam, know CAF as a **structured migration/adoption guide**, not a single tool you install.

Outcomes AWS ties to CAF include things like:

- Reduced business risk
- Better ESG (environmental, social, governance) outcomes
- Revenue and efficiency gains

### Migration strategies (think “how do we get the app over?”)

You’ll see **6 R’s** in many courses (rehost, replatform, refactor, etc.). CLF-C02 also mentions understanding strategies like **database replication** for moving data.

**Services to associate with migration** (more detail in Session 3):

- **AWS Migration Hub** — track migrations
- **Application Migration Service** — lift-and-shift style server migration
- **AWS DMS** — database replication/migration
- **AWS SCT** — convert schemas between engines
- **Application Discovery Service** — inventory on-prem for planning

---

## 1.4 — Cloud economics

### Fixed vs variable costs

- **On-prem:** datacenter, racks, cooling, hardware you bought whether you use it or not → lots of **fixed** cost.
- **Cloud:** mostly **variable** — you pay for hours, GB, requests. (Reserved/Savings Plans add commitment but still “cloud economics”.)

### Other concepts that show up

| Term | Meaning |
|------|---------|
| **Rightsizing** | Pick instance/storage size that matches real need — not “largest by default”. |
| **Economies of scale** | AWS buys hardware in bulk; customers often get lower unit costs than DIY at small scale. |
| **BYOL** | Bring Your Own License — you supply the license; understand it vs **license included** in a managed service. |
| **Automation** | Less manual ops → fewer errors and often lower labor cost. |

**Exam tip:** “Moving to cloud always saves money” is **false** without governance. Cloud *enables* savings; waste is still possible (idle EC2, wrong storage class).

---

## Session 1 — one-page recap

1. Cloud = agility, elasticity, global infrastructure, pay-for-use.
2. Well-Architected = 6 pillars including **sustainability**.
3. Migration = CAF + tools like Migration Hub, DMS, Application Migration Service.
4. Economics = fixed vs variable, rightsizing, scale, licensing models.

**Homework:** Write one sentence per pillar with an AWS example (e.g. “Cost optimization → S3 Intelligent-Tiering”).
