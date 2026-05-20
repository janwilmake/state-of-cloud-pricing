# Compute Pricing Comparison — AWS vs GCP vs Azure

> Last updated: 2026-05-20  
> All prices are **on-demand, Linux, per hour** in primary US regions (us-east-1 / us-central1 / East US). Prices in USD.

## General Purpose — 2 vCPU / 8 GB RAM

| Provider | Instance | vCPU | RAM | $/hr | $/mo (730 hr) | Notes |
|---|---|---|---|---|---|---|
| AWS | m5.large | 2 | 8 GB | $0.0960 | $70.08 | Intel Xeon |
| AWS | m7g.large (Graviton3) | 2 | 8 GB | $0.0816 | $59.57 | ARM, ~15% cheaper |
| AWS | m8g.large (Graviton4) 🆕 | 2 | 8 GB | $0.0898 | $65.55 | ARM, up to 30% better perf vs Graviton3 |
| GCP | e2-standard-2 | 2 | 8 GB | $0.0671 | $48.98 | Cost-optimized |
| GCP | n2-standard-2 | 2 | 8 GB | $0.0971 | $70.88 | Balanced |
| GCP | n4-standard-2 | 2 | 8 GB | $0.0974 | $71.10 | Newer gen |
| GCP | n4a-standard-2 (Axion) 🆕 | 2 | 8 GB | $0.0770 | $56.21 | ARM, GA Jan 26 2026 |
| Azure | D2s v5 | 2 | 8 GB | $0.0960 | $70.08 | Intel |
| Azure | D2as v5 (AMD) | 2 | 8 GB | $0.0860 | $62.78 | EPYC Turin |

## General Purpose — 4 vCPU / 16 GB RAM

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | m5.xlarge | 4 | 16 GB | $0.1920 | $140.16 | Intel |
| AWS | m7g.xlarge (Graviton3) | 4 | 16 GB | $0.1632 | $119.14 | ARM |
| AWS | m8g.xlarge (Graviton4) 🆕 | 4 | 16 GB | $0.1795 | $131.04 | ARM Graviton4 |
| GCP | e2-standard-4 | 4 | 16 GB | $0.1342 | $97.97 | Cost-optimized |
| GCP | n2-standard-4 | 4 | 16 GB | $0.1942 | $141.77 | Balanced |
| GCP | n4a-standard-4 (Axion) 🆕 | 4 | 16 GB | $0.1540 | $112.42 | ARM Axion |
| Azure | D4s v5 | 4 | 16 GB | $0.1920 | $140.16 | Intel |
| Azure | D4as v5 (AMD) | 4 | 16 GB | $0.1720 | $125.56 | EPYC Turin |

## General Purpose — 8 vCPU / 32 GB RAM

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | m5.2xlarge | 8 | 32 GB | $0.3840 | $280.32 | Intel |
| AWS | m7g.2xlarge (Graviton3) | 8 | 32 GB | $0.3264 | $238.27 | ARM |
| AWS | m8g.2xlarge (Graviton4) 🆕 | 8 | 32 GB | $0.3590 | $262.07 | ARM Graviton4 |
| GCP | e2-standard-8 | 8 | 32 GB | $0.2684 | $195.93 | Cost-optimized |
| GCP | n2-standard-8 | 8 | 32 GB | $0.3884 | $283.53 | Balanced |
| GCP | n4a-standard-8 (Axion) 🆕 | 8 | 32 GB | $0.3080 | $224.84 | ARM Axion |
| Azure | D8s v5 | 8 | 32 GB | $0.3840 | $280.32 | Intel |

## Memory Optimized — 4 vCPU / 32 GB RAM

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | r5.xlarge | 4 | 32 GB | $0.2520 | $183.96 | |
| GCP | n2-highmem-4 | 4 | 32 GB | ~$0.2280 | ~$166.44 | Approx. |
| Azure | E4s v5 | 4 | 32 GB | $0.2520 | $183.96 | |

## Network/Storage-Optimized Compute — 2–4 vCPU

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Network | Notes |
|---|---|---|---|---|---|---|---|
| AWS | c8in.large (Intel Xeon 6) 🆕 | 2 | 4 GB | $0.1361 | $99.35 | 600 Gbps | GA Apr 2026; network-intensive |
| AWS | c8in.xlarge (Intel Xeon 6) 🆕 | 4 | 8 GB | $0.2722 | $198.71 | 600 Gbps | Highest net bandwidth EC2 instance |
| AWS | c8ib.xlarge (Intel Xeon 6) 🆕 | 4 | 8 GB | $0.2722 | $198.71 | — | 300 Gbps EBS; DB/file systems |

