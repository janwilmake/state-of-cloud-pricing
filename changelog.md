# Changelog

> Pricing changes tracked by the Cloud Pricing Tracker agent. Newest entries first.

---

## 2026-05-18

### ⚠️ Azure Cache for Redis: New Instance Creation Blocked for All Customers — October 1, 2026
- **Effective October 1, 2026**: New Azure Cache for Redis instances (Basic, Standard, Premium) **cannot be created** by any customer — including existing customers. (New customer creation was already blocked April 1, 2026.)
- Enterprise and Enterprise Flash tier creation was blocked April 1, 2026; auto-migration to Azure Managed Redis begins April 1, 2027; Enterprise retires March 31, 2027.
- All existing Basic/Standard/Premium instances continue operating until full retirement on **September 30, 2028**. Instances will be disabled starting October 1, 2028 if not migrated.
- **Azure Managed Redis** is the recommended replacement — built on Redis Enterprise software, offering zone redundancy by default, active geo-replication, Redis modules, and up to 99.999% SLA.
- Reservations (1-yr and 3-yr) available for Azure Managed Redis since November 2025.
- Updated: `providers/azure.md` (Redis section, Upcoming Changes), `comparisons/databases.md` (Redis table + warning)

### 🆕 Azure Managed Redis: M350, B350, X350 SKUs — Generally Available (April 2026)
- **Memory Optimized M350** (360 GB, 48 vCPUs), **Balanced B350** (360 GB, 96 vCPUs), and **Compute Optimized X350** (360 GB, 192 vCPUs) SKUs moved from Preview to **General Availability** in April 2026.
- These are the largest generally available SKUs in the Azure Managed Redis lineup (M500, M700, M1000, M1500, M2000 remain in Preview).
- Targeted at large in-memory analytics, large caches, and enterprise workloads requiring >235 GB RAM.
- Updated: `providers/azure.md` (Azure Managed Redis table)

### ✅ No new AWS pricing changes found (as of 2026-05-18)
- EC2 Capacity Blocks next review: July 2026 — no new rate changes since the p5en.48xlarge US increase on ~2026-05-16
- Lambda, S3, RDS, Aurora, EKS pricing all unchanged
- Database Savings Plans (expanded to OpenSearch + Neptune in March 2026) unchanged
- No new instance type launches or pricing announcements detected

### ✅ No new GCP pricing changes found (as of 2026-05-18)
- All May 1, 2026 changes (CDN Interconnect/Peering, A3 Ultra EU/Asia) remain in effect — no further changes
- G4 VM family, N4A, TPU v7 Ironwood pricing unchanged
- Cloud SQL, BigQuery, Cloud Run pricing unchanged

### ✅ No new Azure IaaS/PaaS compute/storage pricing changes found (as of 2026-05-18)
- Azure Blob Storage 128 KiB minimum object size: still upcoming July 1, 2026 (new accounts)
- Azure Functions v3 Linux Consumption enforcement: still upcoming September 30, 2026
- Microsoft 365 commercial pricing increase: still upcoming July 1, 2026 (as previously tracked)
- Azure GPv1 retirement: still upcoming October 13, 2026

---

## 2026-05-16

### ⚠️ AWS: EC2 Capacity Blocks — p5en.48xlarge US Region Price Increase (~+10%)
- **Effective: ~mid-May 2026** (detected from AWS pricing page last updated 2026-05-13; prior to the July 2026 review cycle)
- **p5en.48xlarge** (8× NVIDIA H200) Capacity Block rate in **US regions** increased:
  - US East (Ohio), US East (N. Virginia), US West (N. California), US West (Oregon): **$41.612 → $45.768/hr** (~+10%)
  - EU/Asia regions (Stockholm, London, Spain, Jakarta, Mumbai, Tokyo, Seoul) **unchanged at $41.612/hr**
- **p5e.48xlarge rates are unchanged**: $39.799/hr (most regions), $49.749/hr (US West N. California)
- AWS pricing page still states next scheduled review: **July 2026**
- This is the second p5en US rate increase in 2026 — rates in US regions are now 26% higher than EU/Asia for the same instance type
- On-Demand and Savings Plans pricing for these instances remain unchanged
- Updated: `providers/aws.md` (GPU table), `comparisons/compute.md`

