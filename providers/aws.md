# AWS Pricing Reference

> Last updated: 2026-04-10

## Compute — Amazon EC2 (On-Demand, Linux, us-east-1)

### General Purpose

| Instance | vCPU | RAM | $/hr | $/mo (730 hr) |
|---|---|---|---|---|
| t3.micro | 2 | 1 GB | $0.0104 | $7.59 |
| t3.small | 2 | 2 GB | $0.0208 | $15.18 |
| t3.medium | 2 | 4 GB | $0.0416 | $30.37 |
| t3.large | 2 | 8 GB | $0.0832 | $60.74 |
| m5.large | 2 | 8 GB | $0.0960 | $70.08 |
| m5.xlarge | 4 | 16 GB | $0.1920 | $140.16 |
| m5.2xlarge | 8 | 32 GB | $0.3840 | $280.32 |
| m7g.xlarge (Graviton3) | 4 | 16 GB | $0.1632 | $119.14 |
| m7g.2xlarge (Graviton3) | 8 | 32 GB | $0.3264 | $238.27 |

### Compute Optimized

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| c5.large | 2 | 4 GB | $0.0850 | $62.05 |
| c5.xlarge | 4 | 8 GB | $0.1700 | $124.10 |
| c5.2xlarge | 8 | 16 GB | $0.3400 | $248.20 |

### Memory Optimized

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| r5.large | 2 | 16 GB | $0.1260 | $91.98 |
| r5.xlarge | 4 | 32 GB | $0.2520 | $183.96 |
| r5.2xlarge | 8 | 64 GB | $0.5040 | $367.92 |

### GPU / ML Instances

| Instance | GPUs | $/hr (On-Demand) | Notes |
|---|---|---|---|
| p3.2xlarge | 1× V100 | $3.06 | Previous gen |
| p4d.24xlarge | 8× A100 | $32.77 | UltraCluster |
| p5.48xlarge | 8× H100 | $98.32 | UltraCluster |
| p5e.48xlarge | 8× H200 | $98.32 (on-demand) | Capacity Block: **$39.80/hr** ⚠️ |
| p5en.48xlarge | 8× H200 | — | Capacity Block: **$41.61/hr** ⚠️ |

> ⚠️ **January 4, 2026**: AWS raised EC2 Capacity Blocks for ML by ~15%.
> p5e.48xlarge Capacity Block rate: $34.61 → **$39.80/hr** (most regions).
> US West (N. California): $43.26 → **$49.75/hr**.
> On-Demand and Savings Plans rates for these instances are **unchanged**.
> Next Capacity Blocks review scheduled: **July 2026**.

### Savings / Commitment Options

| Model | Savings vs On-Demand |
|---|---|
| 1-yr Reserved (no upfront) | ~40% |
| 3-yr Reserved (all upfront) | ~60–62% |
| Compute Savings Plans | up to ~66% |
| Spot Instances | 60–90% (interruptible) |

---

## Serverless — AWS Lambda (us-east-1)

| Component | x86 price | ARM (Graviton2) price |
|---|---|---|
| Requests | $0.20 / million | $0.20 / million |
| Duration | $0.0000166667 / GB-s | $0.0000133334 / GB-s |

- **Free tier (permanent)**: 1 million requests + 400,000 GB-seconds/month
- Minimum billing: 1 ms
- Memory range: 128 MB – 10,240 MB (1 MB increments)
- ARM is ~20% cheaper per GB-second
- **August 2025 change**: INIT (cold start initialization) phase is now billed. Previously it was mostly free.
- Ephemeral storage: first 512 MB free; additional at $0.0000000309 /GB-s
- CloudWatch Logs (ingestion): $0.50/GB down to $0.05/GB at high volume (tiered pricing introduced late 2025)

### Lambda Managed Instances (new in 2026)

Allows running Lambda on dedicated EC2 instance types (e.g., m7g.xlarge) for high-throughput workloads:
- Request charges: $0.20/million
- Compute management fee: +15% on top of EC2 on-demand price
- Normal EC2 instance charges apply (Savings Plans & RIs eligible)

---

## Storage — Amazon S3 (us-east-1)

### Storage Tiers

