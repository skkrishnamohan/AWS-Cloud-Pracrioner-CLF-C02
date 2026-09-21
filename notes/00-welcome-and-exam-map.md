# Session 0 — Welcome & how this course maps to the exam

*Notes from day one — before we open the AWS console.*

---

## Why this certification exists

AWS Cloud Practitioner is the **“speak cloud confidently”** cert. You’re not expected to design a full production architecture or write production code for this exam. You *are* expected to:

- Explain **why** companies use AWS
- Name **core services** and what problem each solves
- Understand **security basics** and the **shared responsibility model**
- Talk about **pricing** without panicking at the bill

Think of it as cloud literacy for everyone — engineers, sales, finance, product, support.

---

## CLF-C02 syllabus (what the exam actually tests)

This matches the official **Content Outline** weights:

| Domain | Weight | What you’ll feel on exam day |
|--------|--------|------------------------------|
| 1. Cloud Concepts | 24% | Benefits of cloud, Well-Architected, migration, economics |
| 2. Security and Compliance | 30% | Shared responsibility, IAM, compliance tools, security services |
| 3. Cloud Technology and Services | 34% | Regions/AZs, compute, storage, DB, network, analytics, AI/ML, more |
| 4. Billing, Pricing, and Support | 12% | EC2 pricing models, Cost Explorer, support plans, AWS docs |

**Mental model:** Domain 3 is the biggest slice — lots of “which service fits this scenario?” questions. Domain 2 is second — security shows up everywhere in real jobs too.

---

## Vocabulary you’ll hear every session

- **Region** — geographic area (e.g. `us-east-1`). You choose it for latency, compliance, or pricing.
- **Availability Zone (AZ)** — isolated data centers *inside* a Region. Use multiple AZs for high availability.
- **Edge location** — cache/content closer to users (think **CloudFront**).
- **Pay-as-you-go** — no big upfront hardware; you pay for what you use (with exceptions like Reserved capacity).
- **Managed service** — AWS runs more of the stack (e.g. RDS); you configure and use it.
- **Console vs CLI vs API/SDK** — same cloud, different doors in.

---

## How to study (what actually worked in class)

1. **One domain per week** is fine — don’t cram all services in one night.
2. **Free Tier + Labs:** Create something tiny (S3 bucket, EC2 t2/t3 micro if still eligible, IAM user). Names stick after you click them once.
3. **Practice questions:** Official AWS practice set beats random memorization.
4. **Scenario questions:** Read the *business problem* first (“low traffic website”, “batch once a night”, “need SQL”), then pick the service.

---

## What’s explicitly *out of scope* for CLF-C02

Per the exam guide, you’re **not** tested on deep implementation: coding apps, designing full architectures, troubleshooting production, load testing, etc.

You **are** tested on recognizing services and concepts at a **foundational** level.

---

## My running “exam map” checklist

- [ ] I can explain the **six Well-Architected pillars** (including **sustainability**)
- [ ] I can split **customer vs AWS** responsibilities for EC2, Lambda, and RDS
- [ ] I know **S3 vs EBS vs EFS** in one sentence each
- [ ] I know when **Lambda** beats **EC2** for a use case
- [ ] I can compare **On-Demand, Reserved, Spot, Savings Plans**
- [ ] I know where to find **compliance reports** (Artifact) and **logs** (CloudTrail)

Next session: **Domain 1 — Cloud Concepts.**
