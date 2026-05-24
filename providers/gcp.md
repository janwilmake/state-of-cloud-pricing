# GCP Pricing Reference

> Last updated: 2026-05-24

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

### Accelerator Optimized — G4 Series (NVIDIA RTX PRO 6000 Blackwell, GA Feb 2026) 🆕

Powered by **NVIDIA RTX PRO 6000 Blackwell** GPU (96 GB GDDR7 VRAM, 1.6 TB/s bandwidth, FP4/FP6 support). Purpose-built for inference workloads; can serve 70B+ parameter models without infrastructure management. Also available on Cloud Run (serverless GPUs).

#### Fractional G4 (GA April 22, 2026) 🆕

Fractional G4 VMs use NVIDIA vGPU technology to slice a single RTX PRO 6000 into smaller units — useful for lightweight inference, remote desktops, video transcoding, and workloads that don't need a full 96 GB GPU.

| Machine Type | GPU Fraction | vCPU | RAM | GPU Mem | Use Case |
|---|---|---|---|---|---|
| g4-standard-6 | 1/8 GPU | 6 | 22 GB | 12 GB | Remote desktops, entry-level streaming |
| g4-standard-12 | 1/4 GPU | 12 | 45 GB | 24 GB | Video transcoding, real-time data viz |
| g4-standard-24 | 1/2 GPU | 24 | 90 GB | 48 GB | LLM inference, robotics simulation |

