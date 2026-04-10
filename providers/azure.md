# Azure Pricing Reference

> Last updated: 2026-04-10

## Compute — Azure Virtual Machines (Pay-as-you-go, Linux, East US)

### General Purpose — B-series (burstable)

| Instance | vCPU | RAM | $/hr | $/mo (730 hr) |
|---|---|---|---|---|
| B1ls | 1 | 0.5 GB | $0.0052 | $3.80 |
| B1s | 1 | 1 GB | $0.0104 | $7.59 |
| B2ats v2 | 2 | 1 GB | $0.0090 | $6.57 |
| B2s | 2 | 4 GB | $0.0416 | $30.37 |
| B4ms | 4 | 16 GB | $0.1660 | $121.18 |

### General Purpose — D-series (balanced)

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| D2s v5 | 2 | 8 GB | $0.0960 | $70.08 |
| D4s v5 | 4 | 16 GB | $0.1920 | $140.16 |
| D8s v5 | 8 | 32 GB | $0.3840 | $280.32 |
| D2as v5 (AMD) | 2 | 8 GB | $0.0860 | $62.78 |
| D4as v5 (AMD) | 4 | 16 GB | $0.1720 | $125.56 |

> AMD-based D-series (Dasv5 / Dadsv7) run on AMD EPYC™ 9005 (Turin) processors at up to 4.5 GHz.

### Memory Optimized — E-series

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| E2s v5 | 2 | 16 GB | $0.1260 | $91.98 |
| E4s v5 | 4 | 32 GB | $0.2520 | $183.96 |
| E8s v5 | 8 | 64 GB | $0.5040 | $367.92 |

### Savings / Commitment Options

| Model | Savings vs Pay-as-you-go |
|---|---|
| 1-yr Reserved Instance | ~36–45% |
| 3-yr Reserved Instance | up to ~72% |
| Azure Savings Plan for Compute (1-yr) | ~11–65% |
| Azure Spot VMs | up to ~85% (interruptible) |
| Azure Hybrid Benefit (existing Windows/Linux licenses) | up to ~49% on Windows VMs |

> ⚠️ **Effective November 1, 2025**: Microsoft eliminated volume-based EA tier discounts (Levels B–D) for Online/Cloud Services. All customers now pay Level A (list) pricing regardless of volume. Impact: **+6–12%** for former Level D enterprise customers.

---

## Serverless — Azure Functions

### Consumption Plan (pay-as-you-go)

| Component | Price |
|---|---|
| Execution time | $0.000016 / GB-second |
| Requests | $0.20 / million |
| Free grant (permanent) | 400,000 GB-s + 1M requests/month |
| Min execution | 100 ms, 128 MB |
| Max memory | 1,536 MB |

### Flex Consumption Plan (recommended for new apps)

- Per-instance billing with configurable concurrency
- Supports virtual network connectivity + faster cold starts
- Always-ready instances billed at a lower baseline rate
- Recommended over Linux Consumption plan for most new workloads

> ⚠️ Azure Functions on **Linux in Consumption plan** is being retired on **September 30, 2028**. Migrate to Flex Consumption or Premium plan.

### Premium Plan (EP instances)

| Instance | vCPU | RAM | $/hr (core-seconds) |
|---|---|---|---|
| EP1 | 1 | 3.5 GB | Based on allocated core-seconds |
| EP2 | 2 | 7 GB | Based on allocated core-seconds |
| EP3 | 4 | 14 GB | Based on allocated core-seconds |

- At least 1 instance always warm (minimum monthly cost)
- No per-execution charge; billed on provisioned core-seconds
- Supports VNet, longer runtimes, no cold starts

---

## Storage — Azure Blob Storage (LRS, East US)

### Block Blob Access Tiers (GPv2 accounts)

| Tier | $/GB-mo | Min Duration | Retrieval Fee | Use Case |
|---|---|---|---|---|
| Hot | $0.018 | None | None | Frequently accessed |
| Cool | $0.010 | 30 days | $0.01/GB | Infrequent (once/mo) |
| Cold | $0.0045 | 90 days | $0.02/GB | Rare access (1–2×/yr) |
| Archive | $0.00099 | 180 days | $0.022/GB (standard rehydration) | Long-term archival |
| Premium Block Blob | $0.15 | None | None | High-transaction HPC / analytics |

> ⚠️ **March 3, 2026**: New GPv1 storage account creation blocked via Azure portal and ARM API.  
> ⚠️ **October 13, 2026**: Full GPv1 retirement — all remaining accounts auto-migrated to GPv2. Migration may change billing (tiered pricing, per-operation rates differ).

### Azure Files (provisioned model, LRS, East US)