### ✅ No new GCP pricing changes found (as of 2026-05-16)
- GCP CDN Interconnect/Peering increases (May 1, 2026) confirmed in effect — no new announcements
- G4 VM family, N4A, A3 Ultra pricing all unchanged
- No new BigQuery, Cloud SQL, Cloud Run, or Cloud Storage pricing announcements

### ✅ No new Azure pricing changes found (as of 2026-05-16)
- All previously tracked upcoming changes remain on schedule:
  - July 1, 2026: Azure Blob Storage min 128 KiB object size (new accounts)
  - July 1, 2026: Microsoft 365 commercial price increases
  - Sep 30, 2026: Azure Functions runtime v3 on Linux Consumption enforcement
  - Oct 13, 2026: Azure GPv1 storage account retirement
- No new VM, Functions, SQL, CDN, or storage pricing announcements found

---

## 2026-05-14

### 🆕 AWS: EC2 Capacity Blocks — P6-B300 (8× NVIDIA B300) Pricing Published
- **p6-b300.48xlarge** Capacity Block: **$93.60/hr per instance** ($11.70/accelerator) for 8× NVIDIA B300 GPUs
- Available regions: **US West (Oregon)** and **US East (N. Virginia)**
- B300 is the successor to B200 in NVIDIA's Blackwell architecture lineup — ~14% premium over p6-b200.48xlarge ($82.368/hr)
- Still only available via Capacity Blocks (no On-Demand or Savings Plans published yet)
- OS charges additional: $0 (Linux), $1.8432/hr (RHEL), $3.8592/hr (RHEL with HA)
- Next Capacity Blocks pricing review: **July 2026**
- Updated: `providers/aws.md` (GPU table), `comparisons/compute.md`

### 🆕 GCP: G4 VM Family (NVIDIA RTX PRO 6000 Blackwell) — GA / Pricing Published
- New **G4** accelerator-optimized VM family featuring **NVIDIA RTX PRO 6000 Blackwell** GPUs (96 GB GDDR7, 1.6 TB/s bandwidth, FP4/FP6 support)
- Can serve 70B+ parameter models in a single g4-standard-48 instance (1 GPU)

| Machine Type | GPUs | vCPU | RAM | $/hr (On-Demand) | $/hr (Spot) |
|---|---|---|---|---|---|
| g4-standard-48 | 1× RTX PRO 6000 | 48 | 180 GB | $4.50 | $2.25 |
| g4-standard-96 | 2× RTX PRO 6000 | 96 | 360 GB | $9.00 | $4.50 |
| g4-standard-192 | 4× RTX PRO 6000 | 192 | 720 GB | $18.00 | $9.00 |
| g4-standard-384 | 8× RTX PRO 6000 | 384 | 1,440 GB | $36.00 | $18.00 |

- 1-yr CUD: ~20% off; 3-yr CUD: ~46% off
- Available: us-central1, us-west1, europe-west4 (expanding)
- **Cloud Run GPU pricing** (no reservation required): **$0.00036522/second** (no zonal redundancy) ≈ $1.31/hr; **$0.00056913/second** (with zonal redundancy) ≈ $2.05/hr
  - Preview regions: us-central1, europe-west4, limited in asia-south2, asia-southeast1
  - Requires min 20 vCPU + 80 GiB RAM per Cloud Run instance
  - RTX PRO 6000 on Cloud Run was announced February 3, 2026; G4 VMs highlighted at Cloud Next '26 (April 22, 2026)
- Updated: `providers/gcp.md` (new G4 section, Cloud Run GPU pricing), `comparisons/compute.md`

### ✅ No new Azure IaaS/PaaS pricing changes found (as of 2026-05-14)
- Azure Kubernetes Service v1.32 reached end of standard support April 30, 2026 (lifecycle event, not a pricing change)
- Azure Linux 2.0 node image removal (March 31, 2026) already passed — no pricing impact
- All previously tracked upcoming changes (Blob Storage 128 KiB minimum, Functions v3 enforcement, GPv1 retirement, M365 increases) remain on schedule
- No new VM, Functions, SQL, CDN, or storage pricing announcements found

---

## 2026-05-12

