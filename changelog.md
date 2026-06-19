# Changelog

> Pricing changes tracked by the Cloud Pricing Tracker agent. Newest entries first.

---

## 2026-06-19

### ⏰ Azure: Legacy VM Reserved Instances Discontinuation — **12 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-19**: 12 days until the hard deadline. **No new purchases or renewals after June 30, 2026.**
- After July 1: affected RIs cannot be purchased or renewed — auto-renew is silently blocked; workloads fall back to pay-as-you-go rates when the RI expires
- Full series list (no change from prior entries):
  - **1-year RIs ending**: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2
  - **1-year and 3-year RIs ending**: Dv3, Dsv3, Ev3, Esv3
- Highest-impact: **Dv3/Dsv3 and Ev3/Esv3** — widely used general-purpose and memory-optimized series in SMB and mid-market
- Migration paths: newer VM series (Dv5, Ev5, Lsv3) + Azure Savings Plan for Compute, or renew before June 30 if staying short-term
- Microsoft confirmed: existing RIs valid through their full purchased term; auto-renew silently blocked post-July 1
- Source: [Azure Update ID 560948](https://azure.microsoft.com/en-us/updates/?filters=%5B%22Retirements%22%5D) / [Transition guide](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/manage-legacy-vm-reservations-after-july-1-2026)

### ⏰ Azure: Microsoft 365 Commercial Pricing Increases — **12 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-19**: 12 days until the effective date. Renew **before June 30** to lock in current rates for one additional year.
- Increases take effect for new customers and renewing customers on their first renewal after July 1, 2026
- Key price changes (per user/month, annual commitment, USD):
  | SKU | Old Price | New Price | Change |
  |---|---|---|---|
  | Microsoft 365 Business Basic | $6.00 | $7.00 | +16% |
  | Microsoft 365 Business Standard | $12.50 | $14.00 | +12% |
  | Microsoft 365 Business Premium | $22.00 | $22.00 | — no change |
  | Microsoft 365 E3 | $36.00 | $39.00 | +8% |
  | Microsoft 365 E5 | $57.00 | $60.00 | +5% |
  | Office 365 E3 | $23.00 | $26.00 | +13% |
  | Office 365 E5 | $38.00 | $41.00 | +8% |
  | Microsoft 365 F1 | $2.25 | $3.00 | +33% |
  | Microsoft 365 F3 | $8.00 | $10.00 | +25% |
- Bundled new capabilities at July 1: Copilot Chat, Microsoft Defender for Office 365 Plan 1, expanded Intune, +50 GB mailbox storage
- Note: M365 Business Premium is **not** increasing — creates narrower gap vs. Business Standard (was $9.50 gap, becomes $8.00), strengthening the upgrade value proposition for MSPs
- Source: [microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates](https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates)

### ⏰ AWS: EC2 Capacity Blocks for ML — July 2026 Pricing Review Imminent
- **Status as of 2026-06-19**: AWS pricing page confirmed **"current prices are scheduled to be updated next in July, 2026"** (verified live from [aws.amazon.com/ec2/capacityblocks/pricing/](https://aws.amazon.com/ec2/capacityblocks/pricing/) on 2026-06-19)
- Current rates unchanged from the April–May 2026 snapshot:
  - **p5e.48xlarge** (8× H200): $39.799/hr (most regions); $49.749/hr (US West N. California)
  - **p5en.48xlarge** (8× H200): $45.768/hr (US regions); $41.612/hr (EU/Asia)
  - **p6-b200.48xlarge** (8× B200): $82.368/hr
  - **p6-b300.48xlarge** (8× B300): $93.60/hr
  - **P6e UltraServer u-p6e-gb200x72** (72× B200): $761.904/hr (US East Dallas Local Zone)
- On-Demand and Savings Plans rates for all EC2 instances remain **unchanged**
- Background: Capacity Blocks have been reviewed quarterly. Jan 2026 saw a 15% hike; the April 2026 review passed without a published base-rate change. The July 2026 review is the next one.
- **Watch**: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new AWS base pricing changes found (as of 2026-06-19)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront — all rates confirmed unchanged
- S3 pricing structure stable: Standard $0.023/GB (first 50 TB), $0.022/GB (51–500 TB), $0.021/GB (>500 TB)
- AWS Free Tier structure unchanged: new accounts (≥Jul 15, 2025) get $200 credit-based model (6-month Free Plan); legacy accounts retain 12-month per-service model

### ✅ No new GCP pricing changes found (as of 2026-06-19)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — all rates confirmed unchanged
- GCP CDN Interconnect/Peering/Direct Peering price increases (effective May 1, 2026) remain in effect; no further changes
- N4A (Axion ARM), G4 (RTX PRO 6000), Fractional G4 VMs — all at previously documented rates
- GCP Compute Flexible CUD model (expanded Feb 2026) — no changes

### ✅ No new Azure base pricing changes found (as of 2026-06-19)
- Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN — all rates confirmed unchanged
- **Azure Blob Storage 128 KiB minimum object size**: still **PAUSED** (paused June 8, 2026 via Azure Update ID 559756) — no new timeline or replacement policy published
- Azure Cobalt 200 VMs (Early Access Preview, June 2, 2026): pricing still not published; on track to expand to more regions

---

## 2026-06-17

### ⏰ Azure: Legacy VM Reserved Instances Discontinuation — **14 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-17**: 14 days until the deadline. Last chance to purchase or renew RIs on affected legacy series.
- No new purchases or renewals available after June 30. Affected series:
  - **1-year RIs ending**: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2
  - **1-year and 3-year RIs ending**: Dv3, Dsv3, Ev3, Esv3
- Existing RIs remain valid through their purchased term; auto-renew is blocked after July 1
- If your RI for any of these series expires after July 1, it cannot be renewed — usage will fall back to pay-as-you-go rates
- **Recommended path**: Migrate to newer series (Dv5, Ev5, Fsv2 → Dlsv6) and buy Azure Savings Plan for Compute, or renew before June 30 if staying on legacy series short-term
- Microsoft transition guide: [learn.microsoft.com/…/manage-legacy-vm-reservations-after-july-1-2026](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/manage-legacy-vm-reservations-after-july-1-2026)

### ⏰ Azure: Microsoft 365 Commercial Pricing Increases — **14 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-17**: 14 days until the deadline. Renew before June 30 to lock in current rates for one year.
- Key per-user/month increases taking effect July 1:
  - Microsoft 365 Business Basic: $6.00 → **$7.00** (+16%)
  - Microsoft 365 Business Standard: $12.50 → **$14.00** (+12%)
  - Microsoft 365 E3: $36.00 → **$39.00** (+8%)
  - Microsoft 365 E5: $57.00 → **$60.00** (+5%)
  - Office 365 E3: $23.00 → **$26.00** (+13%)
  - Microsoft 365 F1: $2.25 → **$3.00** (+33%)
  - Microsoft 365 F3: $8.00 → **$10.00** (+25%)
  - **Microsoft 365 Business Premium**: no change ($22.00)
- New capabilities bundled at July 1: Copilot Chat, Defender for Office 365 Plan 1, expanded Intune, +50 GB mailbox
- Source: [microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates](https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates)

### 🆕 Azure: NVv3 and NVv4 GPU VM Series Retirement — September 30, 2026
- **Announced April 15, 2025** (Azure Update ID 516070); confirmed in Azure VM retirement list (updated June 2026)
- **Azure NVv3-series** and **NVv4-series** GPU VMs will be **retired on September 30, 2026**
- After retirement: VMs on these series cannot be started; no SLA; existing disks preserved but compute stops
- **NVv3** is powered by NVIDIA Tesla M60 GPUs (8 GB GDDR5/GPU); **NVv4** uses AMD Radeon Instinct MI25 GPUs
- Both are visualization-class GPUs designed for remote desktop / VDI workloads — superseded by newer options
- **Recommended replacements**:
  - NVv3 → **NVadsA10 v5** (NVIDIA A10, 24 GB) or **NCv6 / NCads H100 v5** depending on workload
  - NVv4 → **NVadsA10 v5** (NVIDIA A10) for visualization; or newer AMD-based GPU series if available
  - For AI inference: consider **NCv6 RTX PRO 6000** (GA June 2026) or **NCads H100 v5**
- **Purchase/renewal of 1-year and 3-year RIs for NVv3/NVv4 also ended** — no new commitments available
- Time remaining: ~104 days. Begin migration planning now.
- Migration guide: [azure.microsoft.com/…/nvv3-series-retirement](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/gpu-accelerated/nvv3-series-retirement)
- Updated: `providers/azure.md` (NVv3/NVv4 retirement added under Upcoming Changes)

### ✅ AWS: EC2 Capacity Blocks — July 2026 Review Still Upcoming (no change since Jun 15)
- AWS pricing page confirmed as of June 17, 2026: **"current prices are scheduled to be updated next in July, 2026"**
- All Capacity Block rates remain unchanged from the June 15 snapshot:
  - p5e.48xlarge (8× H200): **$39.799/hr** (most regions), $49.749/hr (US West N. California)
  - p5en.48xlarge (8× H200): **$45.768/hr** (US regions), $41.612/hr (EU/Asia)
  - p6-b200.48xlarge (8× B200): **$82.368/hr**
  - p6-b300.48xlarge (8× B300): **$93.60/hr**
  - P6e UltraServer u-p6e-gb200x72 (72× B200): **$761.904/hr** (US East Dallas Local Zone)
- On-Demand and Savings Plans rates for all EC2 instances remain unchanged
- Monitor: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new AWS base pricing changes found (as of 2026-06-17)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront — all rates unchanged

### ✅ No new GCP pricing changes found (as of 2026-06-17)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage — all rates unchanged
- GCP P100 GPU end-of-support (Sep 15, 2026) and CDN Interconnect/Peering increases (May 1, 2026) still in effect — no new developments

### ✅ No new Azure base pricing changes found (as of 2026-06-17)
- Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN — all rates unchanged
- Azure Blob Storage 128 KiB minimum object size: still **PAUSED** (June 8, 2026) — no new timeline published

---

## 2026-06-15

### 🆕 GCP: Datastream — Perpetual Free Tier for AlloyDB & Spanner → BigQuery (June 2, 2026)
- **Announced via Google Cloud release notes: June 2, 2026**
- Datastream now offers a **permanent free tier**: up to **100 GiB of CDC (Change Data Capture) data per billing account per month** at **$0** — no expiry
- **Eligible sources**: AlloyDB for PostgreSQL and Cloud Spanner (first-party GCP sources only)
- **Eligible destination**: BigQuery only
- Usage is aggregated across all eligible AlloyDB + Spanner streams within a single billing account
- Once the 100 GiB free threshold is crossed, standard tiered pricing applies: **$2.00/GiB** (up to 2,500 GiB), $1.50/GiB (2,500–5,000 GiB), $1.20/GiB (5,000–10,000 GiB), $0.80/GiB (>10,000 GiB)
- CDC from **other sources** (Oracle, MySQL, SQL Server, PostgreSQL self-managed) is **not** covered by the free tier and is charged from the first GiB
- Separate from the existing 500 GiB **one-time backfill credit** per billing account
- **Pricing confirmed via**: [cloud.google.com/datastream/pricing](https://cloud.google.com/datastream/pricing)
- **Impact for engineers**: Teams building real-time pipelines from AlloyDB/Spanner → BigQuery at under 100 GiB/month now pay $0 for the Datastream CDC component. Typical small/medium analytics replication scenarios are fully covered.
- Updated: `providers/gcp.md` (new Datastream free tier section added), `comparisons/free-tiers.md` (GCP free tier table updated)

### ⚠️ GCP: VMware Engine ve1 CUDs — 1-Year End-of-Sale in Europe (West2 / London) (Effective May 20, 2026)
- **Announced May 20, 2026** (VMware Engine release notes / service announcements)
- 1-year Committed Use Discounts (CUDs) for Google Cloud VMware Engine **`ve1` SKUs** are now **End-of-Sale** in the **europe-west2 (London, UK)** region
- Existing ve1 CUDs in europe-west2 are **not affected** — they remain valid until their current term ends
- On-demand pricing for ve1 nodes in europe-west2 **continues**
- **`ve2` nodes and CUDs are unaffected** and remain purchasable in europe-west2
- Background: 3-year ve1 CUDs had been end-of-sale globally since September 2025; this extends the end-of-sale to 1-year ve1 CUDs in europe-west2. **Most other regions retain 1-year ve1 CUDs** for now.
- **Action**: Teams using ve1 in London should migrate to ve2 node types for continued CUD access, or use on-demand pricing in the interim.
- Updated: `providers/gcp.md` (VMware Engine / Upcoming Changes section)

### ⚠️ GCP: VMware Engine ve2 3-Year CUDs — Terminate Oct 15, 2028 (Effective June 1, 2026)
- **Announced June 1, 2026** (VMware Engine release notes)
- All **3-year (36-month) ve2 Committed Use Discounts purchased after May 31, 2026** will be **terminated on October 15, 2028**, regardless of the original term end date
- 3-year CUD pricing rates still apply for the period used (not prorated at higher on-demand rates)
- Background: VMware Engine hardware and licensing lifecycle changes (Broadcom VCF transition) are driving a wind-down of long-term commitments beyond 2028
- **Action**: Teams purchasing 3-year ve2 CUDs after May 31, 2026 should budget for GCVE on-demand or ve2 re-commitment costs starting October 2028. Consider shorter commitments (1-year) if planning beyond 2028.
- Updated: `providers/gcp.md` (VMware Engine / Upcoming Changes section)

### ⏰ Azure: Legacy VM Reserved Instances Discontinuation — 16 Days Away (Effective July 1, 2026)
- **Status as of 2026-06-15**: 16 days until the deadline. No new purchases or renewals after July 1.
- Reminder: the following RI series are affected:
  - **1-year RIs ending**: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2
  - **1-year and 3-year RIs ending**: Dv3, Dsv3, Ev3, Esv3
- Existing RIs remain valid through their purchased term; auto-renew is blocked after July 1
- Microsoft transition guide: [learn.microsoft.com/…/manage-legacy-vm-reservations-after-july-1-2026](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/manage-legacy-vm-reservations-after-july-1-2026)
- No new pricing announcements on this item since last tracking entry (2026-05-24)

### ⏰ Azure: Microsoft 365 Commercial Pricing Increases — 16 Days Away (Effective July 1, 2026)
- **Status as of 2026-06-15**: 16 days until the deadline. Lock in current M365 rates before June 30.
- Customers who renew before June 30, 2026 can lock in current rates for one additional year
- Key increases at July 1:
  - Microsoft 365 Business Basic: $6.00 → **$7.00/user/mo** (+16%)
  - Microsoft 365 Business Standard: $12.50 → **$14.00/user/mo** (+12%)
  - Microsoft 365 E3: $36.00 → **$39.00/user/mo** (+8%)
  - Office 365 E3: $23.00 → **$26.00/user/mo** (+13%)
  - Microsoft 365 F1: $2.25 → **$3.00/user/mo** (+33%)
  - Microsoft 365 F3: $8.00 → **$10.00/user/mo** (+25%)
- Bundles include new capabilities: Copilot Chat, Defender for Office 365 Plan 1, Intune Remote Help + Advanced Analytics rolling out June–August 2026
- **Note**: This is M365 SaaS pricing, not Azure IaaS/PaaS — included here for completeness as it affects total Microsoft spend

### ✅ AWS: EC2 Capacity Blocks — July 2026 Review Still Upcoming (no change)
- AWS pricing page (last updated June 9, 2026) still confirms: **"current prices are scheduled to be updated next in July, 2026"**
- All current Capacity Block rates unchanged:
  - p5e.48xlarge (8× H200): **$39.799/hr** (most regions), $49.749/hr (US West N. California)
  - p5en.48xlarge (8× H200): **$45.768/hr** (US), $41.612/hr (EU/Asia)
  - p6-b200.48xlarge (8× B200): **$82.368/hr**
  - p6-b300.48xlarge (8× B300): **$93.60/hr**
  - P6e UltraServer (72× B200): **$761.904/hr**
- On-Demand and Savings Plans rates unchanged for all EC2 instances
- Watch: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/) — update expected sometime in July 2026

### ✅ No new AWS base pricing changes found (as of 2026-06-15)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront all unchanged

### ✅ No new GCP base pricing changes found (as of 2026-06-15)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage rates all unchanged
- GCP Flex-start VMs in MIGs now GA (June 3, 2026) — operational feature for obtaining discounted GPU capacity; not a pricing rate change

---

## 2026-06-13

### 🆕 Azure: Lasv5 & Laosv5 Storage-Optimized VMs — Private Preview (June 2, 2026)
- **Azure Update ID 564446** — Added to roadmap: **June 2, 2026** (announced at Microsoft Build 2026)
- New storage-optimized VM series powered by **5th-Gen AMD EPYC™ (Turin)** processors
- Two series with distinct storage capacity targets:
  - **Lasv5**: Up to **30.7 TB** local NVMe storage; designed for storage-intensive workloads requiring high disk throughput and I/O (DBs, analytics, large media)
  - **Laosv5**: Up to **138 TB** local NVMe storage; targets workloads requiring very high local storage density (distributed file systems, large-scale NoSQL, HPC data staging)
- Both series: 2–160 vCPU sizes; **8 GiB memory per vCPU**; **720 GB NVMe per vCPU**; up to **200 Gbps network bandwidth**; up to **35% better average CPU performance** vs previous generation
- Lasv5 improvements vs Lasv4: 33% larger maximum local storage, new 128 and 160 vCPU sizes
- Laosv5 improvements vs Laosv4: 500% larger maximum local storage, new 48/64/96/128/160 vCPU sizes
- **Status**: Private Preview (June 2026). **Pricing not yet published.** Apply via [aka.ms/Lasv5-Laosv5-Pr](https://aka.ms/Lasv5-Laosv5-Pr)
- Previous Lasv4 reference pricing for comparison (East US): ~$0.20–$2.40/hr depending on size (see Azure portal)
- Updated: `providers/azure.md` (new Lasv5/Laosv5 section added under Storage-Optimized compute)

### ⏰ Azure: Batch Pool Legacy VM Series Retirement — November 15, 2028 (Notice: June 11, 2026)
- **Azure Update ID 564774** — Added to roadmap: **June 11, 2026**
- Azure Compute will retire the following VM series for **Azure Batch pools** on **November 15, 2028**:
  - **Av2-series** (general purpose legacy)
  - **F-series, Fs-series, Fsv2-series** (compute-optimized legacy)
  - **G-series, Gs-series** (memory/storage-optimized legacy)
  - **Lsv2-series** (storage-optimized legacy)
- **Effect after November 15, 2028**: New Batch pools on these series cannot be created (already blocked now in some cases); existing pools cannot scale out; remaining VMs will be stopped/deallocated; no SLA coverage
- **Recommended replacements**:
  - Av2 → **Dsv5/Ddsv5** or **Dasv5/Dadsv5**
  - F/Fs/Fsv2 → **Dlsv6/Dldsv6**, **Falsv6**, or **Dsv5/Ddsv5**
  - G/Gs → **Lsv3/Lasv3** or **Easv5/Edsv5**
  - Lsv2 → **Lsv3/Lasv3** (or new Lasv5 when GA)
- **Action**: Scale pool to zero and update VM size using Batch API (version 07-01-24 or later), or create new pools with supported sizes and migrate workloads
- **Note**: VM pricing may change after migration to newer series. Review [Azure VM pricing](https://azure.microsoft.com/pricing/details/virtual-machines/) before migrating
- No impact on standalone VM workloads — this notice is Batch-pool-specific

### ✅ AWS: EC2 Capacity Blocks — July 2026 Review Still Upcoming (unchanged, as of 2026-06-13)
- AWS pricing page still confirms: **"current prices are scheduled to be updated next in July, 2026"**
- All Capacity Block rates unchanged since last update:
  - p5e.48xlarge (8× H200): **$39.799/hr** (most regions), $49.749/hr (US West N. California)
  - p5en.48xlarge (8× H200): **$45.768/hr** (US), $41.612/hr (EU/Asia)
  - p6-b200.48xlarge (8× B200): **$82.368/hr**
  - p6-b300.48xlarge (8× B300): **$93.60/hr**
  - P6e UltraServer (72× B200): **$761.904/hr**
- On-Demand and Savings Plans rates for all EC2 instances unchanged
- Monitor: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new GCP pricing changes found (as of 2026-06-13)
- All compute, storage, serverless, database, and CDN rates unchanged
- GCP NVIDIA P100 GPU end-of-support reminder: **September 15, 2026** — migrate to A3/G4/other GPU families
- C4N / M4N VM families: still in Preview with no pricing published
- Z4D / Z4M storage VMs: still pre-GA; no pricing published
- A5X (Vera Rubin): still announced only; no GA date or pricing set

### ✅ No new AWS base pricing changes found (as of 2026-06-13)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront all unchanged
- EC2 standard On-Demand and Savings Plans rates unchanged

---

## 2026-06-11

### 🆕 Azure: Cobalt 200 ARM VMs — Early Access Preview (June 2, 2026)
- **Announced: June 2, 2026** at Microsoft Build 2026 (Azure Blog)
- Microsoft's next-generation custom Arm-based CPU for cloud-native and agentic AI workloads
- Successor to **Cobalt 100** (GA December 2024); up to **50% better generational performance** over Cobalt 100
- Claims: up to **135% better** on cloud databases vs Cobalt 100; **80% better** on some VM workloads
- Memory encryption on by default (negligible perf impact via custom memory controller); Arm CCA (Confidential Compute Architecture) hardware isolation supported
- **New VM families introduced with Cobalt 200** (in addition to existing Cobalt 100 families Dp/Dpl/Ep):
  - **Dpsv7 / Dpdsv7** — General Purpose (with/without local NVMe)
  - **Dplsv7 / Dplds​v7** — General Purpose, lower memory-to-CPU ratio (cost-optimized)
  - **Epsv7 / Epdsv7** — Memory Optimized
  - **Mpsv4 / Mpdsv4** — High-Memory Optimized 🆕 (new category vs Cobalt 100)
  - **Lpsv5** — Dense Local NVMe Storage 🆕 (new category vs Cobalt 100)
- Up to **85 Gbps network bandwidth** and **70 Gbps remote storage throughput** on most series
- Preview regions: West US3, East US2, Central US, Sweden Central, East US, West US2, Spain Central, Indonesia Central
- **Pricing: Not yet published** — expected to be competitive with (or below) Cobalt 100 pricing per vCPU. Confirm at [Azure Virtual Machines pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/) when available
- Updated: `providers/azure.md` (new Cobalt 200 section added), `comparisons/compute.md` (ARM VM note updated)

### 🆕 Azure: HorizonDB — PostgreSQL-Compatible, AI-Optimized (Build 2026, Preview)
- **Announced: June 2, 2026** at Microsoft Build 2026
- Fully managed PostgreSQL service on Azure, purpose-built for AI applications and agentic workloads
- Claims **>3× the throughput** of comparable self-managed PostgreSQL setups in internal testing
- Distinct from Azure Database for PostgreSQL Flexible Server — HorizonDB is a new, separate product with a different internal architecture optimized for high-throughput AI/agent use cases
- **Pricing: Not yet published** (preview stage; check Azure portal for early access rates)
- Still in Preview — no GA date announced
- Updated: `providers/azure.md` (new HorizonDB note in databases section)

### ⏰ AWS: EC2 Capacity Blocks — July 2026 Pricing Review Upcoming (unchanged)
- AWS pricing page still confirms: **"current prices are scheduled to be updated next in July, 2026"**
- All rates unchanged as of 2026-06-11:
  - p5.48xlarge (8× H100): **$34.608/hr** (US regions), $31.464/hr (AP/EU/SA regions)
  - p5e.48xlarge (8× H200): **$39.799/hr** (most regions), $49.749/hr (US West N. California)
  - p5en.48xlarge (8× H200): **$45.768/hr** (US regions), $41.612/hr (EU/Asia regions)
  - p6-b200.48xlarge (8× B200): **$82.368/hr**; p6-b300.48xlarge (8× B300): **$93.60/hr**
  - P6e UltraServer (72× B200, Dallas LZ): **$761.904/hr**
- On-Demand and Savings Plans rates for all EC2 instances are unchanged
- Monitor: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new GCP pricing changes found (as of 2026-06-11)
- All compute, storage, serverless, database, and CDN rates unchanged
- TPU v7 Ironwood GA (April 2026) — pricing unchanged since GA
- C4N / M4N VM families still in Preview with no pricing published
- Z4D / Z4M storage VMs: still pre-GA; no pricing published
- A5X (Vera Rubin): still announced only; no pricing or GA date set

### ✅ No new AWS base pricing changes found (as of 2026-06-11)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront all unchanged
- EC2 standard On-Demand and Savings Plans rates unchanged

---

## 2026-06-09

### 🚫 Azure: Blob Storage 128 KiB Minimum Object Size — **PAUSED** (effective June 8, 2026)
- **Azure Update ID 559756** — last modified **June 8, 2026**
- Azure has **paused** the introduction of the minimum billable object size of **128 KiB** for Cool, Cold, and Archive tiers, which was previously scheduled to take effect:
  - July 1, 2026 (new accounts)
  - July 1, 2027 (all accounts)
- **Billing behavior will NOT change** on either date. There is no impact on any account — new or existing.
- Azure will announce a **revised approach and timeline** in a future Azure Update. No customer action required.
- **Engineering impact**: If you were planning to package small blobs, change lifecycle policies, or update billing dashboards for the new `BlockBlobSmall` / `Azure Data Lake Storage Small` metric types — those changes are **no longer needed** until a new date is set
- Updated: `providers/azure.md`, `comparisons/storage.md` (min object size warning removed; pause noted)

### 🆕 Azure: NCv6 Series VMs (NVIDIA RTX PRO 6000 Blackwell) — Generally Available (June 2026)
- **GA: June 2026** (was in Public Preview since November 2025)
- NC RTX PRO 6000 BSE v6 series: powered by **NVIDIA RTX PRO 6000 Blackwell Server Edition** (96 GB GDDR7) + **Intel Xeon Granite Rapids** (up to 4.2 GHz)
- Three sizing categories: General Purpose, Compute Optimized, Memory Optimized (16–320 vCPU, 64–1,280 GB RAM)

| Instance | vCPU | RAM | GPUs | $/hr (On-Demand) |
|---|---|---|---|---|
| NCdsxlRTX6kv6 | 32 | 128 GB | 1× RTX PRO 6000 | **$1.44** |
| NCldsxlRTX6kv6 | 64 | 128 GB | 1× RTX PRO 6000 | **$2.44** |

- Up to **200 Gbps** Azure Accelerated Networking; supports Premium SSD v2, Ultra Disk; up to 2 TB local temp storage
- **Price positioning**: At $1.44/hr per GPU, Azure NCv6 is the **lowest on-demand list price** for an RTX PRO 6000 instance among AWS, GCP, and Azure
  - vs. AWS G7e.2xlarge: $3.36/hr (same GPU, 8 vCPU/64 GiB)
  - vs. GCP G4-standard-48: $4.50/hr (same GPU, 48 vCPU/180 GiB)
  - vs. GCP Cloud Run (serverless, no-redundancy): ~$1.31/hr GPU-only (but requires min 20 vCPU ~$3.41/hr additional)
- Updated: `providers/azure.md` (new NCv6 section), `comparisons/compute.md` (GPU table updated)

### 🆕 Azure: DocumentDB Free Tier Now Provisions Instantly (June 2, 2026)
- **Azure Update ID 563082 / Dev Blog: June 2, 2026**
- Azure DocumentDB (MongoDB-compatible, open-source engine) free tier cluster provisioning is now **near-instant** (seconds instead of minutes)
- No change to pricing or free tier limits (still **32 GB storage, dedicated MongoDB cluster, free for account lifetime**)
- Enables agentic workflows and developer iteration loops to use DocumentDB free tier as a **zero-latency bootstrap step** — spin up a MongoDB-compatible cluster instantly for testing, validation, or ephemeral workloads
- 1 free tier cluster per Azure subscription; paused after 60 days inactivity; seamless upgrade path to paid tiers
- Updated: `providers/azure.md` (new DocumentDB section), `comparisons/free-tiers.md` (Azure DocumentDB always-free row added)

### ⏰ AWS: EC2 Capacity Blocks — July 2026 Pricing Review Upcoming
- AWS pricing page confirms: **"current prices are scheduled to be updated next in July, 2026"** (no change since last update)
- Current rates: p5e.48xlarge **$39.799/hr** (most regions), p5en.48xlarge **$45.768/hr** (US) / **$41.612/hr** (EU/Asia), p6-b200.48xlarge **$82.368/hr**, p6-b300.48xlarge **$93.60/hr**, P6e UltraServer **$761.904/hr**
- On-Demand and Savings Plans pricing **not affected** by Capacity Block reviews
- Direction of July update unspecified; monitor [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new GCP pricing changes found (as of 2026-06-09)
- GCP CUD Analysis reached GA (June 1, 2026) — tooling/UX feature, not a pricing change
- All compute, storage, serverless, database, and CDN rates unchanged since last update
- C4N and M4N VM families (Preview, announced Apr 2026): pricing still not published
- Z4D/Z4M storage VMs: still pre-GA; no pricing
- A5X (Vera Rubin): still announced only; no pricing or GA date

### ✅ No new AWS base pricing changes found (as of 2026-06-09)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront all unchanged
- EC2 standard On-Demand and Savings Plans rates unchanged

---

## 2026-05-26

### 🆕 Azure: Blob Storage Smart Tier — Generally Available (April 14, 2026)
- **GA: April 14, 2026** (Azure Update ID: 559746)
- Smart tier is Azure's **fully managed, automatic tiering** for Blob Storage and Data Lake Storage — moves data between Hot, Cool, and Cold tiers based on access patterns, without requiring lifecycle rules
- Directly analogous to AWS S3 Intelligent-Tiering (and GCS Autoclass), but with differences in supported tiers and billing structure
- **How it works**: New data lands in Hot by default. Objects untouched for **30 days** move to Cool; after **90 days** of inactivity they move to Cold. Access resets the clock and promotes back to Hot automatically
- **Billing model**: Objects billed at standard Hot/Cool/Cold capacity rates for whichever tier they currently reside in
  - Monthly **monitoring fee** charged per object **>128 KiB** managed by smart tier (covers orchestration cost)
  - Objects ≤128 KiB: **no monitoring fee** (helps with small-object workloads)
  - **No tier-change fees**, **no early deletion fees**, **no retrieval charges** within smart tier
- **Not supported**: Page blobs, append blobs, GPv1 storage accounts (GPv1 is retiring Oct 13, 2026), Archive tier (smart tier only spans Hot/Cool/Cold)
- **Comparison with S3 Intelligent-Tiering**: Both auto-tier based on access inactivity. Smart tier covers Hot/Cool/Cold (no Archive automated transition); S3 IT covers Standard/IA/Archive Instant/Archive/Deep Archive. Azure charges a per-object monitoring fee for objects >128 KiB; S3 IT charges per-object monitoring for objects >128 KB. Neither service charges retrieval/transition fees within their automated range
- **Action**: Teams with unpredictable blob access patterns can now enable Smart tier instead of manually configuring lifecycle policies — similar savings, zero management overhead
- Updated: `providers/azure.md` (new Smart tier section), `comparisons/storage.md` (Azure auto-tiering updated from ❌ to ✅)

### ⏰ AWS: EC2 Capacity Blocks — Next Pricing Review in July 2026
- AWS pricing page confirms: **"current prices are scheduled to be updated next in July, 2026"**
- Current rates remain: p5e.48xlarge **$39.80/hr**, p5en.48xlarge **$41.61/hr** (most US regions); p5e.48xlarge US West (N. California) **$49.75/hr**
- P6-B200 Capacity Block: **$82.368/hr** (8× NVIDIA B200); P6-B300 Capacity Block: **$93.60/hr** (8× NVIDIA B300) — unchanged
- P6e UltraServer: **$761.904/hr** (72× NVIDIA B200, Dallas Local Zone) — unchanged
- No change to On-Demand, Savings Plans, or Spot pricing for these instance families
- Monitor: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/) — direction of July update unspecified (could be up or down)

### ✅ No new AWS base pricing changes found (as of 2026-05-26)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront all unchanged
- EC2 standard On-Demand rates (m5, c5, r5, Graviton3/4, Intel Xeon 6 families) all unchanged

### ✅ No new GCP pricing changes found (as of 2026-05-26)
- CDN Interconnect/Peering increases (effective May 1, 2026) in effect — no further changes
- A3 Ultra EU/Asia price increase (May 1, 2026) in effect — no further changes
- GCS multi-region pricing changes (Nearline +50%, Archive multi-region -40%) remain current
- Cloud Run, Cloud SQL, BigQuery, GKE pricing all unchanged

### ✅ No new Azure IaaS/PaaS pricing changes found (as of 2026-05-26)
- Azure Blob Storage 128 KiB minimum object size: still upcoming **July 1, 2026** (new accounts) / **July 1, 2027** (all accounts)
- Azure Functions v3 Linux Consumption enforcement: still upcoming **September 30, 2026**
- Microsoft 365 commercial pricing increases: still upcoming **July 1, 2026**
- Azure GPv1 storage account retirement: still upcoming **October 13, 2026**
- Azure Cache for Redis new-instance block (all customers): still upcoming **October 1, 2026**
- Azure Reserved VM Instances for legacy series discontinued: still upcoming **July 1, 2026**

---

## 2026-05-24

### 🆕 GCP: G4 Fractional GPU VMs — Generally Available (April 22, 2026)
- **GA: April 22, 2026** (announced in preview at GTC 2026, March 16, 2026)
- Three new G4 machine types using NVIDIA vGPU technology to slice the RTX PRO 6000 Blackwell GPU into smaller, proportionally priced units
- Ideal for workloads that don't need a full 96 GB GPU — right-size costs by using exactly the GPU fraction needed

| Machine Type | GPU Fraction | vCPU | RAM | GPU Mem | Use Case |
|---|---|---|---|---|---|
| g4-standard-6 | 1/8 GPU | 6 | 22 GB | 12 GB | Remote desktops, entry-level AI streaming |
| g4-standard-12 | 1/4 GPU | 12 | 45 GB | 24 GB | Video transcoding, real-time data visualization |
| g4-standard-24 | 1/2 GPU | 24 | 90 GB | 48 GB | LLM inference, robotics sensor simulation |

- Pricing is proportional to the full `g4-standard-48` rate ($4.50/hr); fractional SKUs are priced accordingly (roughly $0.56/hr for 1/8, $1.13/hr for 1/4, $2.25/hr for 1/2 — confirm via [GCP GPU pricing page](https://cloud.google.com/compute/gpus-pricing))
- Not the same as MIG (Multi-Instance GPU): vGPU-based fractional slices share resources differently than MIG hardware partitioning
- Can be managed by GKE with advanced container bin-packing for higher utilization
- Available in same regions as G4: us-central1, us-west1, europe-west4
- Updated: `providers/gcp.md` (new fractional G4 table in G4 section)

### ⚠️ Azure: Reserved VM Instances for Legacy Series Discontinued — July 1, 2026
- **Announced: May 5, 2026** (Azure ID: 560948)
- Starting **July 1, 2026**, **new purchases and renewals** of Reserved VM Instances (1-yr and 3-yr) are **ending** for the following legacy VM series:
  - **Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2** — no RI purchases or renewals after July 1
  - **Dv3, Dsv3, Ev3, Esv3** — 1-yr and 3-yr RI purchases and renewals also end July 1
- Existing RIs continue through their **current term** and keep their discount — **but auto-renew will fail silently** and workloads will shift to pay-as-you-go at term expiry
- **Azure Savings Plans for Compute are not affected** — remain available for all VM series including newer equivalents (Dv5, Ev5, etc.)
- **Action required**: Audit RI inventory for impacted series, check expiry dates, and decide now whether to migrate workloads to newer VM generations or switch to a Savings Plan before July 1
- Updated: `providers/azure.md` (new entry in Upcoming Changes section)

### ✅ No new AWS pricing changes found (as of 2026-05-24)
- EC2 Capacity Blocks next scheduled review: **July 2026** — p5en.48xlarge US rate ($45.768/hr) and p5e.48xlarge rate ($39.799/hr) unchanged
- Lambda, S3, RDS, Aurora, EKS, DynamoDB pricing all unchanged
- Database Savings Plans (expanded to OpenSearch + Neptune in March 2026) unchanged
- No new instance type launches or pricing announcements since 2026-05-20

### ✅ No new GCP pricing changes found beyond items noted above (as of 2026-05-24)
- G4 fractional GPUs GA (April 22, 2026) documented — the only new GCP item since last update
- CDN Interconnect/Peering increases (May 1, 2026) in effect — no further changes
- N4A, G4, TPU v7 Ironwood pricing unchanged; BigQuery Fluid Scaling unchanged

### ✅ No new Azure IaaS/PaaS compute/storage pricing changes found (as of 2026-05-24)
- Azure Reserved VM Instance discontinuation (July 1, 2026) documented above
- Azure Blob Storage min 128 KiB object size: still upcoming July 1, 2026 (new accounts)
- Azure Functions v3 Linux Consumption enforcement: still upcoming September 30, 2026
- Microsoft 365 commercial pricing increase: still upcoming July 1, 2026
- Azure GPv1 retirement: still upcoming October 13, 2026
- Azure Cache for Redis existing-customer block: still upcoming October 1, 2026

---

## 2026-05-20

### 🆕 AWS: EC2 G7e Instances (NVIDIA RTX PRO 6000 Blackwell Server Edition) — Added to Tracking
- **GA: January 20, 2026** (US East N. Virginia, US East Ohio); expanded to **US West (Oregon) February 4, 2026**
- G7e instances deliver **up to 2.3× inference performance** vs the prior G6e generation
- GPU: **NVIDIA RTX PRO 6000 Blackwell Server Edition** — 96 GB GDDR7 VRAM per GPU (2× G6e), 1.85× GPU memory bandwidth, 4× inter-GPU and EFA networking bandwidth vs G6e
- Key use case: run 70B-parameter models (FP8 precision) on a **single GPU** ($3.36/hr)

| Instance | GPUs | vCPU | GPU Mem | $/hr (On-Demand) | $/hr (Spot) |
|---|---|---|---|---|---|
| g7e.2xlarge | 1 | 8 | 96 GB | $3.363 | ~$1.06 |
| g7e.4xlarge | 1 | 16 | 96 GB | ~$4.414 | ~$1.40 |
| g7e.8xlarge | 1 | 32 | 96 GB | ~$8.744 | ~$2.70 |
| g7e.12xlarge | 2 | 48 | 192 GB | ~$13.125 | ~$4.20 |
| g7e.24xlarge | 4 | 96 | 384 GB | $16.572 | ~$5.00 |
| g7e.48xlarge | 8 | 192 | 768 GB | $33.144 | ~$10.54 |

- Available via On-Demand, Spot Instances, and Savings Plans (no Reserved Instances yet)
- Supports NVIDIA GPUDirect P2P + RDMA with EFAv4 in EC2 UltraClusters (for multi-GPU multi-node workloads)
- EKS, ECS, Fargate supported; SageMaker AI support coming soon
- Updated: `providers/aws.md` (new G7e section in GPU table), `comparisons/compute.md` (new inference GPU table)

### 🆕 AWS: EC2 C8id, M8id, R8id — Local NVMe Storage Instances — Added to Tracking
- **GA: February 4, 2026**
- Powered by custom **Intel Xeon 6** processors; up to **22.8 TB local NVMe SSD** storage (3× more than prior-gen)
- 43% higher compute performance; 3.3× more memory bandwidth; 46% better I/O-intensive database perf vs C6id/M6id/R6id
- Supports **Instance Bandwidth Configuration** — flexible 25% allocation between network and EBS bandwidth
- **C8id**: compute-intensive — high-performance web servers, batch processing, distributed analytics, video encoding, gaming
- **M8id**: general purpose — application servers, microservices, enterprise apps, small/medium databases
- **R8id**: memory-intensive — in-memory databases, real-time analytics, large caches, scientific computing; also available in Europe (Frankfurt)
- Available in: US East (N. Virginia), US East (Ohio), US West (Oregon) + EU Frankfurt for R8id
- Purchase: On-Demand, Savings Plans, Spot Instances
- Updated: `providers/aws.md` (C8id added to Compute Optimized; R8id/M8id to Memory Optimized)

### 🆕 GCP: BigQuery Fluid Scaling — Generally Available (April 22, 2026)
- **GA launched at Google Cloud Next '26 (April 22, 2026)**
- Enables **per-second billing** with premier autoscaling: dynamically right-sizes compute allocation to match actual query demand
- Google-stated average: **up to 34% cost reduction** for teams using BigQuery autoscaling — no code or configuration changes required
- Mechanism: fluid scaling avoids over-provisioning for peak capacity; compute scales up when agents/queries are active, down when idle
- Also announced at Next '26: **BigQuery workload management features** — reservation groups (GA), dynamic assignments (preview), project-level slot controls (preview)
- Also announced: **35% YoY query speed improvement** and **40% YoY query processing cost reduction** from advanced runtime, small query, and history-based optimizations (GA)
- ⚠️ **August 11, 2026 (upcoming)**: BigQuery Data Transfer Service SKU billing label changes from uppercase `DATA_TRANSFER_SERVICE` to lowercase `data_transfer_service` — update billing exports, dashboards, and reporting queries to include both labels
- Updated: `providers/gcp.md` (BigQuery section — Fluid Scaling + upcoming label change)

### ✅ No new AWS base pricing changes found (as of 2026-05-20)
- EC2 Capacity Blocks next scheduled review: **July 2026** — no new rate changes since p5en.48xlarge US increase (~May 16, 2026)
- Lambda, S3, RDS, Aurora, EKS pricing all unchanged
- G7e On-Demand pricing confirmed: $3.363/hr (g7e.2xlarge) through $33.144/hr (g7e.48xlarge) — no changes since GA

### ✅ No new GCP pricing changes found (as of 2026-05-20)
- All May 1, 2026 changes (CDN Interconnect/Peering, A3 Ultra EU/Asia) remain in effect — no further changes
- G4 VM family, N4A, TPU v7 Ironwood pricing unchanged
- Cloud SQL, Cloud Run, Cloud Storage pricing unchanged
- BigQuery Fluid Scaling is a cost-reduction feature, not a pricing model change (rates unchanged)

### ✅ No new Azure IaaS/PaaS pricing changes found (as of 2026-05-20)
- Azure Blob Storage 128 KiB minimum object size: still upcoming July 1, 2026 (new accounts) / July 1, 2027 (all accounts)
- Azure Functions v3 Linux Consumption enforcement: still upcoming September 30, 2026
- Microsoft 365 commercial pricing increase: still upcoming July 1, 2026
- Azure GPv1 retirement: still upcoming October 13, 2026
- Azure Cache for Redis: all-customer new-instance creation block still upcoming October 1, 2026
- No new VM, Functions, SQL, CDN, or storage pricing announcements found

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
