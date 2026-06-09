# Azure Pricing Reference

> Last updated: 2026-06-09

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

### GPU Accelerated — NCv6 Series (NVIDIA RTX PRO 6000 Blackwell Server Edition, GA June 2026) 🆕

Powered by **NVIDIA RTX PRO 6000 Blackwell Server Edition** (96 GB GDDR7 VRAM) with Intel Xeon Granite Rapids CPUs (up to 4.2 GHz). Three sizing categories spanning general purpose, compute-optimized, and memory-optimized workloads. Purpose-built for converged AI inference and visual computing (digital twins, LLM inference, agentic workflows, rendering).

| Instance | vCPU | RAM | GPUs | GPU Mem | $/hr (On-Demand) | Notes |
|---|---|---|---|---|---|---|
| NCdsxlRTX6kv6 | 32 | 128 GB | 1 | 96 GB | **$1.44** | General purpose sizing |
| NCldsxlRTX6kv6 | 64 | 128 GB | 1 | 96 GB | **$2.44** | Compute-optimized sizing |
| (larger sizes) | up to 320 | up to 1,280 GB | up to N | — | See Azure portal | Memory-optimized sizing |

> 🆕 **June 2026 (GA)**: **NCv6 series** (NC RTX PRO 6000 BSE v6) moves from Public Preview (announced Nov 2025) to **General Availability**.  
> Supports: Premium SSD v2, Ultra Disk, Azure Accelerated Networking up to 200 Gbps.  
> Up to 2 TB local temp storage.  
> Available: select regions — check [Azure VM sizes overview](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/gpu-accelerated/nc-rtxpro6000-bse-v6-series) for region availability.  
> Pricing at ~$1.44/hr (32 vCPU, 1 GPU, 128 GB) makes it competitive with AWS G7e (~$3.36/hr for comparable 1-GPU 96 GB VRAM instance) and GCP G4 (~$4.50/hr for full g4-standard-48).

---

### Savings / Commitment Options

| Model | Savings vs Pay-as-you-go |
|---|---|
| 1-yr Reserved Instance | ~36–45% |
| 3-yr Reserved Instance | up to ~72% |
| Azure Savings Plan for Compute (1-yr) | ~11–65% |
| Azure Savings Plan for Databases (1-yr) | up to **35%** (announced March 2026) 🆕 |
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
> ⚠️ **April 17, 2026**: Azure Functions **runtime v3** on **Linux Consumption** will **stop running September 30, 2026** (enforcement of the December 2022 runtime v3 EOL). After that date, affected functions will not start or process executions. **Migrate to runtime v4 now** — and consider migrating the plan to Flex Consumption (which also supports runtime v4 and is the go-forward recommendation).
> ⚠️ **Azure Functions runtime v1.x** end-of-support: **September 2026**. Functions on runtime 1.x will stop being supported; migrate to v4.
> ⚠️ **Azure Functions in-process .NET model** end-of-support: **November 2026**. Migrate to the **isolated worker model** (the default for new .NET apps). In-process model will not receive updates after this date. Migration tooling and automated compatibility checks are available.

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

| Tier | $/GB-mo | Min Duration | Retrieval Fee | Min Object Size (billing) | Use Case |
|---|---|---|---|---|---|
| Hot | $0.018 | None | None | None | Frequently accessed |
| Cool | $0.010 | 30 days | $0.01/GB | None | Infrequent (once/mo) |
| Cold | $0.0045 | 90 days | $0.02/GB | None | Rare access (1–2×/yr) |
| Archive | $0.00099 | 180 days | $0.022/GB (standard rehydration) | None | Long-term archival |
| Premium Block Blob | $0.15 | None | None | None | High-transaction HPC / analytics |

> ✅ **June 8, 2026 — PAUSED**: Azure has **paused** the previously announced minimum billable object size of 128 KiB for Cool, Cold, and Archive tiers. The July 1, 2026 effective date has been cancelled. Billing behavior will **not change** for new or existing accounts until a revised approach is announced. (Azure Update ID 559756)  
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

### Azure DocumentDB (MongoDB-compatible) 🆕

Fully managed, open-source, MongoDB-compatible database service (powered by the open-source DocumentDB engine). Distinct from Cosmos DB for MongoDB — vCore-based horizontal scaling model vs. RU-based Cosmos DB.