### ⚠️ Azure Blob Storage: Minimum Billable Object Size for Cool/Cold/Archive — **Upcoming** (Effective July 1, 2026 for new accounts; July 1, 2027 for all)
- **Announced April 14, 2026** (Azure Update ID: 559756)
- Objects stored in **Cool, Cold, or Archive** tiers that are **smaller than 128 KiB** will be billed as **128 KiB** objects
- **Hot tier is not affected** — no minimum object size applies
- Rollout is phased:
  - **July 1, 2026**: New storage accounts created on or after this date are subject to the rule
  - **July 1, 2027**: Rule extends to all existing storage accounts
- Billing uses the existing capacity meters; no change to transaction billing
- New Azure Portal metric blob types: `BlockBlobSmall` and `Azure Data Lake Storage Small` (breaking change for dashboards/alerts filtering on `BlockBlob` type)
- **Impact example**: 1,000 × 1 KiB Archive objects → billed as 1,000 × 128 KiB = 128 MB (vs 1 MB actual storage; 128× cost inflation for micro-objects)
- **Mitigation**: Pack small objects into larger archives before tiering; use smart tier to keep sub-128 KiB objects in Hot; review automation that relies on `BlockBlob` metric type
- Updated: `providers/azure.md` (Blob Storage tier table + Upcoming Changes), `comparisons/storage.md` (new row + Key Differences table)

### 🆕 AWS: EC2 C8in + C8ib — Generally Available (April 16, 2026)
- **C8in** — Compute-optimized, 6th-gen Intel Xeon Scalable + 6th-gen Nitro cards
  - **600 Gbps network bandwidth** — highest of any enhanced networking EC2 instance
  - Up to 384 vCPUs; up to 43% higher performance vs C6in
  - Available: US East (N. Virginia), US West (Oregon), Asia Pacific (Tokyo), Europe (Spain)
  - Pricing: c8in.large $0.1361/hr, c8in.xlarge $0.2722/hr, c8in.2xlarge $0.5443/hr (us-east-1)
- **C8ib** — Same CPU; optimized for storage I/O
  - **300 Gbps EBS bandwidth** — highest of any non-accelerated compute instance
  - Ideal for commercial databases and high-performance file systems
  - Available: US East (N. Virginia), US West (Oregon)
  - Pricing: c8ib.xlarge $0.2722/hr (us-east-1)
- Both available via Savings Plans, On-Demand, and Spot
- Updated: `providers/aws.md`, `comparisons/compute.md` (new Network/Storage-Optimized section)

### 🆕 AWS: EC2 C8ine + M8ine — Generally Available (April 27, 2026)
- **C8ine** — Compute-optimized network-intensive instances (6th-gen Intel Xeon Scalable + Nitro)
  - 2.5× higher packet performance per vCPU vs C6in
  - 2× higher Internet gateway network throughput vs C6in
  - Available: US East (N. Virginia), US West (Oregon), Asia Pacific (Tokyo)
- **M8ine** — General purpose network-intensive instances (same silicon)
  - Same packet performance improvements vs M6in
  - Available: US East (N. Virginia), US West (Oregon)
- Both designed for: security/network virtual appliances, virtual firewalls, load balancers, Telco 5G UPF workloads
- Available via Savings Plans and On-Demand
- Updated: `providers/aws.md`, `comparisons/compute.md`

### ✅ AWS: EC2 Capacity Blocks Next Review — July 2026 (April Review Passed; No Rate Change)
- The April 2026 pricing review cycle passed without changes to GPU Capacity Block rates
- p5e.48xlarge remains $39.80/hr (most regions); p5en.48xlarge remains $41.61/hr
- EC2 Capacity Blocks pricing page now states: **"current prices are scheduled to be updated next in July, 2026"**
- On-Demand and Savings Plans rates for GPU instances remain unchanged

### ✅ No new GCP pricing changes found (as of 2026-05-12)
- GCP CDN Interconnect/Peering increases (May 1, 2026) already in effect — no additional changes
- A3 Ultra EU/Asia price increase (May 1, 2026) already in effect — no further announcement
- Vertex AI Agent Engine billing live since Feb 11, 2026 — no new rate changes

---

## 2026-05-10