> 🆕 **April 16, 2026**: **C8in** (GA) — 600 Gbps network bandwidth (record for EC2 enhanced networking); up to 384 vCPUs; 43% better vs C6in. Best for distributed compute, large-scale analytics.  
> 🆕 **April 16, 2026**: **C8ib** (GA) — 300 Gbps EBS bandwidth (record for non-accelerated instances). Best for commercial databases and high-throughput file systems.  
> 🆕 **April 27, 2026**: **C8ine / M8ine** (GA) — network virtual appliance optimized; 2.5× packet performance/vCPU vs prior gen; virtual firewalls, load balancers, 5G UPF.

## Entry-Level / Free-Tier Eligible

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | t3.micro | 2 | 1 GB | $0.0104 | $7.59 | 12-mo free eligible |
| GCP | e2-micro | 0.25–2 shared | 1 GB | $0.0084 | $6.11 | Always free (select regions) |
| Azure | B1ls | 1 | 0.5 GB | $0.0052 | $3.80 | 12-mo free eligible |
| Azure | B1s | 1 | 1 GB | $0.0104 | $7.59 | 12-mo free eligible |

## GPU / ML Instances — Graphics & Inference (On-Demand, Single-to-Multi GPU)

| Provider | Instance | GPU | GPUs | $/hr (On-Demand) | $/GPU/hr | Notes |
|---|---|---|---|---|---|---|
| AWS | g7e.2xlarge 🆕 | RTX PRO 6000 | 1 | **$3.363** | $3.363 | GA Jan 20, 2026; 96 GB GDDR7 |
| AWS | g7e.8xlarge 🆕 | RTX PRO 6000 | 1 | **$8.744** | $8.744 | 32 vCPU / 256 GiB RAM |
| AWS | g7e.48xlarge 🆕 | RTX PRO 6000 | 8 | **$33.144** | $4.143 | 192 vCPU / 2 TiB RAM; 1600G EFA |
| GCP | g4-standard-48 🆕 | RTX PRO 6000 | 1 | **$4.50** | $4.50 | 48 vCPU / 180 GB RAM; us-central1 |
| GCP | g4-standard-384 🆕 | RTX PRO 6000 | 8 | **$36.00** | $4.50 | 384 vCPU / 1440 GB RAM |
| GCP | Cloud Run (G4) 🆕 | RTX PRO 6000 | 1 | **~$1.31** | $1.31 | Serverless; no redundancy; ~$4.72/hr with min 20 vCPU |

