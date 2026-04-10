# GCP Pricing Reference

> Last updated: 2026-04-10

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

### Notes on Discounts

- **Sustained Use Discounts (SUDs)**: Automatic discounts for N1, N2, N2D machine families when VMs run >25% of the month. Max discount ~30% at 100% monthly usage.
  - SUDs do **not** apply to E2, C3, or C4 families.
- **Committed Use Discounts (CUDs)**: Up to 57% off (1-yr), ~70% off (3-yr) for eligible machine series.
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

> ⚠️ **Effective May 1, 2026**: GCP is doubling CDN Interconnect / Direct Peering / Carrier Peering egress rates in North America and Europe, and ~42% increase in Asia.

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

### May 1, 2026 — GCP CDN Interconnect & Peering Price Increase
Announced January 27, 2026:
- CDN Interconnect egress (NA): $0.04 → **$0.08/GiB** (+100%)
- CDN Interconnect egress (EU): $0.05 → **$0.08/GiB** (+60%)
- CDN Interconnect egress (Asia): $0.06 → **$0.085/GiB** (+42%)
- Affects Direct Peering and Carrier Peering as well.
- Fixed-price contracts unaffected until renewal.

### March 2, 2026 — GKE Backup for GKE Pricing Change
- Management fee: per-Pod ($1.00/pod-mo) → **per-Namespace ($9.00/namespace-mo)**
- Backup storage: $0.028 → **$0.045/GiB-mo**

### May 1, 2026 — A3 Ultra GPU Price Increase (Europe and Asia)
Announced January 27, 2026:
- A3 Ultra (a3-ultragpu-8g) instances with 8× NVIDIA H200 GPUs will see list price increases in **Europe and Asia** regions only.
- US regions (e.g., us-central1: ~$86.76/hr) are **not affected**.
- Exact EU/Asia rates not yet published in public pricing pages; customers were notified via email.
- CUD (1-year and 3-year committed use) pricing also increases proportionally.