### ✅ GCP: CDN Interconnect & Peering Price Increase — **NOW IN EFFECT** (Effective May 1, 2026)
- The long-tracked price increase for CDN Interconnect, Direct Peering, and Carrier Peering is now active (effective May 1, 2026)
- North America: **$0.08/GiB** (was $0.04, +100%)
- Europe: **$0.08/GiB** (was $0.05, +60%)
- Asia: **$0.085/GiB** (was $0.06, +42%)
- Standard internet egress rates are **not** changed
- Now reflected in May 2026 invoices
- Customers still on Direct/Carrier Peering: evaluate migrating to Verified Peering Providers (VPPs), which offer SLAs and are Google's recommended alternative
- Updated: `providers/gcp.md`, `comparisons/storage.md` (countdown language removed; "NOW IN EFFECT" status applied)

### ✅ GCP: A3 Ultra GPU (H200) — Europe/Asia Price Increase **NOW IN EFFECT** (Effective May 1, 2026)
- The A3 Ultra (a3-ultragpu-8g, 8× NVIDIA H200) list price increase in **Europe and Asia** regions is now active
- US regions (us-central1: **$84.81/hr** on-demand) remain unchanged
- CUD pricing also increased proportionally in affected EU/Asia regions
- Now reflected in May 2026 invoices
- Updated: `providers/gcp.md`

### 🆕 GCP: C4N and M4N VM Families — Preview (announced April 22, 2026 at Cloud Next '26)
- **C4N** (compute-optimized with enhanced networking): 4th-gen Compute Engine with higher NIC bandwidth; optimized for RL reward calculation, agent orchestration, nested visualization, Teradata analytics workloads
- **M4N** (memory-optimized with enhanced networking): 26.57 GiB RAM per vCPU; targets Oracle and high-memory database workloads; claims >20% TCO reduction for Oracle vs prior gen with Hyperdisk Extreme
- Both in Preview; no public pricing yet published
- ⚠️ **CUD migration risk**: Existing resource-based CUDs for C4 (C4N predecessor) and M3 (M4N predecessor) do NOT automatically transfer — teams migrating workloads must purchase new commitments or lose CUD coverage
- Sign-up required for Preview access
- Updated: `providers/gcp.md`, `comparisons/compute.md`

### 🆕 GCP: Z4D Storage-Optimized VMs — Preview coming (announced April 22, 2026 at Cloud Next '26)
- New VM family (distinct from Z4M) optimized for **I/O-intensive workloads**: SQL, NoSQL, and vector databases
- Up to **84 TiB local SSD** on-node; up to **400 Gbps VM-to-VM bandwidth**
- Preview expected soon (no date); pricing not yet published
- Comparison: Z4M = 168 TiB local SSD, distributed file systems / AI/ML training staging; Z4D = 84 TiB, database I/O workloads
- Updated: `providers/gcp.md`

### 🆕 AWS: Database Savings Plans — Now Covers OpenSearch + Neptune Analytics (March 5, 2026)
- AWS expanded Database Savings Plans (launched Dec 2025) to cover two additional services:
  - **Amazon OpenSearch Service**: 20% instance discount, 20% serverless discount
  - **Amazon Neptune Analytics**: 30% serverless discount
- Full coverage now spans: Aurora, RDS, DynamoDB, ElastiCache (Valkey only), DocumentDB, Neptune, Neptune Analytics, OpenSearch, Keyspaces, Timestream, DMS
- Key constraint: Gen 7+ instance families only for provisioned compute; ElastiCache applies to Valkey only (not Redis/Memcached)
- 1-year term only; spend-based (not per-resource); cross-service and cross-region
- Updated: `providers/aws.md` (new Database Savings Plans section), `comparisons/databases.md`

### ✅ No new pricing changes found for Azure IaaS/PaaS (as of 2026-05-10)
- Azure Functions runtime v3 / Linux Consumption enforcement (Sep 30, 2026) remains upcoming
- Azure GPv1 storage retirement (Oct 13, 2026) remains upcoming
- Microsoft 365 commercial price increases (July 1, 2026) remain upcoming
- No new Azure VM, Blob, SQL, AKS, or CDN pricing announcements found

---

## 2026-04-26

### 🆕 GCP: TPU v7 Ironwood — Generally Available (April 22, 2026)
- **Ironwood (TPU v7)** is now GA to Google Cloud customers as of Cloud Next '26 (April 22, 2026)
- Announced at Cloud Next '25 (April 2025); available in preview since then; GA confirmed April 22, 2026
- **Specs per chip**: 4.6 petaFLOPS FP8 compute, 192 GB HBM3e, 7.37 TB/s memory bandwidth
- **Superpod**: 9,216 chips → 42.5 exaFLOPS — claimed 24× the capacity of El Capitan
- Purpose-built for inference (the "age of inference"); also supports large-scale training
- **Public pricing**: See GCP TPU pricing page (per chip-hour; varies by DWS flex, calendar mode, 1-yr/3-yr CUD)
- Updated: `providers/gcp.md` (new Ironwood GA section under GPU/TPU)

