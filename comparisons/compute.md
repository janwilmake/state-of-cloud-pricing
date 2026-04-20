# Compute Pricing Comparison — AWS vs GCP vs Azure

> Last updated: 2026-04-20  
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

## Entry-Level / Free-Tier Eligible

| Provider | Instance | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | t3.micro | 2 | 1 GB | $0.0104 | $7.59 | 12-mo free eligible |
| GCP | e2-micro | 0.25–2 shared | 1 GB | $0.0084 | $6.11 | Always free (select regions) |
| Azure | B1ls | 1 | 0.5 GB | $0.0052 | $3.80 | 12-mo free eligible |
| Azure | B1s | 1 | 1 GB | $0.0104 | $7.59 | 12-mo free eligible |

## GPU / ML Instances — H100 / H200

| Provider | Instance | GPU | $/hr (On-Demand) | Notes |
|---|---|---|---|---|
| AWS | p5.48xlarge | 8× H100 | $98.32 | UltraCluster |
| AWS | p5e.48xlarge | 8× H200 | $98.32 on-demand; **$39.80** Capacity Block | ⚠️ CB rate raised Jan 2026 |
| AWS | p5en.48xlarge | 8× H200 | — | **$41.61** Capacity Block |
| AWS | u-p6e-gb200x72 (UltraServer) | 72× B200 | — | **$761.904/hr** Capacity Block ($10.582/GPU) 🆕 |
| GCP | a3-ultragpu-8g | 8× H200 | **$84.81** | us-central1 (confirmed Apr 2026); higher in EU/Asia after May 1 |
| GCP | a3-highgpu-8g | 8× H100 | ~$88.49 | us-central1 |
| GCP | a3-megagpu-8g | 8× H100 | ~$93.40 | us-central1 |
| Azure | Standard_ND96isr_H200_v5 | 8× H200 | ~$84.80 | West US 3 |

> ⚠️ **GCP A3 Ultra price increase effective May 1, 2026** (11 days away) for Europe and Asia regions (announced Jan 27, 2026). US rates unchanged.  
> 🆕 **April 2026**: AWS published P6e UltraServer pricing for NVIDIA B200 GPUs (Dallas Local Zone). Capacity Blocks next review: **July 2026** (April review passed with no change to H200 rates).

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
