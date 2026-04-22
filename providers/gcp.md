# GCP Pricing Reference

> Last updated: 2026-04-22

## Compute — Google Compute Engine (On-Demand, Linux, us-central1)

### General Purpose — E2 Series (cost-optimized)

| Machine Type | vCPU | RAM | $/hr | $/mo (730 hr) |
|---|---|---|---|---|
| e2-micro | 0.25–2 shared | 1 GB | $0.0084 | $6.11 |
| e2-small | 0.5–2 shared | 2 GB | $0.0168 | $12.26 |
| e2-medium | 1–2 shared | 4 GB | $0.0335 | $24.46 |
| e2-standard-2 | 2 | 8 GB | $0.0671 | $48.98 |
| e2-standard-4 | 4 | 16 GB | $0.1342 | $97.97 |
| e2-standard-8 | 8 | 32 GB | $0.2684 | $195.93 |

### General Purpose — N2 Series (balanced/flexible)

| Machine Type | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| n2-standard-2 | 2 | 8 GB | $0.0971 | $70.88 |
| n2-standard-4 | 4 | 16 GB | $0.1942 | $141.77 |
| n2-standard-8 | 8 | 32 GB | $0.3884 | $283.53 |
| n2-standard-16 | 16 | 64 GB | $0.7769 | $567.14 |

### General Purpose — N4 Series (newer generation)

| Machine Type | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| n4-standard-2 | 2 | 8 GB | $0.0974 | $71.10 |
| n4-standard-4 | 4 | 16 GB | $0.1949 | $142.28 |

### General Purpose — N4A Series (Google Axion ARM, GA Jan 26, 2026) 🆕

Powered by Google's custom-designed **Axion processor** (Arm Neoverse N3). Generally available as of January 26, 2026. Google claims up to 2× better price-performance than comparable x86 VMs.

| Machine Type | vCPU | RAM | $/hr | $/mo (730 hr) |
|---|---|---|---|---|
| n4a-standard-1 | 1 | 4 GB | $0.0385 | $28.11 |
| n4a-standard-2 | 2 | 8 GB | $0.0770 | $56.21 |
| n4a-standard-4 | 4 | 16 GB | $0.1540 | $112.42 |
| n4a-standard-8 | 8 | 32 GB | $0.3080 | $224.84 |
| n4a-standard-16 | 16 | 64 GB | $0.6160 | $449.68 |
| n4a-standard-32 | 32 | 128 GB | $1.2320 | $899.36 |
| n4a-standard-64 | 64 | 256 GB | $2.464 | $1,798.72 |

High-CPU variant: `n4a-highcpu-2` (2 vCPU / 4 GB) = **$0.0650/hr** ($47.45/mo)

- SUDs do **not** apply to N4A
- 1-year CUD: ~28% off; 3-year CUD: ~45% off
- Spot VMs: up to 91% off
- Supports `standard`, `highmem`, `highcpu`, and custom machine types (up to 64 vCPU / 512 GB)
- Available regions (GA): us-central1, us-east4, europe-west3, europe-west4, and expanding

### Notes on Discounts

- **Sustained Use Discounts (SUDs)**: Automatic discounts for N1, N2, N2D machine families when VMs run >25% of the month. Max discount ~30% at 100% monthly usage.
  - SUDs do **not** apply to E2, C3, or C4 families.
- **Committed Use Discounts (CUDs)**: Up to 57% off (1-yr), ~70% off (3-yr) for eligible machine series.
- **Compute Flexible CUDs** (spend-based): Cover Compute Engine, GKE Autopilot, GKE Standard, and **Cloud Run** under a single cross-product commitment. Apply to any region + project in a billing account.
  - 🆕 **February 6, 2026**: Expanded coverage automatically migrated to all Cloud Billing accounts — no opt-in needed.
  - 🆕 **January 2026**: GCP migrated spend-based CUDs from a **credit-based model** to a **direct discounted price model** — bills now show the discounted rate directly rather than full price + credit offset. Invoices look different from pre-2026 months; no actual cost change.
  - Also expanded to cover H3 and memory-optimized (M-series) VMs.
- **Spot VMs**: 60–91% off on-demand price for fault-tolerant, interruptible workloads.
- Billing is **per second** (minimum 1 minute).