### 🆕 GCP: 8th-Generation TPUs Announced — TPU 8t (Sunfish) + TPU 8i (Zebrafish) (April 22, 2026)
- First time Google has purpose-built **separate training and inference** TPU chips
- **TPU 8t** (training): 2 compute dies + 1 I/O chiplet, 8× 12-high HBM3e stacks; ~30% higher memory bandwidth than Ironwood; up to 2.7× training price-performance over Ironwood
- **TPU 8i** (inference): 1 compute die + 1 I/O die, 6× HBM3e stacks; 80% inference price-performance improvement over Ironwood; 20–30% cheaper than training variant
- Both fabricated on **TSMC 2nm** process; targeted GA **late 2027**
- Designed with Broadcom (8t) and MediaTek (8i)
- No public pricing announced; interest form available at cloud.google.com/resources/tpu-interest
- Updated: `providers/gcp.md` (new 8th-gen TPU Upcoming section)

### 🆕 GCP: A5X with NVIDIA Vera Rubin NVL72 — Announced (April 22, 2026)
- New **A5X** VM family to be powered by NVIDIA Vera Rubin NVL72 (Blackwell successor)
- Concept uses open-source Falcon networking protocol
- Availability: later in 2026 (no GA date announced); pricing TBD
- Updated: `providers/gcp.md` (new A5X section under upcoming changes)

### ⚠️ Azure: Functions Runtime v3 on Linux Consumption — New Retirement Date (April 17, 2026)
- **New announcement**: Azure Functions **runtime v3** on **Linux Consumption** will **stop running September 30, 2026** (Azure ID: 559311)
- Note: This is distinct from the broader Linux Consumption plan retirement (Sep 30, 2028)
- Runtime v3 was officially retired December 13, 2022 but still executing — enforcement now begins Sep 30, 2026
- After Sep 30, 2026: Function Apps on runtime v3 + Linux Consumption will **not start or process executions**
- **Action required**: Migrate to runtime v4 **and** migrate plan to Flex Consumption (recommended) before Sep 30, 2026
- Flex Consumption supports runtime v4 and ongoing platform updates
- Updated: `providers/azure.md`, `comparisons/serverless.md`

### ⚠️ GCP: CDN Interconnect & Peering Price Increase — Now 5 Days Away (Effective May 1, 2026)
- Effective date: **May 1, 2026** — **5 days away**
- North America: $0.04 → **$0.08/GiB** (+100%); Europe: $0.05 → **$0.08/GiB** (+60%); Asia: $0.06 → **$0.085/GiB** (+42%)
- No further rate changes announced; final countdown
- Updated countdown callout in: `providers/gcp.md`

### ✅ No new pricing changes found for AWS (as of 2026-04-26)
- EC2 Capacity Blocks next review remains July 2026; rates unchanged (p5e.48xlarge: $39.80/hr, p5en.48xlarge: $41.61/hr)
- CloudFront flat-rate plans, Lambda, S3, RDS pricing unchanged
- AWS NVIDIA Vera Rubin (via A5X GCP equivalent): AWS has not announced equivalent yet

---

## 2026-04-24

### ⏰ GCP: CDN Interconnect & Peering Price Increase — Now 7 Days Away (Effective May 1, 2026)
- Effective date: **May 1, 2026** — 7 days away (down from 9 days on Apr 22)
- North America: $0.04 → **$0.08/GiB** (+100%); Europe: $0.05 → **$0.08/GiB** (+60%); Asia: $0.06 → **$0.085/GiB** (+42%)
- No new rate changes; confirmed rates remain as announced
- Last chance to migrate from Direct/Carrier Peering to Verified Peering Providers (VPPs) before billing change
- Updated countdown callouts in: `providers/gcp.md`, `comparisons/storage.md`

