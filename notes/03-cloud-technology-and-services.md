# Session 3 — Cloud Technology and Services (Domain 3, ~34%)

*The “service menu” session — biggest domain. Goal: match problems to services, not memorize every feature.*

---

## 3.1 — Deploying and operating in AWS

### Ways to interact

| Method | When students use it |
|--------|----------------------|
| **Management Console** | Learning, one-off changes |
| **AWS CLI** | Scripts, automation |
| **SDKs** | Apps calling AWS APIs |
| **CloudFormation** | **Infrastructure as Code (IaC)** — repeatable, version-controlled stacks |

### Deployment models

- **Cloud** — all in AWS
- **Hybrid** — on-prem + AWS (VPN, Direct Connect, Outposts)
- **On-premises** — still your DC; AWS tools can extend to it (Outposts, Storage Gateway)

**One-time vs repeatable:** Exam favors **IaC** and pipelines for production; console clicks for experiments.

---

## 3.2 — Global infrastructure

```
Region (e.g. eu-west-1)
 ├── Availability Zone A
 ├── Availability Zone B
 └── Availability Zone C (typically 3+ AZs per Region)

Edge locations (many) → CloudFront caching
```

- **Region** — geographic; choose for latency, sovereignty, service availability.
- **AZ** — isolated failure domain within Region; **multi-AZ = high availability**.
- **Edge location** — content delivery / caching closer to users.

**Multi-Region** — disaster recovery, global users, regulatory data residency.

**Remember:** AZs don’t share a single point of failure with each other (design assumption for HA).

---

## 3.3 — Compute

| Service | Use when… |
|---------|-----------|
| **Amazon EC2** | You need a VM; full control of OS; steady or custom workloads |
| **Auto Scaling** | Match capacity to demand |
| **Elastic Load Balancing (ELB)** | Spread traffic across instances/targets |
| **AWS Lambda** | Short, event-driven code; no server management |
| **AWS Fargate** | Run containers without managing EC2 for them |
| **Amazon ECS / EKS** | Container orchestration (Docker/Kubernetes) |
| **AWS Batch** | Large batch jobs |
| **Elastic Beanstalk** | Upload app; AWS handles capacity (PaaS-style) |
| **Lightsail** | Simple VPS + predictable pricing for small sites |
| **AWS Outposts** | AWS hardware **in your datacenter** (hybrid) |

### EC2 instance families (high level)

- **Compute optimized** — CPU-heavy
- **Storage optimized** — big local disks / high I/O
- **Memory optimized** — RAM-heavy (databases, caches in memory)

**Serverless** on exam = Lambda, Fargate (no EC2 management for you).

---

## 3.4 — Databases

| Type | AWS examples | Typical use |
|------|--------------|-------------|
| **Relational (SQL)** | RDS, Aurora | Transactions, joins, legacy apps |
| **NoSQL** | DynamoDB | Key-value/document; massive scale, single-digit ms |
| **In-memory cache** | ElastiCache | Speed up reads; session cache |
| **Graph** | Neptune | Relationships (social, fraud graphs) |
| **Document** | DocumentDB | MongoDB-compatible workloads |

**EC2-hosted DB vs managed:** RDS/Aurora = AWS patches, backups, Multi-AZ options. EC2 DB = you’re the DBA.

**Migration:** **DMS** replicates data; **SCT** converts schemas (e.g. Oracle → PostgreSQL).

---

## 3.5 — Networking

### Amazon VPC (your private network in AWS)

- **Subnets** — segment network (public vs private)
- **Route tables** — where traffic goes
- **Internet Gateway** — public internet for public subnets
- **NAT Gateway** — outbound internet for private subnets without inbound from internet

### Security in VPC

| Tool | Level |
|------|--------|
| **Security group** | Instance/ENI — stateful firewall |
| **Network ACL** | Subnet — stateless rules |

**Route 53** — DNS (domain names → IP); health checks; routing policies.

### Connect on-prem to AWS

- **Site-to-Site VPN** — encrypted over internet
- **Direct Connect** — dedicated private link (more consistent latency)
- **Client VPN** — individual laptops into VPC

