# Changelog

> Pricing changes tracked by the Cloud Pricing Tracker agent. Newest entries first.

---

## 2026-04-12

### ✅ AWS: EC2 Capacity Blocks — Next Review Rescheduled to July 2026
- April 2026 pricing review passed with **no published rate change** for p5e / p5en H200 instances
- AWS pricing page now states: next review scheduled for **July 2026**
- Rates remain: p5e.48xlarge **$39.80/hr**, p5en.48xlarge **$41.61/hr** (most regions)
- New **P6e (u-p6e-gb200x72 UltraServer)** pricing published: **$761.904/hr** (72× NVIDIA B200, Dallas Local Zone); per-accelerator: **$10.582/hr**
- P6e half-server (36× B200, u-p6e-gb200x36): **$380.952/hr**

### 🆕 AWS: CloudFront Flat-Rate Plans — New Capabilities (March 24, 2026)
- Hundreds of thousands of customers adopted plans since November 2025 launch
- Expanded feature support for existing distribution configurations (previously blocked some migrations)
- Overage handling clarified: first spike up to 3× monthly allowance is accommodated; no overage charges for most customers
- Plans remain: **Free ($0)**, **Pro ($15/mo)**, **Business ($200/mo)**, **Premium ($1,000/mo)**

### 🆕 Azure: Savings Plan for Databases — Generally Available (March 18, 2026)
- Announced at SQLCon / FabCon 2026
- Spend-based, **1-year commitment** (no 3-year term for databases)
- Savings automatically applied to highest-discount eligible usage first
- Up to **35% savings** vs. pay-as-you-go on eligible services
- Eligible services and discounts (1-year):
  | Service | Savings Plan Discount |
  |---|---|
  | Azure SQL Database (Provisioned) | 20% |
  | Azure SQL Database (Serverless) | 35% |
  | Azure Database for PostgreSQL (Flexible) | 20% |
  | Azure Database for MySQL | 20% |
  | Azure Cosmos DB | 12% |
  | Azure DocumentDB | 20% |
  | Azure DB Migration Service | 35% |
  | SQL on Azure VMs / Arc-enabled SQL Server | 0% (count toward commitment but no discount) |
- Cross-service, cross-region flexibility — unlike per-resource reservations
- Scoped to subscription, resource group, management group, or entire account
- Monthly or upfront payment at no cost difference; auto-renewal available

### ✅ GCP: BigQuery + Cloud Storage Multi-Region Data Transfer Billing Change (February 1, 2026)
- Effective **February 1, 2026**: BigQuery jobs now charged for Cloud Storage **multi-region data transfer fees**
- Triggered when a BigQuery job reads from a multi-region Cloud Storage bucket located in a different continent
- Affected SKUs: `990F-BF38-8D3C` (Asia), `D46A-868A-BBF7` (Europe), `3C8A-99C5-F47B` (Northern America)
- Mitigation: co-locate Cloud Storage buckets with BigQuery datasets using bucket relocation

---

## 2026-04-10

### 🆕 New Files Created
- `providers/azure.md` — Full Azure pricing reference added (compute, serverless, storage, databases, CDN, free tier)
- `comparisons/compute.md` — Side-by-side vCPU/RAM/hour pricing for AWS, GCP, Azure
- `comparisons/serverless.md` — Lambda vs Cloud Run Functions vs Azure Functions
- `comparisons/storage.md` — S3 vs GCS vs Azure Blob tiers, egress, operations
- `comparisons/databases.md` — Managed Postgres, Redis, DynamoDB equivalents
- `comparisons/free-tiers.md` — Full free tier breakdown with "gotchas" for engineers

### ✅ GCP: A3 Ultra GPU price increase detail added to providers/gcp.md
- Effective **May 1, 2026** (announced Jan 27, 2026)
- A3 Ultra (8× NVIDIA H200) list price increases in Europe and Asia regions
- US region pricing (us-central1: ~$86.76/hr on-demand) unchanged
- CUD pricing increases proportionally in affected regions

---

## Previously Tracked (Pre-2026-04-10)

### 2026-03-02 — GCP: GKE Backup Pricing Restructure *(effective date)*
- Management fee changed: per-Pod ($1.00/pod-mo) → per-Namespace (**$9.00/namespace-mo**)
- Backup storage: $0.028 → **$0.045/GiB-mo**

### 2026-01-27 — GCP: CDN Interconnect & Peering Price Increase Announced
- Effective **May 1, 2026**
- CDN Interconnect egress (North America): $0.04 → **$0.08/GiB** (+100%)
- CDN Interconnect egress (Europe): $0.05 → **$0.08/GiB** (+60%)
- CDN Interconnect egress (Asia): $0.06 → **$0.085/GiB** (+42%)
- Also affects Direct Peering and Carrier Peering
- Fixed-price contracts unaffected until renewal

### 2026-01-04 — AWS: EC2 Capacity Blocks for ML Price Increase *(effective date)*
- p5e.48xlarge (8× H200) Capacity Block: $34.61 → **$39.80/hr** (~15% increase)
- p5en.48xlarge (8× H200) Capacity Block: $36.18 → **$41.61/hr** (~15% increase)
- US West (N. California): $43.26 → **$49.75/hr**
- On-Demand and Savings Plans rates for these instances **unchanged**
- Next Capacity Blocks pricing review: **April 2026** (now passed; no update found as of 2026-04-10)
- Historical: AWS had cut GPU instance prices by up to 45% in mid-2025 (On-Demand/Savings Plans)

### 2025-12-04 — Azure: Microsoft 365 Commercial Pricing Increases Announced
- Effective **July 1, 2026** for new and renewing customers
- Microsoft 365 E3: $36.00 → **$39.00/user/mo** (+8%)
- Microsoft 365 E5: $57.00 → **$60.00/user/mo** (+5%)
- Office 365 E3: $23.00 → **$26.00/user/mo** (+13%)
- Microsoft 365 Business Basic: $6.00 → **$7.00/user/mo** (+16%)
- Microsoft 365 Business Standard: $12.50 → **$14.00/user/mo** (+12%)
- Microsoft 365 Business Premium: **unchanged** at $22.00/user/mo
- Bundles: Copilot Chat, Defender for Office P1, advanced Intune, +50 GB mailbox storage

### 2025-11-18 — AWS: CloudFront Flat-Rate Plans Launched
- Free tier: $0/month
- Pro: **$15/month** (WAF + Route 53 + CloudWatch + serverless edge + S3 credits)
- Business: **$200/month**
- Premium: **$1,000/month**
- No overage charges; includes DDoS protection
- Available alongside pay-as-you-go per-distribution pricing

### 2025-11-01 — Azure: EA Volume Tier Discounts Eliminated *(effective date)*
- Microsoft removed Level B, C, D volume discounts for Online Services under EA and MPSA
- All customers now pay Level A (list) pricing regardless of purchase volume
- Impact: **+6–12%** effective cost increase for former Level D enterprise customers
- Unified Support bills also increase (calculated as % of total Microsoft spend)

### 2025-08-01 — AWS: Lambda Cold Start (INIT Phase) Now Billed *(effective date)*
- Lambda INIT (initialization/cold start) phase now billed as compute time
- Previously, cold start initialization was mostly free
- Impact largest for heavy runtimes: Java, C#/.NET, Ruby
- New Lambda Managed Instances feature also launched in 2025/2026

### 2025-11-01 — AWS: CloudWatch Logs Ingestion Tiered Pricing
- Tiered pricing introduced for CloudWatch Logs ingestion
- $0.50/GB (first tier) down to $0.05/GB at high volume