### 🆕 GCP: Google Cloud Storage — 2026 Multi-Region Pricing Changes
- **Nearline multi-region** (US/EU): **$0.010 → $0.015/GB-mo (+50%)** — effective 2026
- **Archive multi-region** (US/EU): **$0.004 → $0.0024/GB-mo (-40%)** — effective 2026
- Regional pricing (single-region, e.g. us-central1) unchanged
- Source: FinOut cloud storage comparison (April 20, 2026) — confirmed against GCS pricing docs
- **Action**: Review lifecycle policies. Teams using multi-region Nearline for infrequent data now face higher costs; teams using multi-region Archive get a discount.
- Updated: `providers/gcp.md` (new multi-region table), `comparisons/storage.md` (Cheapest archival row + note)

### 🆕 GCP: Google Cloud Next '26 Compute & Storage Announcements (April 22–24, 2026)
- **C4A.metal** (Axion bare metal) — **Preview**: First Axion bare metal instance, no hypervisor overhead. Powers Android dev, CI/CD, custom hypervisors. No pricing announced yet.
- **GKE Agent Sandbox on N4A** — **GA**: Industry's first native sandbox for AI agent workloads. Runs on Axion N4A VMs; claims 30% better price-performance vs competitors. Priced at standard GKE N4A rates — no Agent Sandbox surcharge.
- **Z4M** storage VMs — **Preview expected Q3 2026**: Up to 168 TiB local SSD, 400 Gbps network, RDMA, bare-metal shapes. Targeting distributed parallel file systems and large-scale AI/ML. Pricing not yet announced.
- **Hyperdisk ML** throughput increase — **GA**: Aggregate throughput raised from 1.2 TiB/s to **2 TiB/s** (~67% improvement). No price change.
- **Hyperdisk Exapools** — **GA**: Highest aggregate block storage performance per AI cluster. Pricing varies by configuration.
- Updated: `providers/gcp.md` (new "Google Cloud Next '26 Announcements" section)

### ✅ No new pricing changes found for AWS (as of 2026-04-24)
- EC2 Capacity Blocks next review remains July 2026; rates unchanged (p5e.48xlarge: $39.80/hr, p5en.48xlarge: $41.61/hr)
- No new Lambda, S3, EC2 on-demand, or Fargate pricing changes found
- AWS P6e UltraServer pricing ($761.904/hr) remains current

### ✅ No new pricing changes found for Azure (as of 2026-04-24)
- **Windows 365 Business 20% list price decrease** effective May 1, 2026 (Windows 365 SaaS — not tracked in IaaS/PaaS docs)
- Azure IaaS/PaaS (VMs, Blob, Functions, SQL) pricing unchanged
- HBv2-series VM retirement announced: May 31, 2027 (1-yr/3-yr RI purchases end April 2, 2026)
- Microsoft 365 commercial price increases remain on track for July 1, 2026 (M365 SaaS, not Azure cloud infra)

---

## 2026-04-22

### 🆕 AWS: Lambda + S3 Files Integration — GA (April 21, 2026)
- **Posted April 21, 2026**: AWS Lambda now supports mounting Amazon S3 buckets as file systems using S3 Files (the NFS v4.2 file-system-on-S3 feature, itself GA on April 7, 2026)
- Mount any S3 bucket into a Lambda function at a standard path (e.g., `/mnt/s3files`) and use normal file operations — no SDK calls required
- Multiple Lambda functions can share the same S3 Files file system simultaneously
- **No additional charge** beyond standard Lambda + S3 pricing
- S3 Files pricing: Cached storage $0.30/GB-mo (hot data only); large file reads (≥1 MB) = standard S3 GET rates (no surcharge); small reads $0.03/GB; writes $0.06/GB
- **EFS vs S3 Files cost comparison**: EFS Standard = $0.30/GB-mo for all data; S3 Files = $0.30/GB-mo only for actively cached/hot data — cold data billed at $0.023/GB-mo (S3 Standard). For a 10 TB dataset with 200 GB hot: S3 Files ~$230/mo vs EFS ~$3,072/mo (~13× cheaper)
- Not compatible with Lambda functions using a capacity provider
- Ideal for: shared ML model serving, large-file ETL pipelines, agentic AI workspaces, multi-function shared config
- Updated: `providers/aws.md` (new S3 Files section), `comparisons/serverless.md` (new Lambda S3 Files section + feature table row), `comparisons/storage.md` (file system access comparison table)