| Tier | $/GB-mo (first 50 TB) | $/GB-mo (next 450 TB) | $/GB-mo (>500 TB) | Min Duration |
|---|---|---|---|---|
| S3 Standard | $0.023 | $0.022 | $0.021 | None |
| S3 Intelligent-Tiering | $0.023 (frequent) / $0.0125 (infrequent) | — | — | None |
| S3 Standard-IA | $0.0125 | — | — | 30 days |
| S3 One Zone-IA | $0.010 | — | — | 30 days |
| S3 Glacier Instant Retrieval | $0.004 | — | — | 90 days |
| S3 Glacier Flexible Retrieval | $0.0036 | — | — | 90 days |
| S3 Glacier Deep Archive | $0.00099 | — | — | 180 days |

### Data Transfer

| Transfer | Cost |
|---|---|
| Ingress (all) | Free |
| Egress to Internet (first 100 GB/mo) | Free |
| Egress to Internet (next 9.9 TB) | $0.09/GB |
| Egress to Internet (10–40 TB) | $0.085/GB |
| Egress to Internet (>40 TB) | $0.070/GB |
| Egress to another AWS region | $0.02/GB |
| Egress within same region | Free |

### CDN — Amazon CloudFront (flat-rate plans, launched Nov 2025)

| Plan | $/mo | Includes |
|---|---|---|
| Free | $0 | Limited CloudFront + WAF + DDoS baseline |
| Pro | $15 | More capacity + WAF + Route 53 + CloudWatch + serverless edge |
| Business | $200 | Higher limits, S3 storage credits |
| Premium | $1,000 | Highest limits, full feature set |

Also available as pay-as-you-go per distribution. Flat-rate plans have **no overage charges**.

---

## Databases

### Amazon RDS (PostgreSQL, us-east-1, single-AZ, on-demand)

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| db.t3.micro | 2 | 1 GB | $0.018 | $13.14 |
| db.t3.medium | 2 | 4 GB | $0.068 | $49.64 |
| db.m5.large | 2 | 8 GB | $0.171 | $124.83 |
| db.m5.xlarge | 4 | 16 GB | $0.342 | $249.66 |
| db.r5.large | 2 | 16 GB | $0.240 | $175.20 |
| db.r5.xlarge | 4 | 32 GB | $0.480 | $350.40 |

Storage: $0.115/GB-mo (gp2), $0.125/GB-mo (gp3). I/O: $0.02/million I/O (gp2).

### Amazon Aurora (PostgreSQL-compatible, us-east-1)

| Instance | vCPU | RAM | $/hr |
|---|---|---|---|
| db.r4.2xlarge | 8 | 61 GB | $1.16 |
| db.r5.2xlarge | 8 | 64 GB | $1.20 |

Storage: $0.10/GB-mo. I/O: $0.20/million requests.

### Amazon DynamoDB (us-east-1)

| Capacity Mode | Write | Read |
|---|---|---|
| On-Demand | $1.25/million write request units | $0.25/million read request units |
| Provisioned | $0.00065/WCU-hr | $0.00013/RCU-hr |

Storage: $0.25/GB-mo (first 25 GB free).

### Amazon ElastiCache (Redis, on-demand, us-east-1)

| Node | vCPU | RAM | $/hr |
|---|---|---|---|
| cache.t3.micro | 2 | 0.5 GB | $0.017 |
| cache.m5.large | 2 | 6.38 GB | $0.136 |
| cache.r6g.large | 2 | 13.07 GB | $0.171 |

---

## Free Tier

### Always Free (no expiry)

| Service | Free allowance |
|---|---|
| Lambda | 1M requests + 400,000 GB-s / month |
| DynamoDB | 25 GB storage + 25 WCU + 25 RCU / month |
| CloudWatch | 10 custom metrics, 1M API requests, 5 GB log data |
| SNS | 1M publishes |
| SES | 3,000 message charges free / month |

### 12-Month Free (new accounts)

| Service | Free allowance |
|---|---|
| EC2 | 750 hours/mo t3.micro (Linux or Windows) |
| S3 | 5 GB Standard + 20,000 GET + 2,000 PUT requests |
| RDS | 750 hours db.t3.micro (Single-AZ) + 20 GB storage |
| CloudFront | 1 TB egress + 10M HTTP requests/mo |
| EBS | 30 GB General Purpose SSD |