---

## Serverless — Cloud Run Functions (2nd Gen, us-central1)

| Component | Price |
|---|---|
| Requests | $0.40 / million |
| vCPU-time | $0.00002400 / vCPU-second |
| Memory | $0.0000025 / GB-second |
| Networking (outbound) | $0.12 / GB |

**Free tier (permanent)**:
- 2 million invocations/month
- 400,000 GB-seconds memory/month
- 200,000 vCPU-seconds/month
- 5 GB network egress/month

### 1st Gen Functions (legacy)

| Component | Price |
|---|---|
| Invocations | $0.40 / million |
| Compute time | $0.0000100 / GHz-second |
| Memory | $0.0000025 / GB-second |
| Networking (outbound) | $0.12 / GB |

---

## Storage — Google Cloud Storage (us-central1)

### Storage Classes

| Class | $/GB-mo | Min Storage Duration | Retrieval Fee | Use Case |
|---|---|---|---|---|
| Standard | $0.020 | None | None | Frequently accessed |
| Nearline | $0.010 | 30 days | $0.01/GB | < 1×/mo access |
| Coldline | $0.004 | 90 days | $0.02/GB | < 1×/qtr access |
| Archive | $0.0012 | 365 days | $0.05/GB | Long-term archival |

> ⚠️ Early deletion fees apply if data is moved/deleted before the minimum duration.

### Data Transfer

| Transfer | Cost |
|---|---|
| Ingress (all) | Free |
| Egress within same region | Free |
| Egress to another GCP region (N. America ↔ Europe) | ~$0.05/GiB |
| Egress to Internet (per GiB) | $0.08–$0.15 depending on region |
| CDN Interconnect egress (after May 1, 2026): North America | **$0.08/GiB** (was $0.04) |
| CDN Interconnect egress (after May 1, 2026): Europe | **$0.08/GiB** (was $0.05) |
| CDN Interconnect egress (after May 1, 2026): Asia | **$0.085/GiB** (was $0.06) |

> ⚠️ **Effective May 1, 2026 (9 days away)**: GCP is doubling CDN Interconnect / Direct Peering / Carrier Peering egress rates in North America and Europe, and ~42% increase in Asia.

---

## Databases

### Cloud SQL (PostgreSQL, us-central1, on-demand)

| Instance | vCPU | RAM | $/hr | $/mo |
|---|---|---|---|---|
| db-f1-micro | shared | 0.6 GB | $0.0150 | $10.95 |
| db-g1-small | shared | 1.7 GB | $0.0500 | $36.50 |
| db-custom-2-4096 | 2 | 4 GB | $0.1040 | $75.92 |
| db-custom-4-8192 | 4 | 8 GB | $0.2080 | $151.84 |
| db-custom-8-16384 | 8 | 16 GB | $0.4160 | $303.68 |

Storage: $0.17/GB-mo (SSD). Backups: $0.08/GB-mo.

### Cloud Spanner

$0.90/node-hour (regional). $3.00/node-hour (multi-region). $0.30/GB-mo storage.

### Firestore (formerly Datastore)

| Operation | Price |
|---|---|
| Reads | $0.06 / 100,000 |
| Writes | $0.18 / 100,000 |
| Deletes | $0.02 / 100,000 |
| Storage | $0.18/GB-mo |

Free tier: 50,000 reads + 20,000 writes + 20,000 deletes + 1 GB storage/day.

### BigQuery

| Component | Price |
|---|---|
| On-demand queries | $5.00/TB scanned |
| Streaming inserts | $0.01/200 MB |
| Active logical storage | $0.02/GB-mo |
| Long-term logical storage | $0.01/GB-mo |
| Multi-region data transfer (North America) | Varies by SKU (see note below) |