| Tier | $/GiB-mo | Use Case |
|---|---|---|
| Hot | $0.0287 | Frequent access, general workloads |
| Cool | $0.0228 | Infrequent access |
| Transaction Optimized | $0.0600 | High-transaction workloads |

### Data Transfer (Blob / General)

| Transfer | Cost |
|---|---|
| Ingress (all) | Free |
| Egress to Internet (first 5 GB/mo) | Free |
| Egress to Internet | $0.087/GB (up to 10 TB) |
| Egress between Azure regions | $0.02/GB |
| Egress within same region | Free |

---

## Databases

### Azure SQL Database (General Purpose, East US, on-demand)

| vCores | $/hr | $/mo |
|---|---|---|
| 2 vCores | $0.3624 | $264.55 |
| 4 vCores | $0.7248 | $529.10 |
| 8 vCores | $1.4496 | $1,058.21 |

Storage: $0.115/GB-mo. Serverless tier available (auto-pause, per-vCore-second billing).

### Azure Database for PostgreSQL — Flexible Server (East US, on-demand)

| Tier | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| Burstable B1ms | 1 | 2 GB | $0.021 | $15.33 |
| General Purpose D2s v3 | 2 | 8 GB | $0.170 | $124.10 |
| General Purpose D4s v3 | 4 | 16 GB | $0.340 | $248.20 |
| Memory Optimized E4s v3 | 4 | 32 GB | $0.452 | $330.13 |

Storage: $0.115/GB-mo (Premium SSD). Backups: $0.095/GB-mo.

### Azure Cosmos DB

| Mode | Write | Read |
|---|---|---|
| Serverless | $0.282 / million RUs | Included |
| Provisioned (manual) | $0.008/RU-hr (100 RU/s = $0.008/hr) | Included |
| Autoscale | $0.012/RU-hr at peak | Included |

Storage: $0.25/GB-mo.

### Azure Cache for Redis

| Tier | Capacity | $/hr | $/mo |
|---|---|---|---|
| Basic C0 | 250 MB | $0.022 | $16.06 |
| Standard C1 | 1 GB | $0.093 | $67.89 |
| Premium P1 | 6 GB | $0.554 | $404.42 |

---

## CDN — Azure Front Door / CDN

### Azure CDN (from Microsoft)

| Transfer Zone | $/GB (0–10 TB) | $/GB (10–50 TB) |
|---|---|---|
| North America / Europe | $0.081 | $0.075 |
| Asia Pacific | $0.120 | $0.110 |
| South America | $0.167 | $0.155 |

### Azure Front Door (Standard)

- $35/month per profile + $0.009/GB (first 10 TB) + $0.015/10K requests

---

## Free Tier

### Always Free (no expiry)

| Service | Free Allowance |
|---|---|
| Azure Functions | 1M requests + 400,000 GB-s/month |
| Cosmos DB | 1,000 RU/s + 25 GB storage |
| App Service | 1 web app (F1 tier) with 1 GB storage |
| Azure DevOps | 5 users free + unlimited public projects |
| Azure Kubernetes Service (AKS) | Free cluster management (pay for VMs) |
| Azure Active Directory | Basic features for unlimited users |

### 12-Month Free (new accounts)

| Service | Free Allowance |
|---|---|
| Virtual Machines (Windows) | 750 hours B1s/month |
| Virtual Machines (Linux) | 750 hours B1s/month |
| Managed Disks | 64 GB P6 SSD × 2 |
| Blob Storage (LRS Hot) | 5 GB |
| SQL Database | 250 GB S0 instance |
| Azure Kubernetes Service | 10,000 API server calls/day |
| Bandwidth | 15 GB outbound |

New accounts also receive **$200 in free credits** (30-day expiry).

---

## Upcoming Changes

### July 1, 2026 — Microsoft 365 Commercial Pricing Increase
Announced December 4, 2025:
- **Microsoft 365 E3**: $36.00 → **$39.00/user/mo** (+8%)
- **Microsoft 365 E5**: $57.00 → **$60.00/user/mo** (+5%)
- **Office 365 E3**: $23.00 → **$26.00/user/mo** (+13%)
- **Microsoft 365 Business Basic**: $6.00 → **$7.00/user/mo** (+16%)
- **Microsoft 365 Business Standard**: $12.50 → **$14.00/user/mo** (+12%)
- **Microsoft 365 Business Premium**: unchanged at $22.00/user/mo
- Reason: Bundling of Copilot Chat, Defender for Office P1, expanded Intune features, +50 GB mailbox storage
- Applies to new and renewing customers globally

### October 13, 2026 — Azure GPv1 Storage Account Retirement
- All remaining GPv1 accounts auto-migrated to GPv2
- May result in billing changes (tiered pricing, new operation rates)