### ⏰ GCP: CDN Interconnect & Peering Price Increase — Now 9 Days Away
- Effective date: **May 1, 2026** — now 9 days away
- North America: $0.04 → **$0.08/GiB** (+100%); Europe: $0.05 → **$0.08/GiB** (+60%); Asia: $0.06 → **$0.085/GiB** (+42%)
- No new rate changes announced; rates confirmed unchanged
- Updated countdown callouts in: `providers/gcp.md`, `comparisons/storage.md`

### ✅ No new pricing changes found for Azure (as of 2026-04-22)
- Azure Functions Linux Consumption retirement (Sep 30, 2028) already tracked
- Azure Savings Plan for Databases (March 18, 2026) remains active
- Microsoft 365 commercial price increases (July 1, 2026) not tracked here (M365, not Azure IaaS/PaaS)

---

## 2026-04-20

### 🆕 AWS: Graviton4 Instances (M8g / C8g / R8g) — Pricing Added
- AWS Graviton4-based instances now tracked in `providers/aws.md` and `comparisons/compute.md`
- **M8g (General Purpose)**: m8g.large (2 vCPU / 8 GB) = **$0.0898/hr** ($65.55/mo); up to 30% better performance vs Graviton3 M7g ($0.0816/hr)
- **C8g (Compute Optimized)**: c8g.large (2 vCPU / 4 GB) = **$0.0798/hr** ($58.25/mo)
- **R8g (Memory Optimized)**: r8g.large (2 vCPU / 16 GB) = **$0.1178/hr** ($86.00/mo)
- All three GA in most AWS regions; expanded to additional regions Dec 2025 and Feb 2026 (OpenSearch support)
- **Price-performance**: Graviton4 delivers up to 40% better performance for databases, 30% for web apps, 45% for large Java apps vs Graviton3
- Note: M8g.large is slightly *more expensive* than M7g.large ($0.0898 vs $0.0816) but delivers significantly more compute per dollar (better price-performance ratio overall)
- Savings Plans / Reserved: 1-yr ~34% off, 3-yr ~55% off; Spot: ~60-63% off on-demand

### 🆕 GCP: N4A (Google Axion ARM) — Generally Available (effective Jan 26, 2026)
- GCP N4A machine family powered by **Google Axion processor** (custom Arm Neoverse N3) became GA on **January 26, 2026**
- Now tracked in `providers/gcp.md` and `comparisons/compute.md`
- **n4a-standard-2**: 2 vCPU / 8 GB = **$0.0770/hr** ($56.21/mo) — cheapest 2 vCPU / 8 GB option across the three major clouds
- **n4a-standard-4**: 4 vCPU / 16 GB = **$0.1540/hr** ($112.42/mo)
- **n4a-standard-8**: 8 vCPU / 32 GB = **$0.3080/hr** ($224.84/mo)
- Google claims up to 2× better price-performance than x86 VMs for scale-out workloads; early customers report 20-60% efficiency gains
- **1-yr CUD**: ~28% off; **3-yr CUD**: ~45% off; **Spot**: up to 91% off
- SUDs do not apply to N4A; supports standard/highmem/highcpu and custom types (up to 64 vCPU / 512 GB)
- Available: us-central1, us-east4, europe-west3, europe-west4, and expanding
- Complements C4A (Axion compute-optimized, GA since Oct 2024) for a full Axion portfolio

### ⏰ GCP: CDN Interconnect & Peering Price Increase — Now 11 Days Away
- Effective date: **May 1, 2026** — now 11 days away (down from 13 days on Apr 18)
- North America: $0.04 → **$0.08/GiB** (+100%); Europe: $0.05 → **$0.08/GiB** (+60%); Asia: $0.06 → **$0.085/GiB** (+42%)
- Updated countdown callouts in: `providers/gcp.md`, `comparisons/storage.md`, `comparisons/compute.md`

### ✅ No new pricing changes found for Azure (as of 2026-04-20)
- No new pricing announcements found; all previously tracked changes remain active
- Next tracked Azure event: July 1, 2026 — Microsoft 365 commercial price increases

---

## 2026-04-18