> ⚠️ **Effective February 1, 2026**: BigQuery jobs are now charged for **Cloud Storage multi-region data transfer fees** when a BigQuery job in one location reads data from a multi-region Cloud Storage bucket. This was previously not billed due to a billing alignment gap.  
> - Affected SKUs: `3C8A-99C5-F47B` (North America), `D46A-868A-BBF7` (Europe), `990F-BF38-8D3C` (Asia)  
> - Mitigation: Co-locate Cloud Storage buckets with BigQuery datasets. Use [bucket relocation](https://cloud.google.com/storage/docs/bucket-relocation/overview) to move existing buckets.

Free tier: 1 TB queries/month + 10 GB active storage/month (always free).

### Memorystore (Redis)

| Tier | $/GB-hr |
|---|---|
| Basic | $0.049 |
| Standard | $0.098 |

---

## Free Tier (Always Free)

| Service | Free Allowance |
|---|---|
| Compute Engine | 1× e2-micro VM/mo (us-central1, us-west1, or us-east1) |
| Cloud Storage | 5 GB regional storage/mo |
| BigQuery | 1 TB queries/mo + 10 GB storage/mo |
| Cloud Run Functions | 2M invocations + 400K GB-s + 200K vCPU-s/mo |
| Cloud Firestore | 1 GB + 50K reads + 20K writes/day |
| Pub/Sub | 10 GB messages/mo |
| Cloud Shell | 5 GB persistent disk |

New accounts also receive **$300 in free credits** (90-day expiry).

---

## Upcoming Changes

### ⚠️ May 1, 2026 — GCP CDN Interconnect & Peering Price Increase (9 days away)
Announced January 27, 2026:
- CDN Interconnect egress (NA): $0.04 → **$0.08/GiB** (+100%)
- CDN Interconnect egress (EU): $0.05 → **$0.08/GiB** (+60%)
- CDN Interconnect egress (Asia): $0.06 → **$0.085/GiB** (+42%)
- Affects Direct Peering and Carrier Peering as well.
- Fixed-price contracts unaffected until renewal.
- **Action required**: Review billing, update budgets. Customers on Direct/Carrier Peering should evaluate migrating to a Verified Peering Provider (VPP) which offers SLAs and is Google's recommended alternative.

### February 11, 2026 — Vertex AI Agent Engine: Sessions, Memory Bank & Code Execution Now Billed (Now Active)
Announced January 26, 2026 (delayed from January 28):
- **Vertex AI Agent Engine Sessions**: $0.25 per 1,000 stored session events (with content)
- **Vertex AI Agent Engine Memory Bank**: billed per memory stored/retrieved (vCPU + memory rate)
- **Vertex AI Agent Engine Code Execution**: $0.0864/vCPU-hour + $0.0090/GiB-hour (same rate as runtime)
- **Runtime (existing billing, always-on)**: vCPU free up to 50 hrs/mo ($0.0864/hr beyond); RAM free up to 100 GiB-hrs/mo ($0.009/GiB-hr beyond)
- Idle agents and idle time are **not** billed (billing only for active requests/sessions)
- System control events (checkpoints, etc.) are **not** billed for sessions
- Code Execution went GA on February 18, 2026
- Impact: AI/ML teams using multi-agent pipelines with sessions + memory will now see new charges on monthly bills

### February 1, 2026 — BigQuery + Cloud Storage Multi-Region Transfer Billing (Now Active)
- BigQuery jobs reading from multi-region Cloud Storage buckets now incur **multi-region data transfer fees**
- Previously not billed due to a billing alignment gap
- Impacted SKUs: `3C8A-99C5-F47B` (North America), `D46A-868A-BBF7` (Europe), `990F-BF38-8D3C` (Asia)
- Mitigation: Co-locate Cloud Storage buckets with BigQuery datasets using bucket relocation

### March 2, 2026 — GKE Backup for GKE Pricing Change
- Management fee: per-Pod ($1.00/pod-mo) → **per-Namespace ($9.00/namespace-mo)**
- Backup storage: $0.028 → **$0.045/GiB-mo**

### May 1, 2026 — A3 Ultra GPU Price Increase (Europe and Asia)
Announced January 27, 2026:
- A3 Ultra (a3-ultragpu-8g) instances with 8× NVIDIA H200 GPUs will see list price increases in **Europe and Asia** regions only.
- US regions (e.g., us-central1: ~$86.76/hr) are **not affected**.
- Exact EU/Asia rates not yet published in public pricing pages; customers were notified via email.
- CUD (1-year and 3-year committed use) pricing also increases proportionally.