| Tier | Price | Notes |
|---|---|---|
| **Free Tier** 🆕 | **$0** | 32 GB storage, dedicated MongoDB cluster, free for account lifetime |
| M10 (2 vCores, 8 GB) | See [pricing page](https://azure.microsoft.com/en-us/pricing/details/documentdb/) | Entry production tier |
| M20 (4 vCores, 16 GB) | See pricing page | General workloads |
| M30 (8 vCores, 32 GB) | See pricing page | Medium production |

> 🆕 **June 2, 2026**: Azure DocumentDB free tier cluster provisioning is now **near-instant** (seconds, not minutes). Enables ephemeral or agentic workflows to spin up MongoDB-compatible clusters as a low-latency step.  
> **Free tier**: 1 free tier cluster per subscription (lifetime); 32 GB storage; feature and API parity with paid tiers. Paused after 60 days of inactivity. High availability, Entra ID auth, backups, HNSW/DiskANN vector indexes, and diagnostic logging not included on free tier.  
> **Upgrade**: One-click online upgrade to paid tier, data/connection string/network rules intact.  
> **Pricing drop (prior)**: Azure DocumentDB prices dropped 30%+ when the service was rebranded from Cosmos DB for MongoDB vCore. Verify current paid tier rates on the Azure portal, as they have changed significantly.

### Azure Cache for Redis ⚠️ (Retiring)

> ⚠️ **Azure Cache for Redis is being retired.** New instance creation is blocked for **new customers as of April 1, 2026** and for **existing customers as of October 1, 2026**. Full retirement: **September 30, 2028** (Basic/Standard/Premium); **March 31, 2027** (Enterprise/Enterprise Flash). Migrate to **Azure Managed Redis**.

| Tier | Capacity | $/hr | $/mo |
|---|---|---|---|
| Basic C0 | 250 MB | $0.022 | $16.06 |
| Standard C1 | 1 GB | $0.093 | $67.89 |
| Premium P1 | 6 GB | $0.554 | $404.42 |

### Azure Managed Redis 🆕 (Recommended Replacement)

Azure Managed Redis is the go-forward service — built on Redis Enterprise, offering higher performance, zone redundancy by default, active geo-replication, and Redis modules. Reservations available (1-yr and 3-yr).

| SKU | Memory | vCPUs | Network | HA (2-node) $/mo (approx.) | Notes |
|---|---|---|---|---|---|
| M10 (Memory Optimized) | 12 GB | 2 | Moderate | See Azure portal | High memory-to-CPU ratio |
| M50 (Memory Optimized) | 60 GB | 8 | Moderate | See Azure portal | |
| M100 (Memory Optimized) | 120 GB | 16 | High | See Azure portal | |
| M350 (Memory Optimized) 🆕 | 360 GB | 48 | Highest | See Azure portal | **GA April 2026** |
| B10 (Balanced) | 12 GB | 4 | Moderate | See Azure portal | 1:4 memory-to-vCPU |
| B350 (Balanced) 🆕 | 360 GB | 96 | Highest | See Azure portal | **GA April 2026** |
| X10 (Compute Optimized) | 12 GB | 8 | Moderate | See Azure portal | 1:2 memory-to-vCPU |
| X350 (Compute Optimized) 🆕 | 360 GB | 192 | Highest | See Azure portal | **GA April 2026** |

> 🆕 **April 2026**: M350, B350, and X350 SKUs (350 GB tier) moved to **General Availability**.  
> Up to **99.999% SLA** with geo-replication across 3+ regions with 3+ AZs each.  
> Reservations offer significant savings vs PAYG; see [Azure Managed Redis pricing](https://azure.microsoft.com/en-us/pricing/details/managed-redis/).

### 🆕 Azure Savings Plan for Databases (GA: March 18, 2026)

A new **spend-based, 1-year commitment** pricing option across the entire Azure Databases portfolio. Unlike per-resource reservations, the plan is cross-service and cross-region — savings are applied to the highest-discount eligible usage each hour automatically.

| Service | Savings Plan Discount (1-yr) | Reservation Discount (1-yr, for comparison) |
|---|---|---|
| Azure SQL Database (Provisioned) | 20% | 15–34% (varies by tier) |
| Azure SQL Database (Serverless) | **35%** | N/A |
| Azure SQL Managed Instance | 20% | 15–34% |
| Azure Database for PostgreSQL (Flexible Server) | 20% | 40% |
| Azure Database for MySQL | 20% | 40% |
| Azure Cosmos DB | 12% | 15–34% (sliding scale) |
| Azure DocumentDB | 20% | N/A |
| Azure DB Migration Service | **35%** | N/A |
| SQL on Azure VMs (hourly licenses) | 0% (counts toward commitment) | N/A |
| SQL Server via Azure Arc (hourly licenses) | 0% (counts toward commitment) | N/A |

> ⚠️ **Cosmos DB Serverless** and DTU-based Azure SQL SKUs are **not eligible** for savings plans due to their billing model.  
> Savings plans apply the highest-percentage discount first across all eligible database usage within the hourly commitment.  
> Payment: monthly or upfront (no cost difference). Auto-renewal configurable. 1-year term only (no 3-year option for databases).

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

### September 2026 — Azure Functions Runtime v1.x End of Support
- Runtime v1.x (original .NET in-process model, Node.js 6, etc.) support ends **September 2026**
- After this date, runtime v1.x functions may continue to run but will not receive security updates or support
- **Action required**: Migrate any v1.x function apps to **runtime v4** (isolated worker model for .NET, current Node.js/Python versions)

### September 30, 2026 — Azure Functions Runtime v3 on Linux Consumption: Enforcement
- **Announced April 17, 2026** (Azure ID: 559311)
- Runtime v3 was officially retired on **December 13, 2022** but continued to run
- Enforcement begins September 30, 2026: Function Apps on runtime v3 + Linux Consumption **will stop executing**
- Distinct from the broader Linux Consumption plan retirement (September 30, 2028)
- **Action required before Sep 30, 2026**:
  1. Migrate to **Azure Functions runtime v4**
  2. Optionally (recommended): migrate to **Flex Consumption** plan, which supports v4 and ongoing updates
- Flex Consumption pricing: per-instance billing with configurable concurrency; supports VNet + faster cold starts

### November 2026 — Azure Functions In-Process .NET Model End of Support
- The **.NET in-process model** (where function code runs in the same process as the Azure Functions host) reaches end-of-support **November 2026**
- After this date, in-process .NET function apps will not receive updates or support
- **Action required**: Migrate to the **isolated worker model** — the default for all new .NET function apps (.NET 8+)
- Migration tooling, automated compatibility checks, and version upgrade advisories are available in the Azure portal
- **Note**: Isolated worker model offers better performance isolation, full middleware pipeline support, and .NET dependency injection compatibility

### ~~July 1, 2026 — Azure Blob Storage: Minimum Billable Object Size on Cooler Tiers~~ — **PAUSED**
- **Originally announced April 14, 2026** (Azure Update ID: 559756); **PAUSED June 8, 2026**
- Azure has paused the introduction of a **128 KiB minimum billable object size** for Cool, Cold, and Archive tiers
- Billing behavior will **not change** on July 1, 2026 for new accounts, nor on July 1, 2027 for all accounts — the two-stage rollout has been cancelled
- **No action required**. Azure will announce a revised approach and timeline in a future update
- If you were planning to package small objects or change lifecycle policies in response, hold off until the new timeline is published

### October 1, 2026 — Azure Cache for Redis: New Instance Creation Blocked (All Customers)
- **New customer creation** already blocked since **April 1, 2026**
- **Existing customer creation** blocked starting **October 1, 2026** — no new Cache for Redis instances can be created after this date, regardless of account age
- Enterprise/Enterprise Flash tier creation was also blocked April 1, 2026; those instances will be **auto-migrated** to Azure Managed Redis starting **April 1, 2027**
- Existing Basic/Standard/Premium instances continue operating until **September 30, 2028** (retirement date)
- **Action**: Migrate to **Azure Managed Redis** now — it supports all existing Redis features and offers better performance, zone redundancy, and geo-replication
- New M350, B350, X350 (360 GB) SKUs now GA (April 2026) for large cache workloads

### ⚠️ July 1, 2026 — Azure Reserved VM Instances: Purchases and Renewals Discontinued for Legacy Series
- **Announced May 5, 2026** (Azure ID: 560948)
- Starting **July 1, 2026**, new purchases and renewals will **no longer be available** for Reserved VM Instances (RIs) on the following older VM series:
  - **Av2, Amv2, Bv1** (burstable legacy)
  - **D, Ds, Dv2, Dsv2** (general purpose legacy)
  - **F, Fs, Fsv2** (compute optimized legacy)
  - **G, Gs** (memory/storage optimized legacy)
  - **Ls, Lsv2** (storage optimized legacy)
  - **Dv3, Dsv3, Ev3, Esv3** (1-yr and 3-yr RIs no longer purchasable)
- Existing RIs remain valid through their purchased term — but **auto-renew will not protect you**: RIs on these series that expire after July 1, 2026 cannot be renewed and usage will revert to pay-as-you-go rates.
- **Recommended action**: Review RI expiry dates now, migrate workloads to newer VM series (Dv5, Ev5, etc.) covered by current RIs or Azure Savings Plan for Compute, which does cover these workloads.
- Compute Savings Plans (1-yr and 3-yr) **are not affected** and remain available.

### October 13, 2026 — Azure GPv1 Storage Account Retirement
- All remaining GPv1 accounts auto-migrated to GPv2
- May result in billing changes (tiered pricing, new operation rates)