> AWS G7e vs GCP G4: AWS G7e comes with significantly more CPU and RAM per GPU (e.g., 8 vCPU/64 GiB at $3.36/hr vs GCP G4's 48 vCPU/180 GiB at $4.50/hr). For pure single-GPU inference at minimum footprint, AWS G7e.2xlarge wins on price; for workloads needing high-CPU alongside the GPU, GCP G4 offers better CPU/GPU ratio at moderate premium.
> GCP Cloud Run G4 is the cheapest option for intermittent inference with automatic scale-to-zero (no idle charges).

## GPU / ML Instances — H100 / H200 / Blackwell Training (Capacity Blocks / Large Scale)

| Provider | Instance | GPU | $/hr (On-Demand) | Notes |
|---|---|---|---|---|
| AWS | p5.48xlarge | 8× H100 | $98.32 | UltraCluster |
| AWS | p5e.48xlarge | 8× H200 | $98.32 on-demand; **$39.799** Capacity Block | ⚠️ CB rate raised Jan 2026 |
| AWS | p5en.48xlarge | 8× H200 | — | **$45.768/hr** (US) / **$41.612/hr** (EU/Asia) Capacity Block ⚠️ |
| AWS | p6-b200.48xlarge | 8× B200 | — | **$82.368/hr** Capacity Block ($10.296/GPU) |
| AWS | p6-b300.48xlarge 🆕 | 8× B300 | — | **$93.60/hr** Capacity Block ($11.70/GPU) |
| AWS | u-p6e-gb200x72 (UltraServer) | 72× B200 | — | **$761.904/hr** Capacity Block ($10.582/GPU) |
| GCP | a3-ultragpu-8g | 8× H200 | **$84.81** | us-central1; higher in EU/Asia after May 1, 2026 |
| GCP | a3-highgpu-8g | 8× H100 | ~$88.49 | us-central1 |
| GCP | a3-megagpu-8g | 8× H100 | ~$93.40 | us-central1 |
| Azure | Standard_ND96isr_H200_v5 | 8× H200 | ~$84.80 | West US 3 |

> ✅ **GCP A3 Ultra price increase NOW IN EFFECT (as of May 1, 2026)** for Europe and Asia regions (announced Jan 27, 2026). US rates unchanged ($84.81/hr on-demand for us-central1).  
> 🆕 **January 20, 2026 (GA)**: AWS **G7e** family — NVIDIA RTX PRO 6000 Blackwell Server Edition (96 GB GDDR7). Up to 2.3× inference perf vs G6e. On-Demand + Spot + Savings Plans. Regions: US East (N. Virginia), US East (Ohio), US West (Oregon). Use case: cost-effective inference including 70B-param models on a single GPU at $3.36/hr.  
> 🆕 **May 2026**: AWS published **P6-B300** Capacity Block pricing: $93.60/hr per 8× B300 instance ($11.70/GPU). Available in US West (Oregon) and US East (N. Virginia).  
> 🆕 **April 22, 2026**: GCP **G4 VM family** (NVIDIA RTX PRO 6000 Blackwell) announced at Cloud Next '26; pricing published ($4.50/hr per GPU in g4-standard-48). Also available on Cloud Run serverless at ~$1.31/hr/GPU (no-redundancy) with no reservations required.  
> 🆕 **April 22, 2026**: GCP **Ironwood (TPU v7) now GA**. 4.6 PFLOPS/chip, 192 GB HBM3e, 9,216-chip superpods = 42.5 exaFLOPS. Purpose-built for inference. See `providers/gcp.md` for pricing details.  
> 🆕 **April 22, 2026**: GCP **TPU 8t + TPU 8i announced** (8th-gen); training vs inference split; TSMC 2nm; GA targeted late 2027. No pricing yet.  
> 🆕 **April 22, 2026**: GCP **A5X** announced — future VM family powered by NVIDIA Vera Rubin NVL72; no pricing or GA date yet.  
> 🆕 **April 22, 2026**: GCP announced **C4N** (compute-optimized enhanced networking) and **M4N** (memory-optimized enhanced networking) VM families — both in Preview. No pricing published yet. Existing C4/M3 resource-based CUDs do **not** transfer to these new families; new commitments required.  
> ⚠️ **~May 2026**: AWS **p5en.48xlarge** US region Capacity Block rate increased ~+10%: $41.612 → **$45.768/hr** in US East/West. EU/Asia remains $41.612/hr. p5e rates unchanged.  
> 🔜 **July 2026**: Next AWS Capacity Blocks pricing review.

## Managed Kubernetes — Control Plane Pricing

| Provider | Service | Base Fee | Notes |
|---|---|---|---|
| AWS | EKS (standard) | $0.10/hr (~$73/mo) | Standard or Extended ($0.60/hr) version support |
| AWS | EKS Provisioned Control Plane XL 🆕 | +$1.65/hr (~$1,205/mo add-on) | Dedicated capacity; 99.99% SLA |
| AWS | EKS Provisioned Control Plane 8XL 🆕 | +$13.90/hr (~$10,147/mo add-on) | Largest tier; 13,600 API seats; GA Mar 20, 2026 |
| GCP | GKE Standard/Autopilot | $0.10/hr (~$73/mo) per cluster | First zonal cluster free |
| Azure | AKS | Free | Pay only for VM nodes |

> 🆕 **March 20, 2026**: AWS EKS 8XL Provisioned Control Plane tier launched. SLA upgraded to 99.99% for all Provisioned tiers (up from 99.95% for standard). Tiers range from XL ($1.65/hr add-on) through 8XL ($13.90/hr add-on).

## Commitment / Savings Summary

| Provider | 1-yr Commitment | 3-yr Commitment | Spot/Preemptible |
|---|---|---|---|
| AWS | ~40% off (Reserved) | ~60–62% off | 60–90% off |
| GCP | ~57% off (CUD) | ~70% off (CUD) | 60–91% off (Spot VMs) |
| Azure | ~36–45% off (Reserved) | up to ~72% off | up to ~85% off (Spot) |
| GCP SUDs | Auto discount up to 30% (N1/N2 families) | — | — |

> GCP Sustained Use Discounts (SUDs) apply automatically to eligible VM families (N1, N2, N2D) when running >25% of the month. SUDs do **not** apply to E2, C3, or C4 families.