Also know: **CloudFront** (CDN), **API Gateway** (manage APIs), **Global Accelerator** (anycast for TCP/UDP), **Transit Gateway** (hub for many VPCs), **PrivateLink** (private access to services).

---

## 3.6 — Storage

| Service | What it is | Exam mnemonic |
|---------|------------|---------------|
| **S3** | Object storage | “Photos, backups, static website files” |
| **S3 Glacier / Glacier classes** | Archive / cold storage | Cheap, slower retrieval |
| **EBS** | Block storage for EC2 | Boot volumes, databases on EC2 |
| **Instance store** | Ephemeral disk on host | Fast, **lost if instance stops** |
| **EFS** | Shared file (NFS) | Many EC2 need same files |
| **FSx** | Managed Windows/Lustre/etc. file systems | Special file workloads |
| **Storage Gateway** | Hybrid cache to cloud | On-prem apps → S3/EBS-backed |
| **AWS Backup** | Central backup policies | Across services |

**S3 storage classes** — know there are tiers for frequent vs infrequent vs archive access; **lifecycle policies** move objects automatically.

---

## 3.7 — Analytics and AI/ML

### Analytics

| Service | Job |
|---------|-----|
| **Athena** | SQL queries on S3 |
| **Glue** | ETL / data catalog |
| **Kinesis** | Streaming data |
| **QuickSight** | Dashboards / BI |
| **Redshift** | Data warehouse |
| **EMR** | Big data (Spark, Hadoop) |
| **OpenSearch** | Search and log analytics |

### AI/ML (recognize, don’t build models on exam)

| Service | Job |
|---------|-----|
| **SageMaker AI** | Build/train/deploy ML |
| **Lex** | Chatbots |
| **Polly** | Text-to-speech |
| **Rekognition** | Image/video analysis |
| **Comprehend** | NLP |
| **Textract** | Extract text from documents |
| **Transcribe / Translate** | Audio and language |
| **Amazon Q** | Generative AI assistant for business/AWS tasks |

---

## 3.8 — Other in-scope categories

### Application integration

- **SNS** — pub/sub notifications (email, SMS, Lambda triggers)
- **SQS** — message queue (decouple components)
- **EventBridge** — event bus (schedule + app events)
- **Step Functions** — orchestrate workflows

**SNS vs SQS:** SNS fans out to many subscribers; SQS holds messages until a consumer processes them.

### Business applications

- **Connect** — contact center
- **SES** — outbound email

### Developer tools

- **CodeBuild** — build code
- **CodePipeline** — CI/CD pipeline
- **X-Ray** — trace/debug distributed apps

### End-user computing

- **WorkSpaces** — virtual desktops (DaaS)
- **AppStream 2.0** — stream apps to browser
- **WorkSpaces Secure Browser** — managed isolated browser

### Frontend / mobile

- **Amplify** — build and host web/mobile frontends

### IoT

- **IoT Core** — connect and manage devices

### Management & governance (frequently tested)

| Service | Job |
|---------|-----|
| **CloudFormation** | IaC templates |
| **CloudWatch** | Monitoring |
| **CloudTrail** | API audit |
| **Config** | Resource configuration compliance |
| **Organizations** | Multiple accounts, consolidated billing |
| **Control Tower** | Multi-account governance landing zone |
| **Service Catalog** | Approved products for users |
| **Systems Manager** | Ops hub (patch, run commands, Parameter Store) |
| **Trusted Advisor** | Recommendations |
| **Health Dashboard** | AWS service health events |
| **Compute Optimizer** | Rightsizing recommendations |

---

## Session 3 — “which service?” drill

1. Static website, global users → **S3** + **CloudFront**
2. Nightly batch reports → **Batch** or **EC2** scheduled; serverless option **Lambda** if short
3. SQL with minimal admin → **RDS** or **Aurora**
4. Shopping cart sessions, millisecond reads → **DynamoDB** + maybe **ElastiCache**
5. Decouple order processing → **SQS**
6. Alert all microservices when order ships → **SNS** or **EventBridge**
7. Company has 50 AWS accounts → **Organizations**
8. Repeatable dev/test/prod environments → **CloudFormation**

**Homework:** Pick 5 in-scope services and write “problem → service” flashcards.
