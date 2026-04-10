# Free Tier Comparison — AWS vs GCP vs Azure

> Last updated: 2026-04-10

## Overview

| Provider | Trial Credits | Credit Expiry | Always-Free Services | 12-Month Free Services |
|---|---|---|---|---|
| AWS | None (new accounts get free tier only) | N/A | ✅ Yes | ✅ Yes |
| GCP | $300 | 90 days | ✅ Yes | ❌ No |
| Azure | $200 | 30 days | ✅ Yes | ✅ Yes |

---

## Always-Free (Permanent, No Expiry)

### Compute

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| GCP | Compute Engine | 1× e2-micro VM/month | us-central1, us-west1, or us-east1 only |
| AWS | Lambda | 1M requests + 400K GB-s/month | Permanent free tier |
| GCP | Cloud Run Functions | 2M invocations + 400K GB-s + 200K vCPU-s/month | Permanent free tier |
| Azure | Azure Functions | 1M requests + 400K GB-s/month | Permanent free tier |
| Azure | App Service | 1 web app (F1 tier, 1 GB storage) | Permanent |
| Azure | AKS | Free cluster management (pay for VMs only) | Permanent |

### Storage

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| GCP | Cloud Storage | 5 GB regional storage/month | Standard class, US regions |
| AWS | S3 | ❌ None always-free | Only 12-month free |

### Databases

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| AWS | DynamoDB | 25 GB storage + 25 WCU + 25 RCU/month | Permanent |
| GCP | Firestore | 1 GB + 50K reads + 20K writes + 20K deletes/day | Permanent |
| Azure | Cosmos DB | 1,000 RU/s + 25 GB storage | Permanent |
| GCP | Cloud Bigtable | ❌ None | — |

### Data & Analytics

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| GCP | BigQuery | 1 TB queries/month + 10 GB storage/month | Permanent |
| GCP | Pub/Sub | 10 GB messages/month | Permanent |
| AWS | CloudWatch | 10 custom metrics, 1M API requests, 5 GB log data | Permanent |

### Messaging / Notifications

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| AWS | SNS | 1M publishes/month | Permanent |
| AWS | SES | 3,000 message charges/month | Permanent (when sending from EC2) |

### Developer Tools

| Provider | Service | Free Allowance | Notes |
|---|---|---|---|
| GCP | Cloud Shell | 5 GB persistent disk | Permanent |
| Azure | DevOps | Up to 5 users + unlimited public projects | Permanent |
| Azure | Active Directory (Entra ID) | Basic user/group management, SSO for 10 apps | Permanent |

---

## 12-Month Free Tier (New Accounts Only)

### AWS 12-Month Free

| Service | Free Allowance |
|---|---|
| EC2 | 750 hours/month t3.micro (Linux or Windows) |
| S3 | 5 GB Standard + 20,000 GET + 2,000 PUT requests |
| RDS | 750 hours/month db.t3.micro (Single-AZ) + 20 GB storage |
| CloudFront | 1 TB egress + 10M HTTP requests/month |
| EBS | 30 GB General Purpose SSD |
| Elastic Load Balancer | 750 hours/month |
| DynamoDB | 25 GB storage + 25 WCU + 25 RCU (also always-free) |

### Azure 12-Month Free

| Service | Free Allowance |
|---|---|
| Virtual Machines (Windows) | 750 hours/month B1s |
| Virtual Machines (Linux) | 750 hours/month B1s |
| Managed Disks | 2× 64 GB P6 Premium SSD |
| Blob Storage | 5 GB LRS Hot tier |
| Azure SQL Database | 250 GB S0 instance |
| Bandwidth | 15 GB outbound/month |

### GCP — No 12-Month Free Tier

GCP does not offer a 12-month free tier for cloud infrastructure. New accounts receive **$300 in credits valid for 90 days**, which can be used on any GCP service. After credits expire, only the Always-Free tier remains.

---

## Free Tier "Gotchas" for Engineers

| Issue | AWS | GCP | Azure |
|---|---|---|---|
| **Egress is never fully free** | 100 GB/mo free (S3 to internet), then charged | 5 GB/mo free (standard egress), then charged | 5 GB/mo free, then charged |
| **Free DB doesn't scale** | RDS db.t3.micro (1 GB RAM) — limited | No free Cloud SQL | Azure SQL S0 = shared resources |
| **Monitoring costs** | CloudWatch free tier is limited; logs ingestion charges apply | Stackdriver/Cloud Monitoring has limits | Azure Monitor Log Analytics charges per GB ingested |
| **Kubernetes control plane** | EKS: **$0.10/hr** (not free!) | GKE: **$0.10/hr** per cluster (Autopilot, not free) | AKS: **Free** control plane |
| **Free credits cannot be combined** | N/A | $300 credit is a one-time grant | $200 credit is a one-time grant |
| **S3 free tier vs GCS free tier** | 5 GB for 12 months only | 5 GB permanently | 5 GB for 12 months only |
| **Lambda cold start billing** | ⚠️ INIT phase billed as of Aug 2025 | Billed from first vCPU instruction | Not separately billed for cold start |

---

## Best Free Tier for Common Use Cases

| Use Case | Best Free Tier | Reason |
|---|---|---|
| **Hobby web app (always on)** | GCP | Free e2-micro VM + 5 GB Cloud Storage permanently |
| **Serverless API** | GCP Cloud Functions | 2M invocations/month vs 1M for AWS/Azure |
| **NoSQL database** | AWS DynamoDB | 25 GB + 25 WCU + 25 RCU permanently; most generous |
| **Relational database** | Azure SQL / AWS RDS | Both offer 12-month free DB tiers; Azure SQL is more powerful (250 GB) |
| **Big data / analytics** | GCP BigQuery | 1 TB free queries + 10 GB storage/month permanently |
| **Static website (CDN)** | AWS CloudFront | 1 TB egress + 10M requests/month for 12 months |
| **Kubernetes** | Azure AKS | Free management plane (only pay for nodes) |
| **New project exploration** | GCP | $300 / 90-day credit; most generous initial grant |