> ⚠️ Fractional G4 pricing is billed proportionally to the full `g4-standard-48` rate. Exact fractional per-hour rates not separately published; see [GCP GPU pricing page](https://cloud.google.com/compute/gpus-pricing) for current rates.

#### Full G4 (integer GPU)

| Machine Type | GPUs | vCPU | RAM | $/hr (On-Demand) | $/hr (Spot) | Notes |
|---|---|---|---|---|---|---|
| g4-standard-48 | 1× RTX PRO 6000 | 48 | 180 GB | $4.50 | $2.25 | us-central1 |
| g4-standard-96 | 2× RTX PRO 6000 | 96 | 360 GB | $9.00 | $4.50 | us-central1 |
| g4-standard-192 | 4× RTX PRO 6000 | 192 | 720 GB | $18.00 | $9.00 | us-central1 |
| g4-standard-384 | 8× RTX PRO 6000 | 384 | 1,440 GB | $36.00 | $18.00 | us-central1 |

- **1-year CUD**: ~20% off on-demand; **3-year CUD**: ~46% off on-demand
- Available in us-central1, us-west1, europe-west4 (and expanding)
- Also available as **RTX PRO 6000 Virtual Workstation** attachment: $1.09565/GPU/hr (1-yr CUD: $0.756/hr, 3-yr: $0.482/hr)
- **Cloud Run GPU** (serverless, no reservation required): $0.00036522/second/GPU (no zonal redundancy); $0.00056913/second/GPU (with zonal redundancy). Requires min 20 vCPU + 80 GiB RAM per instance. Preview available in us-central1, europe-west4, and limited in asia-south2, asia-southeast1.

> 🆕 **February 3, 2026**: Cloud Run G4 (RTX PRO 6000) support launched in preview. GPUs pre-installed with NVIDIA drivers; instances start in ~5 seconds. No reservations required.  
> 🆕 **April 22, 2026 (GA)**: **Fractional G4 VMs** now generally available — 1/8, 1/4, and 1/2 GPU slices using NVIDIA vGPU technology. Announced in preview at GTC 2026 (March 2026). Priced proportionally to the full G4 rate; no separate per-slice pricing SKU. Available where G4 is available (us-central1, us-west1, europe-west4).  
> Also available as standalone Compute Engine G4 VM instances, announced at Google Cloud Next '26 (April 22, 2026).

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

### Cloud Run GPU Pricing (instance-based billing) 🆕

Cloud Run supports attached GPUs for AI inference workloads. Instance-based billing — billed per second for the entire instance lifecycle (including idle minimum instances). No per-request fees for GPU; no reservations required.

| GPU Type | $/second (No Zonal Redundancy) | $/second (Zonal Redundancy) | $/hr approx. |
|---|---|---|---|
| NVIDIA L4 | $0.0001867 | $0.0002909 | ~$0.67 / ~$1.05 |
| NVIDIA RTX PRO 6000 Blackwell 🆕 | $0.00036522 | $0.00056913 | ~$1.31 / ~$2.05 |

> CPU and memory costs are billed separately (see Services pricing above). NVIDIA RTX PRO 6000 instances require min 20 vCPU + 80 GiB RAM.  
> 🆕 **February 3, 2026**: RTX PRO 6000 support added to Cloud Run (preview). Available in us-central1, europe-west4; limited in asia-south2, asia-southeast1.  
> At Next '26 (April 22, 2026), NVIDIA RTX PRO 6000 on Cloud Run highlighted as a key inference platform alongside GKE Agent Sandbox.

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

**Regional (single region, e.g. us-central1):**

| Class | $/GB-mo | Min Storage Duration | Retrieval Fee | Use Case |
|---|---|---|---|---|
| Standard | $0.020 | None | None | Frequently accessed |
| Nearline | $0.010 | 30 days | $0.01/GB | < 1×/mo access |
| Coldline | $0.004 | 90 days | $0.02/GB | < 1×/qtr access |
| Archive | $0.0012 | 365 days | $0.05/GB | Long-term archival |

**Multi-region (US/EU) — 2026 updated rates:**

| Class | $/GB-mo | Notes |
|---|---|---|
| Standard | $0.026 | Multi-region redundancy |
| Nearline | **$0.015** | ⬆️ **Increased in 2026** (was $0.010) |
| Coldline | $0.007 | |
| Archive | **$0.0024** | ⬇️ **Decreased in 2026** (was $0.004) |

> ⚠️ Early deletion fees apply if data is moved/deleted before the minimum duration.
> 
> ⚠️ **2026 multi-region price changes**: Nearline multi-region increased $0.010 → **$0.015/GB** (+50%); Archive multi-region decreased $0.004 → **$0.0024/GB** (-40%). Review lifecycle policies if you use multi-region Nearline or Archive.

### Data Transfer

| Transfer | Cost |
|---|---|
| Ingress (all) | Free |
| Egress within same region | Free |
| Egress to another GCP region (N. America ↔ Europe) | ~$0.05/GiB |
| Egress to Internet (per GiB) | $0.08–$0.15 depending on region |
| CDN Interconnect egress (North America, **as of May 1, 2026**) | **$0.08/GiB** (was $0.04) |
| CDN Interconnect egress (Europe, **as of May 1, 2026**) | **$0.08/GiB** (was $0.05) |
| CDN Interconnect egress (Asia, **as of May 1, 2026**) | **$0.085/GiB** (was $0.06) |

> ⚠️ **NOW ACTIVE (effective May 1, 2026)**: GCP CDN Interconnect / Direct Peering / Carrier Peering egress rates doubled in North America (+100%), +60% in Europe, and +42% in Asia. Standard internet egress rates are unchanged. Consider migrating to a Verified Peering Provider (VPP) if still on Direct/Carrier Peering.

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

> 🆕 **April 22, 2026 (GA)**: **BigQuery Fluid Scaling** — per-second billing with a premier autoscaling model for highly variable/agentic workloads. Dynamically adjusts compute allocation to match actual query demand. Google states up to **34% average cost reduction** for teams already running BigQuery autoscaling. Available now; no code or schema changes required. If autoscaling is not yet enabled, enabling it now is more financially attractive than before. Note: the 34% figure is an average — actual savings vary by query pattern. Monitor BigQuery billing weekly for the first 30 days after enabling to establish the new baseline before resizing CUD commitments.
> ⚠️ **Effective February 1, 2026**: BigQuery jobs are now charged for **Cloud Storage multi-region data transfer fees** when a BigQuery job in one location reads data from a multi-region Cloud Storage bucket. This was previously not billed due to a billing alignment gap.  
> - Affected SKUs: `3C8A-99C5-F47B` (North America), `D46A-868A-BBF7` (Europe), `990F-BF38-8D3C` (Asia)  
> - Mitigation: Co-locate Cloud Storage buckets with BigQuery datasets. Use [bucket relocation](https://cloud.google.com/storage/docs/bucket-relocation/overview) to move existing buckets.
> ⚠️ **August 11, 2026 (upcoming)**: BigQuery Data Transfer Service SKU billing label will change from uppercase (`DATA_TRANSFER_SERVICE`) to lowercase (`data_transfer_service`). Update billing exports, dashboards, and reporting queries to include both labels before this date.

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

### ✅ May 1, 2026 — GCP CDN Interconnect & Peering Price Increase (**NOW IN EFFECT**)
Announced January 27, 2026; effective May 1, 2026:
- CDN Interconnect egress (NA): $0.04 → **$0.08/GiB** (+100%)
- CDN Interconnect egress (EU): $0.05 → **$0.08/GiB** (+60%)
- CDN Interconnect egress (Asia): $0.06 → **$0.085/GiB** (+42%)
- Affects Direct Peering and Carrier Peering as well.
- Fixed-price contracts unaffected until renewal.
- Standard internet egress rates are **not** changed.
- Now reflected in May 2026 invoices. Customers still on Direct/Carrier Peering should evaluate migrating to a Verified Peering Provider (VPP) — Google's recommended alternative with SLAs.

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

### ✅ May 1, 2026 — A3 Ultra GPU Price Increase (Europe and Asia) — **NOW IN EFFECT**
Announced January 27, 2026; effective May 1, 2026:
- A3 Ultra (a3-ultragpu-8g) instances with 8× NVIDIA H200 GPUs: list price increased in **Europe and Asia** regions.
- US regions (e.g., us-central1: $84.81/hr on-demand) are **not affected**.
- Exact EU/Asia rates not separately published; customers were notified via email in January 2026.
- CUD (1-year and 3-year committed use) pricing also increased proportionally in affected regions.
- Now reflected in May 2026 invoices.

### Late 2027 — 8th-Generation TPUs (TPU 8t & TPU 8i)
Announced April 22, 2026 at Cloud Next '26. GA targeted for late 2027. No pricing announced yet. See the new section in the Google Cloud Next '26 Announcements block above.

---

## Google Cloud Next '26 Announcements (April 22–24, 2026)

### 🆕 TPU v7 Ironwood — Generally Available (April 22, 2026)

Google Cloud's seventh-generation TPU, **Ironwood**, is now GA. Announced at Cloud Next '25 (April 2025), it moved to GA at Cloud Next '26 (April 22, 2026). The first TPU purpose-built for inference at scale.

| Spec | Value |
|---|---|
| Peak FP8 compute (per chip) | 4.6 petaFLOPS |
| HBM3e memory (per chip) | 192 GB |
| Memory bandwidth (per chip) | 7.37 TB/s |
| Superpod scale | 9,216 chips = 42.5 exaFLOPS |
| vs. prior gen (Trillium) | ~4× performance per chip |

**Pricing**: Per chip-hour (see [GCP TPU pricing page](https://cloud.google.com/tpu/pricing)); on-demand, DWS Flex-start, DWS Calendar Mode, and 1-yr/3-yr CUD tiers available. Prices vary by region.

> Ironwood is the foundation of Google's AI Hypercomputer and powers Anthropic's Claude inference (1M+ chips). Up to 24× more compute per superpod than the world's current largest supercomputer (El Capitan).

### 🆕 8th-Generation TPUs — TPU 8t & TPU 8i (Announced April 22, 2026; GA ~late 2027)

Google announced the **first split-architecture TPU generation** at Cloud Next '26: separate chips optimized for training and inference.

| | TPU 8t (Training) | TPU 8i (Inference) |
|---|---|---|
| Codename | Sunfish | Zebrafish |
| Design partner | Broadcom | MediaTek |
| Process node | TSMC 2nm | TSMC 2nm |
| HBM | 8× 12-high HBM3e stacks | 6× HBM3e stacks |
| Key advantage | 2.7× training price-perf vs Ironwood | 80% inference price-perf vs Ironwood; 20–30% cheaper than 8t |
| GA target | Late 2027 | Late 2027 |

No public pricing announced. Interest form: [cloud.google.com/resources/tpu-interest](https://cloud.google.com/resources/tpu-interest)

### 🆕 A5X VM Family with NVIDIA Vera Rubin NVL72 (Announced April 22, 2026)

- New **A5X** VM family to be powered by NVIDIA Vera Rubin NVL72 (successor to Blackwell)
- Uses open-source **Falcon** networking protocol concepts
- Availability: later in 2026 (no GA date); pricing TBD
- Complements Google's own TPU roadmap with NVIDIA's latest GPU generation

### 🆕 C4A.metal — Axion Bare Metal (Preview, announced April 22, 2026)
- Google's **first Axion bare metal instance** — runs without hypervisor overhead
- Powers: Android development, automotive simulation, CI/CD pipelines, security workloads, custom hypervisors
- Strong hypervisor security boundary without performance overhead of nested virtualization
- Pricing: Not yet published; expected to be comparable to C4A VM pricing with bare-metal premium
- Available in Preview; no GA date announced

### 🆕 GKE Agent Sandbox (GA, announced April 22, 2026)
- Industry's first **native sandbox service** among hyperscalers for AI agent workloads
- Provides secure, isolated execution environments at machine speed for untrusted code and tool calls
- Runs on **Google Axion N4A** instances; claims up to **30% better price-performance** than comparable hyperscaler offerings
- Pricing: Standard GKE node pricing applies (N4A VM rate + GKE management fee); no Agent Sandbox surcharge announced
- Integrated with Cluster Director for automated orchestration

### 🆕 C4N & M4N VM Families (Preview, announced April 22, 2026) 🆕

**C4N** (compute-optimized with enhanced networking):
- Part of the 4th-generation Compute Engine portfolio; enhanced NIC bandwidth
- Optimized for: RL reward calculation, agent orchestration, nested visualization, Teradata analytics
- Preview access: [sign-up form](https://forms.gle/tx1XV2yDrbMrcWgo8)
- Pricing: Not yet published; expected similar to C4 family. Existing C4 resource-based CUDs do **not** automatically transfer — new CUD purchase required

**M4N** (memory-optimized with enhanced networking):
- Targeted at high-memory workloads that require high memory bandwidth per vCPU
- 26.57 GiB RAM per vCPU; can reduce Oracle TCO by >20% vs previous-gen with Hyperdisk Extreme
- Preview access: [sign-up form](https://docs.google.com/forms/d/e/1FAIpQLSeTBNw_Z5SkaeVlDMgbeFPnHS_wGsrTomEDO2cI6RIQlx93qA/viewform)
- Pricing: Not yet published. Existing M3 resource-based CUDs do **not** automatically transfer

> ⚠️ **CUD migration risk**: If you migrate workloads from C4 → C4N or M3 → M4N, any existing resource-based CUDs for C4/M3 no longer apply. Evaluate new CUD commitments before migrating.

### 🆕 Z4D Storage-Optimized VMs (Preview coming soon, announced April 22, 2026) 🆕

- New VM family optimized for **I/O-intensive workloads** (SQL, NoSQL, vector databases)
- Specs: up to **84 TiB local SSD** directly on-node, up to **400 Gbps VM-to-VM bandwidth**
- Ideal for: large-scale SQL/NoSQL/vector database workloads requiring low-latency storage
- Preview: expected soon (no date given); pricing not yet announced
- Different from Z4M (which uses 168 TiB and targets distributed parallel file systems / AI/ML)

### 🆕 Z4M Storage VMs (Preview expected Q3 2026, announced April 22, 2026)
- New VM/bare-metal family optimized for **distributed parallel file systems and large-scale AI/ML**
- Specs: up to **168 TiB local SSD**, up to **400 Gbps network bandwidth**, RDMA support, bare-metal shapes
- Will integrate with Cluster Director; can colocate with accelerator instances for low-latency data access
- Intended for: large-scale training data staging, parallel file system workloads (Lustre, GPFS, WekaIO)
- Pricing: Not yet announced; expected to be in Preview Q3 2026

### 🆕 Hyperdisk ML Throughput Increase (GA, April 22, 2026)
- **Aggregate throughput increased from 1.2 TiB/s → 2 TiB/s** — a ~67% improvement
- Claims 200× higher throughput per disk than competitive offerings
- No price change announced; existing Hyperdisk ML pricing remains in effect
- Also: **Hyperdisk Exapools** now GA — highest aggregate block storage performance per AI cluster of any hyperscaler; pricing varies by configuration