### ✅ GCP: Vertex AI Agent Engine — Sessions, Memory Bank & Code Execution Billing (Active since Feb 11, 2026)
- Now tracked in `providers/gcp.md` under Upcoming Changes (now active)
- **Sessions**: $0.25 per 1,000 stored session events (content events only; system/checkpoint events free)
- **Code Execution**: $0.0864/vCPU-hr + $0.0090/GiB-hr (same rate as Agent Engine runtime)
- **Memory Bank**: billed at runtime vCPU + memory rates per retrieval/storage operation
- **Runtime free tier**: 50 vCPU-hrs + 100 GiB-hrs/month/project (then $0.0864/vCPU-hr, $0.009/GiB-hr)
- Idle agents are **not** billed — charges only for active processing
- Code Execution reached GA on February 18, 2026
- Impact: Teams using multi-agent pipelines with sessions + memory will now see new line items
- Added to: `providers/gcp.md`

### ⏰ GCP: CDN Interconnect & Peering Price Increase — Countdown Update (Now 13 Days Away)
- Effective date: **May 1, 2026** — now 13 days away
- North America: $0.04 → **$0.08/GiB** (+100%); Europe: $0.05 → **$0.08/GiB** (+60%); Asia: $0.06 → **$0.085/GiB** (+42%)
- No new rate changes announced; rates confirmed unchanged
- Updated countdown callouts in: `providers/gcp.md`, `comparisons/storage.md`

### ✅ No new pricing changes found for AWS or Azure (as of 2026-04-18)
- AWS Lambda INIT billing, CloudFront flat-rate plans, EKS 8XL, P6e UltraServer all previously tracked
- AWS Capacity Blocks next review: July 2026 (confirmed unchanged)
- Azure: no new pricing announcements found; Savings Plan for Databases (March 18, 2026) remains active
- GCP Spot pricing confirmed: `a3-ultragpu-8g` Spot = **$42.18/hr** (us-central1); `a3-megagpu-8g` Spot = **$34.57/hr**

---

## 2026-04-16

### 🆕 AWS: EKS Provisioned Control Plane — New 8XL Tier + SLA Upgrade (March 20, 2026)
- **New 8XL tier** added to Amazon EKS Provisioned Control Plane: **+$13.90/hr** (~$10,147/mo add-on)
- 8XL provides **double the API capacity** of 4XL: 13,600 concurrent API seats, 400 pods/sec scheduling
- SLA for **all** Provisioned Control Plane clusters upgraded from **99.95% → 99.99%** (measured per 1-minute intervals)
- Available in all commercial, GovCloud, and China regions supporting EKS Provisioned Control Plane
- Tiers summary: XL (+$1.65/hr) → 2XL (+$3.40/hr) → 4XL (+$6.90/hr) → 8XL (+$13.90/hr); >8XL: contact AWS
- Useful for: ultra-scale AI/ML training, HPC, large-scale data processing with 1,000s of worker nodes
- Added to: `providers/aws.md`, `comparisons/compute.md`

### 🔍 GCP: A3 Ultra On-Demand Price Confirmed — ~$84.81/hr (us-central1)
- Updated confirmed on-demand price for `a3-ultragpu-8g` (8× H200, 224 vCPU, 2,952 GB RAM)
- us-central1: **$84.81/hr** (previously approximate at ~$86.76/hr; corrected from GCP pricing page)
- Spot (us-central1): ~$42.40/hr
- 1-Year CUD (us-central1): ~$59.36/hr
- EU/Asia rates increase **May 1, 2026** (15 days away); US rates unchanged
- Added Azure ND96isr H200 v5 (~$84.80/hr, West US 3) to GPU comparison table
- Updated: `providers/gcp.md`, `comparisons/compute.md`

### ⚠️ GCP: CDN Interconnect & Peering Price Increase — ~~15 Days Away~~ 13 Days Away (Effective May 1, 2026)
- Rate doubling confirmed; action window is closing
- Customers on Direct Peering or Carrier Peering should evaluate Verified Peering Providers (VPPs)
- Updated imminence callout in: `providers/gcp.md`, `comparisons/storage.md`

### ⚠️ Azure: GPv1 Storage Account Retirement — October 13, 2026
- New GPv1 account creation blocked since **March 3, 2026** (confirmed)
- Full retirement date confirmed: **October 13, 2026**; remaining accounts auto-migrated to GPv2
- Auto-migration may change billing (per-blob tiering + different operation rates)
- Failure to migrate = implicit consent for Microsoft to auto-upgrade
- Updated callout in: `comparisons/storage.md`

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
