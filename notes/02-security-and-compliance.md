# Session 2 — Security and Compliance (Domain 2, ~30%)

*Security is the biggest domain on the exam — and the most important in real life.*

---

## 2.1 — Shared responsibility model

**The one diagram to keep in your head:**

| AWS is responsible for | You (customer) are responsible for |
|------------------------|-------------------------------------|
| **Security *of* the cloud** — hardware, hypervisor, physical DC, core network | **Security *in* the cloud** — data, IAM, OS patches on EC2, network config, encryption choices |

**Shared** depends on the service:

| Service type | You do more… | AWS does more… |
|--------------|--------------|----------------|
| **EC2** | OS patching, app security, security groups config | Physical host, hypervisor |
| **RDS** | DB user access, some network rules, encryption settings | OS patching, DB engine maintenance |
| **Lambda** | Your code, IAM permissions, env vars | Runtime, underlying infrastructure |

**Exam trap:** “AWS handles all security” → wrong. “Customer handles physical data center security” → wrong (that’s AWS).

---

## 2.2 — Security, governance, and compliance

### Why cloud security can be *better* (when done right)

- Encryption in transit (TLS) and at rest (KMS, S3 SSE)
- Fine-grained IAM
- Central logging and auditing

### Where compliance info lives

- **AWS Artifact** — download AWS compliance reports (SOC, PCI, etc.) for *your* audits.
- Industry/region rules vary — choose **Regions** and services that meet your requirements.

### Logging & governance (know the difference)

| Service | Role |
|---------|------|
| **CloudTrail** | **Who did what** API-wise (audit trail) |
| **CloudWatch** | **Metrics & monitoring**, alarms, logs (operational) |
| **AWS Config** | **Configuration history** and rules (compliance over time) |
| **Access reports** | e.g. S3 bucket access patterns |

### Security services (recognize the job)

| Service | One-liner |
|---------|-----------|
| **GuardDuty** | Threat detection (ML on logs/VPC flow) |
| **Inspector** | Vulnerability assessment for workloads |
| **Security Hub** | Central view of security findings |
| **Shield** | DDoS protection (Standard included; Advanced costs more) |
| **WAF** | Web application firewall (block SQLi, bad IPs at HTTP layer) |
| **Firewall Manager** | Central WAF rules across accounts |
| **Macie** | Discover/protect sensitive data in S3 |
| **Detective** | Investigate security issues from aggregated data |

**Encryption:** Know **in transit** vs **at rest**. **KMS** manages keys; **ACM** manages TLS certificates.

---

## 2.3 — Access management (IAM)

### IAM building blocks

- **Users** — long-term identity (prefer **not** for daily admin)
- **Groups** — attach policies to many users
- **Roles** — temporary credentials; used by EC2, Lambda, cross-account access
- **Policies** — JSON permissions; **managed** (AWS) vs **custom** (yours)

### Rules we repeated in class

1. **Root user** — created when you open the account. **Don’t use for daily work.** Enable **MFA**. Use only for tasks that *require* root.
2. **Least privilege** — minimum permissions to do the job.
3. **MFA** — something you know + something you have.

### IAM Identity Center (formerly SSO)

Single sign-on for humans into multiple AWS accounts and apps — federation for organizations.

### Authentication methods to recognize

- MFA on IAM users
- **IAM roles** (no access keys on instances when you use roles — best practice)
- **Federated access** (corporate IdP → AWS)
- **Cross-account roles**

### Credentials storage

- **Secrets Manager** — secrets + rotation
- **Systems Manager Parameter Store** — config and secrets (different feature set; both appear on exam at high level)

### Root-only tasks (pattern)

Account closure, changing certain account-level settings, restoring IAM user access when locked — exam questions often ask “what should you do first?” → **secure root with MFA**, create **admin IAM user/role** for daily ops.

---

## 2.4 — Security components and resources

### More edge protection

- **WAF** — application layer
- **Shield** — DDoS
- **GuardDuty** — intelligent threat detection

### Third-party security

Available via **AWS Marketplace** — antivirus, firewalls, etc.

### Where to learn more (official)

- **AWS Knowledge Center**
- **AWS Security Center**
- **AWS Security Blog**
- **Trusted Advisor** — basic security/cost/fault tolerance checks (also Domain 4)

---

## Session 2 — scenario cheat sheet

| Scenario | Lean toward |
|----------|-------------|
| Audit who deleted a bucket | CloudTrail |
| Alert when CPU > 80% | CloudWatch alarm |
| Prove resource was compliant last month | Config |
| Download AWS’s SOC report | Artifact |
| Block SQL injection at ALB | WAF |
| DDoS on public website | Shield (+ architecture with CloudFront often) |
| Temporary access for app on EC2 | IAM **role**, not hard-coded keys |
| Company login with Okta/Azure AD | IAM Identity Center / federation |

**Homework:** For EC2, RDS, and Lambda, write one line each: “Customer secures ___; AWS secures ___.”
