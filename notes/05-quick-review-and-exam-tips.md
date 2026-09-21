# Session 5 — Quick review & exam day tips

*Cram sheet before practice exam — not a substitute for doing questions.*

---

## Exam mechanics (CLF-C02)

- **50 scored** questions, **15 unscored** (same experience — don’t guess which)
- **Multiple choice** and **multiple response** (select **all** that apply)
- **No penalty** for wrong answers — **never leave blank**
- Pass: **700/1000**; compensatory scoring (strong in one domain can offset weaker areas)

---

## Domain weights (study time guide)

```
Security & Compliance     ████████████████  30%
Cloud Tech & Services     █████████████████  34%
Cloud Concepts            ████████████      24%
Billing & Support         ██████            12%
```

Spend extra time on **service matching** (Domain 3) and **IAM + shared responsibility** (Domain 2).

---

## High-yield comparisons

### S3 vs EBS vs EFS

| | S3 | EBS | EFS |
|---|----|-----|-----|
| Type | Object | Block | File (NFS) |
| Attach | Via API | One EC2 (usually) | Many EC2 |
| Use | Static assets, backup | Boot disk, DB on EC2 | Shared files |

### Lambda vs EC2

| Lambda | EC2 |
|--------|-----|
| Event-driven, short runs | Always-on, full OS control |
| AWS scales | You patch & size instances |
| Pay per invocation/time | Pay per instance hour |

### SNS vs SQS

| SNS | SQS |
|-----|-----|
| Push to many subscribers | Queue for workers |
| Fan-out | Buffer/decouple |

### CloudWatch vs CloudTrail vs Config

| CloudWatch | CloudTrail | Config |
|------------|------------|--------|
| Performance & ops metrics | API audit | Config compliance history |

---

## Well-Architected pillars (say them in order out loud)

1. Operational excellence  
2. Security  
3. Reliability  
4. Performance efficiency  
5. Cost optimization  
6. Sustainability  

---

## Security quick hits

- **Root user** → MFA, minimal use  
- **Least privilege** → IAM policies  
- **Artifact** → compliance **reports**  
- **KMS** → encryption **keys**  
- **Shield** → **DDoS**  
- **WAF** → **HTTP** threats  
- **GuardDuty** → threat **detection**

---

## Pricing quick hits

- **Spot** → cheap, can lose instance  
- **Reserved / Savings Plans** → commit, save money  
- **Pricing Calculator** → estimate **before**  
- **Cost Explorer** → analyze **after**  
- **Budgets** → **alerts**

---

## In-scope services — rapid fire (spell recognition)

**Compute:** EC2, Lambda, Beanstalk, Lightsail, Batch, Outposts  
**Containers:** ECS, EKS, ECR, Fargate  
**Storage:** S3, Glacier, EBS, EFS, FSx, Storage Gateway, Backup  
**DB:** RDS, Aurora, DynamoDB, ElastiCache, Neptune, DocumentDB  
**Network:** VPC, Route 53, CloudFront, Direct Connect, VPN, API Gateway  
**Security:** IAM, Identity Center, Cognito, KMS, WAF, Shield, GuardDuty, Inspector, Macie, Secrets Manager  
**Migration:** Migration Hub, DMS, SCT, Application Migration Service  
**ML:** SageMaker AI, Rekognition, Lex, Comprehend, Amazon Q  
**Integration:** SNS, SQS, EventBridge, Step Functions  

*(Full official list is in the exam guide — this is study flashcard style.)*

---

## Exam-day strategy (what our cohort agreed on)

1. **Flag** unclear questions; don’t burn 10 minutes on one item.
2. On **multiple response**, select only what you’re sure of — but if two answers are clearly right and a third is “maybe”, use judgment (no partial credit per question, but need minimum correct set).
3. Watch for **Region**, **cost**, **security**, and **managed vs unmanaged** keywords.
4. “Most secure” often means **MFA + least privilege + encryption + logging**, not “disable all access”.

---

## After you pass

- Associate paths: **Solutions Architect Associate**, **Developer Associate**, or **CloudOps** — pick based on role.
- Keep hands-on: certifications expire (recertify or advance).

Good luck — you’ve got the map; practice questions turn notes into recall.
