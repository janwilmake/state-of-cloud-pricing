# Changelog

> Pricing changes tracked by the Cloud Pricing Tracker agent. Newest entries first.

---

## 2026-09-05

### 🆕 AWS: EC2 R9g / R9gd (Graviton5) — Memory-Optimized family GA (Effective August 31, 2026)

- **GA: August 31, 2026** ([AWS News Blog](https://aws.amazon.com/blogs/aws/amazon-ec2-r9g-and-r9gd-instances-powered-by-aws-graviton5-processors-are-now-generally-available/); [What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-r9g-and-r9gd-memory-optimized-instances-are-now-available/)) — the **third (and final major) AWS Graviton5** instance line, after **C9g** (Jul 2026) and **M9g** (Jun 10, 2026). **R9g** = memory-optimized; **R9gd** = R9g + up to **11.4 TB local NVMe**.
- **Silicon**: same Graviton5 chip — 192 cores/chip, Armv9.2-A @ 3.3 GHz, **5× larger L3 cache** vs Graviton4, first AWS CPU with **PCIe Gen 6 + DDR5-8800**; 6th-gen **Nitro System** incl. formally-verified **Nitro Isolation Engine**. Up to **25% better compute** vs Graviton4 R8g → **30% faster databases**, **35% faster web apps**, **35% faster ML**.
- **Sizes**: 12 sizes, `r9g.medium` (1 vCPU / 8 GiB) → `r9g.48xlarge` & `metal-48xl` (192 vCPU / **1.5 TiB**). **1 vCPU = 8 GiB RAM** (vs 4 GiB on M9g, 2 GiB on C9g). Network up to **100 Gbps** (48xl); EBS up to **72 Gbps** (>2× R8g); **Instance Bandwidth Configuration** shifts up to 25% between EBS/network.
- **Pricing (Linux, on-demand, us-east-1)** — a **uniform +9.0% over R8g** across all 11 sizes (the same premium rate as C9g/C8g and M9g/M8g); ~**$0.0642/vCPU-hr**:

| Instance | vCPU | RAM | $/hr (On-Demand) | $/hr (Spot) | $/mo (730 hr) | vs R8g |
|---|---|---|---|---|---|---|
| r9g.medium | 1 | 8 GiB | $0.0642 | — | $46.87 | +9.0% |
| r9g.large | 2 | 16 GiB | $0.1284 | $0.054 | $93.74 | +9.0% |
| r9g.xlarge | 4 | 32 GiB | $0.2568 | — | $187.48 | +9.0% |
| r9g.2xlarge | 8 | 64 GiB | $0.5137 | — | $374.99 | +9.0% |
| r9g.4xlarge | 16 | 128 GiB | $1.0274 | — | $750.00 | +9.0% |
| r9g.48xlarge | 192 | 1,536 GiB | $12.3283 | — | $8,999.66 | +9.0% |

> **R9gd** is priced at a premium over R9g (local NVMe) — verify on the [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/). **No Reserved Instances** — commitments via **Compute Savings Plans** (~20–30% off, 1-yr no-upfront). Spot ~57–60% off on-demand. GA regions: **US East (N. Virginia), US East (Ohio), US West (Oregon), Europe (Frankfurt)** — expanding.
- **FinOps**: for new memory-optimized Linux workloads (Redis/Memcached, in-memory DBs, real-time analytics), prefer **R9g** over R8g where available — ~25% faster for ~9% more $/hr → better price-perf. Stay on R8g only where R9g isn't yet offered. R9gd for data-logging/open-source-DB workloads needing low-latency local storage.
- Sources: [AWS News Blog (Aug 31, 2026)](https://aws.amazon.com/blogs/aws/amazon-ec2-r9g-and-r9gd-instances-powered-by-aws-graviton5-processors-are-now-generally-available/); [AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-r9g-and-r9gd-memory-optimized-instances-are-now-available/); [Vantage r9g.large = $0.12842 on-demand / $0.054 spot](https://instances.vantage.sh/aws/ec2/r9g.large); [DevelopersIO pricing check (Sep 2, 2026) — uniform +9.0% over R8g](https://dev.classmethod.jp/en/articles/ec2-r9g-graviton5-instance-launch/); [SiliconANGLE](https://siliconangle.com/2026/08/31/aws-targets-data-intensive-workloads-with-graviton5-powered-r9g-and-r9gd-instances)
- Updated: `providers/aws.md` (new R9g/R9gd top callout + Memory-Optimized table rows + note block), `comparisons/compute.md` (r8g/r9g.xlarge rows in Memory-Optimized table)

### ⚠️ Azure: Microsoft Foundry model-deployment regional/Data-Zone premiums — NOW IN EFFECT (September 1, 2026) — *adjacent (AI inference)*

- **Effective September 1, 2026** ([Foundry Blog, Jul 9 2026](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/microsoft-foundry-model-deployment-pricing-update/4535385)) — the Azure AI **Microsoft Foundry** model-deployment premiums flagged as upcoming in the 2026-08-29 changelog are now live. **Global** pricing is unchanged (still the cheapest); premiums apply to **EU Data Zone** and **Regional deployments outside the US**, plus a **new APAC Data Zone**:

| Deployment | Price vs. Global | Change |
|---|---|---|
| Global | same | No change |
| APAC Data Zone (new) | +20% | Newly available |
| EU Data Zone | +20% | Increasing by +9% |
| US Data Zone | +10% | No change |
| Regional — US | +10% | No change |
| Regional — outside US | +25% to +50% | Increasing by +7% to +16% (region-dependent) |

  - Regional breakdown vs. Global: **+25%** (Australia, India, Indonesia, Malaysia, NZ); **+30%** (Canada, Germany, Italy, Mexico, Spain, Sweden, Switzerland, UAE, et al.); **+35%** (Japan, Korea, Taiwan); **+40%** (France, Hong Kong, Israel, Norway, Qatar, UK); **+50%** (Brazil, EU North, EU West, Singapore).
  - **Grandfathering**: for Standard (PAYG), premiums apply **only to models launched on/after Sep 1, 2026** — customers staying on current models see no increase. For **Provisioned Throughput (PTU)**, the increase applies to **all** EU Data Zone / non-US Regional PTUs.
- **Scope note**: Foundry is **AI inference / model hosting — outside this KB's core compute/storage/serverless/DB/CDN scope** — confirmed as now-effective for FinOps completeness (it was previously flagged "effective September 1, 2026"). No Azure VM/Blob/Functions/SQL/CDN rate-card impact. Managed Compute GPU rates (A100 $4, H100 $8, MI300 $8 / compute-hr, Global) are unchanged.

### ✅ No new GCP base pricing changes (as of 2026-09-05)

- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — on-demand rates confirmed unchanged since 2026-08-15. The most recent cost-relevant GCP change remains the **Hyperdisk ML throughput-floor reduction (Aug 3, 2026)**. Google Cloud release notes (Aug 29 – Sep 5, 2026): no compute/storage/serverless/database/CDN rate-card changes; items were non-pricing (Managed Airflow 2.11 version-policy alignment; GCE MIG distribution monitoring dashboard; Vertex AI Search configurable-pricing threshold tweaks; COS/GKE version updates).

### ✅ No new Azure base pricing changes (as of 2026-09-05)

- VMs, Blob Storage, Azure SQL, AKS, App Service, CDN, Azure Functions — on-demand rates unchanged since the **Dl/D/E v7 248/372-vCPU GA (Aug 25, 2026)**. Early-September Azure updates were non-pricing feature/status items (Confidential VMs for Azure Linux; Azure Virtual Desktop Hybrid GA Sep 1; Azure CLI 2.90). The only cost-relevant effective-Sept-1 change is the **Foundry** AI premiums above (adjacent).

### 📝 AWS (week of Aug 31, 2026) — non-pricing items noted for completeness

- **AWS Lambda public preview runtimes** (Node.js 26, Python 3.15) — preview only, **no pricing change**; Lambda request/compute rates unchanged. Available in all commercial, GovCloud (US), and China regions. ([Weekly Roundup Aug 31](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-welcome-ducklabs-to-the-team-agentic-resource-discovery-ard-and-more-august-31-2026/))
- **ECS instance-health-aware task recovery** (Fargate / Managed Instances / ECS on EC2) — no additional cost. **Amazon EC2 turns 20** (retrospective only). AWS–DuckLabs (DuckDB) acquisition — analytics, no compute/storage rate impact.
- **Aug 28, 2026**: EC2 **P6-B300** (8× NVIDIA Blackwell Ultra) expanded to **Asia Pacific (Hyderabad)** and **South America (São Paulo)** — regional availability expansion of an already-GA, already-priced family; no rate-card change. ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-p6-b300-instances-available-additional-regions))

## 2026-08-29

### 🆕 Azure: 248 & 372 vCPU sizes for Dl/D/E v7 VMs — General Availability (Effective August 25, 2026)

- **GA: August 25, 2026** ([Azure Update 569546](https://azure.microsoft.com/en-us/updates?id=569546)) — the **largest sizes** of Azure's **Intel® Xeon® 6 (Granite Rapids)** `Dlsv7`/`Dsv7`/`Esv7` (and local-NVMe `Dldsv7`/`Ddsv7`/`Edsv7`) series are now generally available. The series itself GA'd up to 192 vCPU in May 2026; **the new 248 and 372 vCPU sizes** (scaling to **2.8 TiB memory**) complete the family.
- **What's new**: up to **20% better compute performance** than prior-generation Intel-based v6 VMs. At the **372 vCPU** size:
  - **Esv7 / Edsv7**: up to **400 Gbps** networking; up to **800k IOPS / 20 GBps** to Premium SSD v2 / Ultra Disk **remote** storage
  - **Ddsv7 / Edsv7** (local NVMe): up to **9.6M IOPS / 53 GBps** to **local NVMe** temp disk
- **Use cases**: larger in-memory databases, agentic AI workloads with larger context windows, lower-latency apps via fewer cross-node network hops.
- **GA regions (248/372)**: Central US, East US, East US 2, Germany West Central, South Central US, Sweden Central, West US 2, West US 3.
- **Pricing (East US, Linux, pay-as-you-go)** — Dsv7 is the **premium Intel** general-purpose line (~37% pricier than D2s v5 at 2 vCPU/8 GB, for ~20% more compute):

| Size | vCPU | RAM | $/hr (PAYG) | $/mo (730 hr) |
|---|---|---|---|---|
| Standard_D2s_v7 | 2 | 8 GiB | $0.1320 | $96.36 |
| Standard_D4s_v7 | 4 | 16 GiB | $0.2640 | $192.72 |
| Standard_D8s_v7 | 8 | 32 GiB | $0.5290 | $386.17 |
| Standard_D248s_v7 🆕 | 248 | 992 GiB | see [Azure VM pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/) | — |
| Standard_D372s_v7 🆕 | 372 | 1,488 GiB | see [Azure VM pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/) | — |

> Spot is available (e.g. D8s v7 Spot ≈ $0.0978/hr); Savings Plans (1-yr) and Reserved Instances apply. **No base-rate change for existing v7 sizes** — this is a **new largest-size tier** for an already-GA family. For 2 vCPU/8 GB general purpose, Dsv7 ($0.1320) is pricier than D2s v5 ($0.0960) and D2as v5 ($0.0860); pick v7 only when you need the Granite Rapids performance uplift.
- **FinOps context**: for the largest single-VM footprints (in-memory DBs, big-context agentic AI) the 372 vCPU / 2.8 TiB D/E v7 reduces cross-node network hops vs. sharding across smaller VMs. For everyday 2–8 vCPU general-purpose workloads, D2s/D2as v5 remain cheaper per hour.
- Sources: [Azure Update 569546 (Aug 25, 2026)](https://azure.microsoft.com/en-us/updates?id=569546); [Dsv7 sizes (learn.microsoft.com)](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/general-purpose/dsv7-series); [azurespeed.com D2s_v7 = $0.1320](https://www.azurespeed.com/AzureVmPricing/Regions/eastus); [Vantage D8s v7 = $0.529](https://instances.vantage.sh/azure/vm/d8s-v7)
- Updated: `providers/azure.md` (new Dl/D/E v7 section + top callout), `comparisons/compute.md` (Dsv7 rows)

### 📍 AWS: Graviton4 (C8gd/M8gd/R8gd) + R8a regional availability expansions (Aug 19–20, 2026) — no rate changes

- **Aug 19, 2026**: **EC2 R8a** (5th-Gen AMD EPYC "Turin", memory-optimized) now available in **Asia Pacific (Taipei)** — up to 30% higher perf / 19% better price-perf vs R7a. ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-r8a-asia-pacific-taipei/))
- **Aug 20, 2026**: **EC2 C8gd / M8gd / R8gd** (Graviton4 + up to 11.4 TB local NVMe) expanded to additional regions: **C8gd → Asia Pacific (Singapore)**; **M8gd → Mexico (Central) + Asia Pacific (Melbourne)**; **R8gd → Europe (Zurich)**. ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-c8gd-m8gd/))
- **Pricing**: No rate-card change — regional availability expansions of already-GA, already-priced families. Regional on-demand rates vary; verify on the [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/) by selecting the region.
- Updated: `providers/aws.md` (R8a Taipei + Graviton4-local-NVMe regional notes)

### 📍 AWS: New Availability Zone in Europe (London) — eu-west-2d (Aug 19, 2026)

- **Aug 19, 2026**: AWS added a **4th Availability Zone** (`eu-west-2d`) to the Europe (London) Region (`eu-west-2`), with next-gen AI/ML capacity (Trn3 + P6 accelerated instances) alongside general-purpose compute — improving fault isolation for 4-AZ HA architectures. **Standard Europe (London) Region pricing applies** — a capacity/fault-isolation expansion, not a rate change. ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/aws-new-availability-zone-europe/))
- Updated: `providers/aws.md` (London AZ note)

### 💸 AWS: Glue 6.0 — 30% price reduction (GA Aug 21, 2026) — *adjacent (serverless ETL)*

- **Aug 21, 2026**: **AWS Glue 6.0** GA — **30% lower per-DPU-hour pricing** than prior Glue versions, on a modernized runtime (Apache Spark 4.1, Python 3.13, Scala 2.13) with full **Apache Iceberg v3** support. Available in all regions where Glue operates. ([AWS News Blog](https://aws.amazon.com/blogs/aws/aws-glue-6-0-now-available-with-30-lower-price-and-full-apache-iceberg-v3-support/))
- **Scope note**: Glue is serverless ETL/analytics, **outside this KB's core compute/storage/functions/DB/CDN scope** — noted for FinOps completeness. No EC2/S3/Lambda/RDS/CloudFront rate impact.
- Also **Aug 22, 2026**: **Amazon Bedrock** reduced **OpenAI GPT-5.6 Sol** token pricing to **$4 / 1M input tokens** + **$20 / 1M output tokens** (AI inference — outside core scope). ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/bedrock-openai-gpt-56-sol-reduced-pricing/))

### 🆕 AWS: RDS for Oracle — Reserved Instances for R8i & M8i (GA Jul 31, 2026) — *belated catch-up*

- **Jul 31, 2026**: Amazon RDS for Oracle now offers **1-yr and 3-yr Reserved Instances** for **R8i** and **M8i** instance classes — **up to 53% savings** vs On-Demand. Available in all regions where those instance types are offered **except South America (São Paulo)**. ([What's New](https://aws.amazon.com/about-aws/whats-new/2026/07/amazon-rds-oracle-r8i-m8i/)) — not captured in prior changelog runs; added now.
- **FinOps**: for steady-state Oracle workloads on R8i/M8i, a 3-yr All-Upfront RI is the deepest discount path. RIs discount only the **instance compute** — not licenses, storage, or Extended Support surcharges. Compare against **Database Savings Plans** (cross-engine/cross-region flexibility) if your Oracle footprint fluctuates.
- Updated: `providers/aws.md` (RDS for Oracle R8i/M8i RI note)

### ✅ No new GCP base pricing changes (as of 2026-08-29)

- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — on-demand rates confirmed unchanged since 2026-08-15. The **Hyperdisk ML throughput-floor reduction (Aug 3, 2026)** remains the most recent cost-relevant GCP change.
- Google Cloud release notes (Aug 22–29, 2026): no compute/storage/serverless/database/CDN rate-card changes. Items were **non-pricing**:
  - **Google SecOps SOAR** 6.3.98 (Aug 29) and 6.3.96 (Aug 8) — security product releases.
  - **Managed Service for Apache Airflow** R35 rollout started Aug 20.
  - **Gemini 3.6 Flash** GA in US/EU multi-regions (Aug 18) — AI model, not infra pricing.
  - **Cloud Hub App Topology API** → usage-based billing **Sep 15, 2026** (with a daily free data-usage allotment) — network-observability product, outside this KB's core scope.
- ⚠️ Still upcoming: **NVIDIA P100 GPU end of support Sep 15, 2026** (~17 days away). Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4 VMs.

### 🆕 Azure (adjacent): SRE Agent 30-Day Trial + PostgreSQL Flexible Server Extended Support (Aug 24–26, 2026)

- **Aug 26, 2026**: **Azure SRE Agent 30-Day Trial** GA ([Azure 569760](https://azure.microsoft.com/en-us/updates?id=569760)) — new customers can create SRE Agents and pay **only for Azure Agent Units (AAUs) consumed when agents perform work**, with **no baseline always-on charges** during the trial. AI SRE assistant — outside core infra scope; noted as a new pricing offering.
- **Aug 24, 2026**: **Extended Support for Azure Database for PostgreSQL — Flexible Server** announced — a program to keep workloads secure/supported while transitioning to newer PostgreSQL versions (analogous to AWS RDS Extended Support; confirm per-vCPU surcharge rates on the [PostgreSQL Flexible Server pricing page](https://azure.microsoft.com/en-us/pricing/details/postgresql/flexible-server/)).
- Also **Aug 26, 2026**: **Azure SRE Agent VNet Integration** GA ([Azure 569695](https://azure.microsoft.com/en-us/updates?id=569695)) — feature GA, not pricing.
- Updated: `providers/azure.md` (SRE Agent trial + PostgreSQL Extended Support notes)

---

## 2026-08-22

### 🆕 AWS: EC2 M9g / M9gd (AWS Graviton5) — General Availability (Effective June 10, 2026) — *belated catch-up*

- **GA: June 10, 2026** ([AWS News Blog](https://aws.amazon.com/blogs/aws/now-available-amazon-ec2-m9g-and-m9gd-instances-powered-by-new-aws-graviton5-processors/); [about.amazon.com](https://www.aboutamazon.com/news/aws/aws-graviton-5-cpu-amazon-ec2)) — announced in preview at re:Invent 2025 (Dec 2025); **M9g and M9gd went GA on June 10, 2026** but had not been captured in prior changelog runs. Added now.
- **What it is**: the first **AWS Graviton5** instance family — **M9g** (general purpose) and **M9gd** (general purpose + local NVMe). 5th-gen Graviton: **192 cores/chip**, Armv9.2-A, **3.3 GHz**, **5× larger L3 cache** vs Graviton4, first AWS CPU to support **PCIe Gen 6** and **DDR5-8800** (fastest DDR5 in the cloud). Built on the 6th-gen **Nitro System** (incl. the new **Nitro Isolation Engine** — formally verified VM isolation).
- **Performance vs Graviton4 (M8g)**: up to **25% better compute**, **35% faster web apps**, **35% faster ML inference**, **30% faster databases**. Customer refs: ClickHouse +36% perf vs M8g (zero code changes); HubSpot MySQL query duration −60%; Honeycomb +36% throughput/core; CockroachDB −23% CPU + ~6% lower p99.
- **Pricing** (us-east-1, Linux, on-demand; **no Reserved Instances** — commitments via **Compute Savings Plans** ~20–30% off 1-yr no-upfront). Graviton5 prices **~9% higher per vCPU than Graviton4 (M8g)** but with ~25% more performance → better price-performance:

| Instance | vCPU | RAM | $/hr (On-Demand) | $/hr (Spot) | $/mo (730 hr) |
|---|---|---|---|---|---|
| m9g.medium | 1 | 4 GiB | $0.0489 | — | $35.70 |
| m9g.large | 2 | 8 GiB | $0.0978 | $0.042 | $71.39 |
| m9g.xlarge | 4 | 16 GiB | $0.1957 | $0.087 | $142.86 |
| m9g.2xlarge | 8 | 32 GiB | $0.3914 | $0.171 | $285.72 |
| m9g.4xlarge | 16 | 64 GiB | $0.7827 | — | $571.37 |
| m9g.8xlarge | 32 | 128 GiB | $1.5654 | — | $1,142.74 |
| m9g.48xlarge | 192 | 768 GiB | $9.3926 | $3.804 | $6,856.50 |

> Spot is **~57% off** on-demand (vs ~60–90% on older Graviton gens). 1 vCPU = 4 GiB RAM across all sizes; network up to 15 Gbps (medium/large/xlarge) → 100 Gbps (48xlarge); EBS up to 12 → 72 Gbps. **M9gd** = same compute + **up to 11.4 TB local NVMe SSD** (3× more than M8gd) with **30% higher IOPS** vs M8gd — for data logging, media processing, batch/log workloads. Pricing scales linearly at **~$0.0489/vCPU-hr**; verify exact M9gd rates on the [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/).
> **RDS also got Graviton5**: `db.m9g` instances are available (e.g. `db.m9g.large` ≈ $0.183/hr on-demand) — see [RDS pricing](https://aws.amazon.com/rds/pricing/).
- **GA regions (June 10, 2026)**: **US East (N. Virginia)**, **US East (Ohio)**, **US West (Oregon)**, **Europe (Frankfurt)** — expanding to additional regions; verify on the [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/).
- **FinOps context**: For new Linux/general-purpose workloads, M9g is now AWS's best price-performance general-purpose ARM option. M9g is ~9% pricier per hour than M8g but ~25% faster — migrate to M9g (not M8g) when Graviton5 is available in your region; stay on M8g only where M9g isn't yet offered. No RIs (use Compute Savings Plans).
- Sources: [AWS News Blog (Jun 10, 2026)](https://aws.amazon.com/blogs/aws/now-available-amazon-ec2-m9g-and-m9gd-instances-powered-by-new-aws-graviton5-processors/); [Vantage m9g.large](https://instances.vantage.sh/aws/ec2/m9g.large) ($0.0978 on-demand / $0.042 spot); [AWS Graviton (Wikipedia)](https://en.wikipedia.org/wiki/AWS_Graviton)
- Updated: `providers/aws.md` (new Graviton5 / M9g-M9gd section + top callout), `comparisons/compute.md` (M9g rows + Graviton5 in ARM roadmap)

### 📍 AWS: EC2 High Memory U7in-24TB Expanded to South America (São Paulo) (Effective ~Aug 11, 2026)

- **~Aug 11, 2026**: **EC2 High Memory `u7in-24tb.224xlarge`** (24 TB memory, 224 vCPU) is now available in the **South America (São Paulo)** region (`sa-east-1`). ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-high-memory-u7i-south-america))
- **Pricing**: No rate-card change — a **regional availability expansion** of an already-GA, already-priced High Memory family (SAP HANA / large in-memory DB scale-up). Regional on-demand rates vary; verify on the [EC2 on-demand pricing page](https://aws.amazon.com/ec2/pricing/on-demand/) by selecting `sa-east-1`.
- **FinOps context**: Gives in-country (Brazil) data residency for very-large-memory scale-up workloads without egressing to a US/EU region.
- Updated: `providers/aws.md` (new High Memory regional-availability note)

### ✅ No new AWS base pricing changes (as of 2026-08-22)
- Lambda (Functions / Managed Instances), EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-08-15. The only substantive AWS item this run is the **Graviton5 / M9g-M9gd catch-up above** (a new-tier addition, GA June 10, 2026) and the **U7in-24TB São Paulo regional expansion**.
- EC2 Capacity Blocks for ML: July 1 +20% rates remain in effect; next scheduled Capacity Block review is **October 2026** (~5–7 weeks away).
- Lambda INIT cold-start billing (since Aug 2025): unchanged.
- Other Aug 11–15, 2026 AWS announcements were **non-pricing**: Amazon Redshift `rg.large`/`rg.12xlarge` in GovCloud (US); Claude Opus 5 in GovCloud (US); Bedrock IAM cost allocation to the bedrock-mantle endpoint; EC2 application status checks; OpenSearch Serverless 10K collections/group; IAM account access manager; AWS Marketplace managed buyer notifications.

### ✅ No new GCP base pricing changes (as of 2026-08-22)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — on-demand rates confirmed unchanged since 2026-08-15. The Hyperdisk ML throughput-floor reduction (Aug 3, 2026) remains the most recent cost-relevant GCP change.
- Google Cloud release notes (Aug 15–22, 2026): no compute/storage/serverless/database/CDN rate-card changes. Items were **non-pricing feature/runtime updates**:
  - **Cloud Run** (Aug 19): **Go 1.27 runtime** in Preview (Preview); Go runtime lifecycle now aligns to the community release cycle from 1.26+.
  - **Cloud Run** (Aug 11): NVIDIA L4 GPU **driver 580.x.x** available for services/jobs/worker pools.
  - **Cloud Run** (Aug 5): **sandboxes for all resources** (incl. jobs + worker pools) in Preview — for untrusted/AI-generated code.
  - **Compute Engine** (Jul 27–28): Hyperdisk Balanced **max IOPS/GiB** raised (from 4 IOPS/GiB) and **max throughput** raised for `c4d-*-96/192/384` (e.g. c4d-*-192: 4,800 → **6,250 MiB/s**) — capacity/performance improvements at the same price tier, not rate changes.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** (~24 days away). Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.

### ✅ No new Azure base pricing changes (as of 2026-08-22)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged since 2026-08-15.
- Azure updates (Aug 15–22, 2026) were **non-pricing feature/status GAs**:
  - **VM vCore Customization — GA (added to roadmap Aug 19, 2026)**: Disable SMT/Hyper-Threading and Configurable Constrained Cores on supported Azure VMs (incl. VMSS Uniform). Available in all Azure public regions. **FinOps relevance**: disabling SMT / constraining visible vCPUs can **reduce per-VM SQL Server & licensing cost** (licensing is per visible vCPU) and improve latency consistency — no Azure infrastructure rate change, but it can lower your OS/licensing bill for licensed workloads. ([Azure updates](https://azure.microsoft.com/en-us/updates))
  - **Azure Databricks Lakebase** GA in 4 additional regions (North Central US, France Central, Germany West Central, East Asia) — Azure ID 569684 (Aug 19). Analytics regional expansion; not core compute/storage/serverless/database/CDN rate change.
  - **Azure Disk Storage — Live Resize for shared Premium SSD v2 and Ultra Data Disks** GA (Aug) — capacity/feature, no rate change.
  - **Azure SQL** mid-Aug 2026 updates (VS Code keyboard-shortcut config; MSSQL-extension provisioning) — tooling, non-pricing.
  - **AKS** control-plane metrics collection with Managed Prometheus — GA (Aug); **Azure Site Recovery** BYON — GA (Aug); **Azure Copilot** direct agent access — Aug 2026. All non-pricing.
- Microsoft Foundry model-deployment pricing increases remain **effective September 1, 2026** (~10 days away) — the next scheduled Azure cost change.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption stops running **September 30, 2026** (~39 days); Azure Cache for Redis new-instance creation blocked **October 1, 2026** (~40 days); Azure NVv3/NVv4 GPU VM retirement **September 30, 2026**; Azure GPv1 storage account retirement **October 13, 2026** (~52 days).

---

## 2026-08-15

### 📍 AWS: EC2 R8a (AMD EPYC Turin) Expanded to Canada (Central) (Effective August 11, 2026)

- **Aug 11, 2026**: **EC2 R8a** (memory-optimized, 5th-Gen AMD EPYC "Turin", up to 4.5 GHz) now available in **Canada (Central)** — `ca-central-1`. ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-r8a-instances-canada-central/))
- **Pricing**: No rate-card change — this is a **regional availability expansion** of an already-GA, already-priced family (R8a/C8a/M8a went GA in late 2025). Regional on-demand rates vary by region; verify on the [EC2 on-demand pricing page](https://aws.amazon.com/ec2/pricing/on-demand/) by selecting `ca-central-1`.
- **FinOps context**: R8a is AWS's AMD-based memory-optimized family — up to **30% higher performance** and **~19% better price-performance** vs R7a, with **45% more memory bandwidth**, SAP-certified (+38% SAPS vs R7a), and 1 vCPU = 1 physical core (no SMT) for predictable latency. Useful for in-memory DBs / large caches / real-time analytics / EDA in the Canada (Central) region (in-country data residency). 12 sizes incl. 2 bare metal.
- Updated: `providers/aws.md` (new R8a regional-availability note)

### ✅ No new AWS base pricing changes (as of 2026-08-15)
- Lambda (Functions / Managed Instances), EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-08-08.
- EC2 Capacity Blocks for ML: July 1 +20% rates remain in effect; next scheduled Capacity Block review is **October 2026**.
- Lambda INIT cold-start billing (since Aug 2025): unchanged.
- This week's AWS items (R8a Canada Central expansion above) are availability, not rate, changes. Other Aug 8–15 AWS announcements were **non-pricing**: S3 richer Access-Denied error messages (Aug 13); AWS Billing **Managed Dashboards** at no additional cost (Aug 14); AWS Client VPN CLI/controls at standard pricing (Aug 13); ACM email→DNS validation migration (Aug 13); RDS for Oracle APEX 26.1 (Aug 14); EKS control-plane config params (Aug 12). None alter rate cards.

### ✅ No new GCP base pricing changes (as of 2026-08-15)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — on-demand rates confirmed unchanged since 2026-08-08. The Hyperdisk ML throughput-floor reduction (Aug 3, 2026) remains the most recent cost-relevant GCP change.
- Google Cloud release notes (Aug 8–15, 2026): no compute/storage/serverless/database/CDN rate-card changes. Items were non-pricing: App Engine TLS 1.2+ enforcement (Aug 14); Dataproc image / Conda-channel default changes (Aug 14, eff. Aug 25); Cloud SQL for MySQL 9.7 flag updates (Aug 13); Managed Airflow release (Aug 10).
- ℹ️ Out of core scope (network observability, not compute/storage/serverless/database/CDN): **Cloud Hub App Topology API** transitions to a **usage-based billing model** (with a daily free data-usage allotment) effective **September 15, 2026** — noted for completeness only.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** (~31 days away). Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.

### ✅ No new Azure base pricing changes (as of 2026-08-15)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged since 2026-08-08.
- August 8–15, 2026 Azure updates were **non-pricing feature/status items**: Azure Database for PostgreSQL Flexible Server pre-upgrade validation checks GA (Aug 12); Azure Front Door batch rule updates GA (Aug 12); Azure Functions "Serverless Agents" (Aug 12, blog); Azure Firewall explicit proxy GA; Azure Databricks Unity AI Gateway / SharePoint Connector GA (Aug 5). None alter rate cards.
- Microsoft Foundry model deployment pricing increases remain **effective September 1, 2026** (~17 days away) — the next scheduled Azure cost change.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption stops running **September 30, 2026** (~46 days); Azure Cache for Redis new-instance creation blocked **October 1, 2026** (~47 days); Azure NVv3/NVv4 GPU VM retirement **September 30, 2026**; Azure GPv1 storage account retirement **October 13, 2026** (~59 days).

---

## 2026-08-08

### 💸 GCP: Hyperdisk ML Minimum Provisioned Throughput Floor Cut 80% for Large Fan-Out (Effective August 3, 2026)

- **Announced/Effective**: August 3, 2026 ([Google Cloud release notes](https://docs.cloud.google.com/release-notes))
- **Change**: The **minimum provisioned throughput for a Hyperdisk ML volume attached to more than 20 instances** dropped from **100 MiB/s per instance → 20 MiB/s per instance**.
- **Why it's a cost change**: Hyperdisk ML is billed for **provisioned throughput** at **$0.000164384 per MiB/s-hour** (≈ **$0.12 per MiB/s-month** in us-central1), in addition to provisioned capacity ($0.000109589/GiB-hr). The per-instance minimum forces the volume's provisioned throughput to be at least `(#instances × per-instance floor)`.
  - Example: a read-only Hyperdisk ML volume shared across **30 inference instances** previously required ≥ 30 × 100 = **3,000 MiB/s** minimum (≈ **$360/mo** on throughput alone); now ≥ 30 × 20 = **600 MiB/s** (≈ **$72/mo**) — an **~80% reduction in the throughput floor** for large read-only-many fan-out (LLM inference / HPC dataset loading).
- **Workloads affected**: ML inference and training data loading where a single immutable dataset volume is fanned out read-only to many GPU/CPU instances. Not relevant to single-instance or small-fan-out volumes (the per-instance floor only applies at >20 attached instances).
- **FinOps note**: Throughput is also still bounded by the volume's own min/max throughput (400 MiB/s – 2 TiB/s, size-dependent) and each instance's machine-type bandwidth cap; right-size the volume's provisioned throughput to actual need rather than the floor.
- Updated: `providers/gcp.md` (new Hyperdisk ML note in Storage section)

### 📍 AWS: Graviton4 (C8g / M8g) Expanded to More Regions (Effective August 4 & 6, 2026)

- **Aug 4, 2026**: **EC2 C8g** (Graviton4, compute-optimized) now available in **Europe (Paris)**, **Africa (Cape Town)**, **Israel (Tel Aviv)**, and **Canada West (Calgary)**. ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-c8g-instances-additional-regions/))
- **Aug 6, 2026**: **EC2 M8g** (Graviton4, general-purpose) now available in **Asia Pacific (Taipei)** and **Mexico (Central)**. ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ec2-m8g-instances-additional-regions/))
- **Pricing**: No rate-card change — these are **regional availability expansions** of already-GA, already-priced Graviton4 families (up to 30% better price-performance vs Graviton3). Regional on-demand rates vary by region; verify on the [EC2 on-demand pricing page](https://aws.amazon.com/ec2/pricing/on-demand/).
- **FinOps context**: Graviton4 is now reachable in more in-country/low-latency regions (Cape Town, Tel Aviv, Calgary, Taipei, Mexico), enabling ARM-based cost optimization (20–30% vs comparable x86) without crossing geographies.
- Updated: `providers/aws.md` (new Graviton4 regional-availability note)

### ℹ️ GCP: Cloud Billing Reports — "Originating Products" Filter (August 7, 2026, non-pricing)

- **Announced**: August 7, 2026 ([Cloud Billing release notes](https://docs.cloud.google.com/billing/docs/release-notes))
- New **"Originating products"** filter and **Group by** option in Cloud Billing Reports — attributes usage caused by one product in another (e.g., Gemini Enterprise driving Gemini-app usage) to improve **AI spend visibility**.
- Also GA: **GKE workload recommenders** in the FinOps hub (right-size over/under-provisioned workloads).
- **Not a pricing change** — reporting/attribution only. Useful for FinOps teams attributing AI spend, but no rates moved.

### ✅ No new AWS base pricing changes (as of 2026-08-08)
- Lambda (Functions / Managed Instances), EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-08-01.
- EC2 Capacity Blocks for ML: July 1 +20% rates remain in effect; next scheduled Capacity Block review is **October 2026**.
- This week's AWS items (C8g/M8g regional expansions above) are availability, not rate, changes.

### ✅ No new GCP base pricing changes (as of 2026-08-08)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — on-demand rates confirmed unchanged since 2026-08-01. The only cost-relevant change this period is the Hyperdisk ML throughput-floor reduction above (a minimum-bill floor change, not a per-unit rate change).
- Google Cloud release notes (Aug 1–8, 2026): no compute/storage/serverless/database/CDN rate-card changes.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** (~38 days away). Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.

### ✅ No new Azure base pricing changes (as of 2026-08-08)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged since 2026-08-01.
- August 2026 Azure updates were **non-pricing feature/status items**: Azure ExpressRoute resiliency guard (Public Preview, Aug 7); Azure Virtual Network routing appliance (GA, Aug 4); Azure DNS ↔ Traffic Manager load-balancing integration (Preview, Aug 4); automatic backup immutability for Azure SQL Database / Managed Instance (GA, Aug 3); Trusted Launch as default (GA, Aug 3). None alter rate cards.
- Microsoft Foundry model deployment pricing increases remain **effective September 1, 2026** (~24 days away).
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption stops running **September 30, 2026** (~53 days); Azure Cache for Redis new-instance creation blocked **October 1, 2026** (~54 days); Azure NVv3/NVv4 GPU VM retirement **September 30, 2026**; Azure GPv1 storage account retirement **October 13, 2026** (~66 days).

---

## 2026-08-01

### 🆕 Azure: New Region — India South Central (Hyderabad) Now Generally Available (Effective July 2026)

- **Announced/Added to roadmap**: July 28, 2026 ([Azure Update ID 568013](https://azure.microsoft.com/en-us/updates?id=568013)); **Effective**: July 2026 (General Availability)
- Microsoft's **fourth India region** — `indiasouthcentral`, located in **Hyderabad, Telangana** — is now **Generally Available**.
  - Existing India regions: **Central India** (Pune), **South India** (Chennai), **West India** (Mumbai).
- **Availability Zones**: supported (**3 zones**) — confirmed on the [Azure regions list](https://learn.microsoft.com/en-us/azure/reliability/regions-list). Paired region: **Central India** (Pune).
- Built with **AI readiness** as a key focus; supports local data residency, improved latency, and additional resilient cloud capacity for India. Useful for in-country DR pairs with Central India.
- **Pricing**: No separate "new region" rate card published; India regions on Azure are typically among the **cheapest Azure regions** (per third-party trackers, Central India avg ~$1.18/hr across VM SKUs vs West Europe ~$1.81/hr and Brazil Southeast ~$2.64/hr — see [cloudprice.net](https://cloudprice.net/regions)). Expect India South Central to price similarly to the other India regions; verify exact VM/region rates on the [Azure VM pricing page](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/).
- **Database availability**: **Azure Database for PostgreSQL — Flexible Server** is now GA in India South Central ([Azure Update ID 568334](https://azure.microsoft.com/en-us/updates?id=568334), July 30, 2026), giving managed-Postgres users a fourth India deployment target.
- **FinOps context**: For India data-residency workloads, India South Central + Central India now form a same-geography multi-AZ DR pair at India-region price points (typically lower than EU/APAC peers). Prefer India regions over Southeast Asia/East Asia for India customers to cut both latency and per-hour compute cost.
- Updated: `providers/azure.md` (new Regions callout + PostgreSQL Flexible Server availability note)

| Region | Programmatic name | Location | AZs | Paired region |
|---|---|---|---|---|
| India South Central 🆕 | `indiasouthcentral` | Hyderabad, Telangana | 3 | Central India (Pune) |
| Central India | `centralindia` | Pune | 3 | South India |
| South India | `southindia` | Chennai | — | Central India |
| West India | `westindia` | Mumbai | — | — |

### 🆕 AWS: New Local Zone — Athens, Greece (Effective July 27, 2026)

- **Announced**: July 27, 2026 ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/07/aws-local-zone-athens-greece/))
- New **AWS Local Zone in Athens, Greece** — the **second EMEA Local Zone with support for Amazon S3 and Amazon EBS Local Snapshots**, enabling storage/processing within Greece for local data-residency needs.
- Supported services/instances at the Athens Local Zone:
  - **Amazon EC2**: C7i, M7i, R7i instances (7th-gen Intel Xeon Scalable)
  - **Amazon S3**: **One Zone-Infrequent Access** storage class
  - **Amazon EBS**, **Amazon ECS**, and more
- **Pricing**: No rate-card change announced; Local Zones carry the standard Local Zone pricing premium over the parent region (Athens is an extension of a European AWS Region). Verify on the [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/) by selecting the Athens Local Zone.
- Updated: `providers/aws.md` (new Local Zones callout)

### ✅ No new AWS base pricing changes (as of 2026-08-01)
- Lambda (Functions / Managed Instances), EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-07-25.
- EC2 Capacity Blocks for ML: July 1 +20% rates remain in effect; next scheduled Capacity Block review is **October 2026**.
- Lambda INIT cold start billing (since Aug 2025): unchanged.
- Note (out of core scope): **Amazon SES** introduced new **pricing plans** (predictable, volume-based billing) on July 27, 2026 — affects email/messaging, not compute/storage/serverless/database/CDN.

### ✅ No new GCP base pricing changes (as of 2026-08-01)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged since 2026-07-25.
- Google Cloud release notes (Jul 25–Aug 1, 2026): no compute/storage/serverless/database/CDN pricing changes. Items were all **non-pricing feature/status updates**:
  - **Cloud Run**: Node.js 26 runtime (Preview, Jul 27); Budget spend caps to pause workloads (Preview, Jul 27); sandboxes for untrusted/AI-generated code (Preview, Jul 8); public container image import from GitHub Container Registry (GA, Jul 14).
  - **Cloud Load Balancing**: global external passthrough Network Load Balancer (Preview, Jul 31) — Layer 4, global anycast, multi-region backends.
  - **Vertex AI Search**: Agent Search now allows *decreasing* configurable-pricing subscription thresholds (GA, Jul 23) — minor.
- C4N GA (Jul 8), CUD scope default change (Jun 16), CDN Interconnect increases (May 1) remain in effect as previously documented.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** — ~45 days away. Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.

### ✅ No new Azure base pricing changes (as of 2026-08-01)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged since 2026-07-25. (The India South Central launch above is a region expansion, not a rate change.)
- Microsoft Foundry model deployment increases (announced Jul 9) remain **effective September 1, 2026** — ~31 days away.
- Azure Reserved VM Instances retirement for legacy series (Av2, Dv3/Dsv3, Ev3/Esv3, etc.) in effect since July 1, 2026.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption stops running **September 30, 2026** (~60 days); Azure Cache for Redis new-instance creation blocked **October 1, 2026** (~61 days); Azure NVv3/NVv4 GPU VM retirement **September 30, 2026**; Azure GPv1 storage account retirement **October 13, 2026** (~73 days).

---

## 2026-07-25

### 🆕 AWS: EC2 G7 (RTX PRO 4500) — On-Demand Pricing Now Published + US East (N. Virginia) Expansion (Effective July 10, 2026)

- **Announced**: July 10, 2026 ([AWS What's New — G7 now in US East (N. Virginia)](https://aws.amazon.com/about-aws/whats-new/2026/07/amazon-ec2-g7-available-North-Virginia/)); **Effective**: July 10, 2026
- EC2 **G7** instances (NVIDIA RTX PRO 4500 Blackwell Server Edition, 32 GB GDDR7/GPU), GA since June 18, 2026, **expanded to US East (N. Virginia)** on July 10, 2026 — now available in **US East (N. Virginia), US East (Ohio), and US West (Oregon)**.
- **On-demand pricing is now published**, resolving the previously "TBD" rates tracked on 2026-07-17 and 2026-07-18. Rates below are US regions (us-east-1/us-east-2/us-west-2), Linux, on-demand, per instance-hour. **No Reserved Instances**; commitments via Compute Savings Plans (~20–30% off 1-yr no-upfront). Spot discounts ~81–83% off on-demand.

| Instance | GPUs | vCPU | RAM | $/hr (On-Demand) | $/GPU/hr | $/hr (Spot) |
|---|---|---|---|---|---|---|
| g7.2xlarge | 1 | 8 | 32 GiB | **$2.52** | $2.52 | ~$0.47 |
| g7.4xlarge | 1 | 16 | 64 GiB | $3.04 | $3.04 | — |
| g7.8xlarge | 1 | 32 | 128 GiB | **$4.09** | $4.09 | — |
| g7.12xlarge | 2 | 48 | 192 GiB | $7.13 | $3.57 | — |
| g7.24xlarge | 4 | 96 | 384 GiB | $14.26 | $3.57 | — |
| g7.48xlarge | 8 | 192 | 768 GiB | **$28.51** | $3.56 | ~$4.80 |

- **Correction**: `providers/aws.md` previously listed g7.8xlarge with 256 GiB RAM; the correct system RAM is **128 GiB** (32 vCPU × 4 GiB/vCPU) — fixed.
- **FinOps context**: For single-GPU inference, G7 (RTX PRO 4500, $2.52/hr) is now the cheapest Blackwell inference option on AWS — below G7e (RTX PRO 6000, $3.36/hr). Choose G7 for ≤32 GB-per-card graphics/inference/RAG; G7e for 96 GB-card LLMs. Multi-GPU G7 nodes price ~$3.56/GPU/hr — useful for sharded inference. Spot (~81–83% off) is viable for interruptible inference/batch.
- Sources: [AWS What's New (Jul 10, 2026)](https://aws.amazon.com/about-aws/whats-new/2026/07/amazon-ec2-g7-available-North-Virginia/); [Vantage g7.2xlarge](https://instances.vantage.sh/aws/ec2/g7.2xlarge) ($2.52 on-demand / $0.469 spot); [Spheron G7 pricing](https://www.spheron.network/blog/aws-ec2-g7-pricing-2026/)
- Updated: `providers/aws.md` (G7 rows — pricing filled in, g7.8xlarge RAM corrected, GA note updated), `comparisons/compute.md` (G7 GPU rows — pricing filled in)

### ✅ No new AWS base pricing changes (as of 2026-07-25)
- Lambda (Functions / Managed Instances), EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-07-18.
- EC2 Capacity Blocks for ML: +20% July 1 rates remain in effect as previously documented.
- Lambda INIT cold start billing (since Aug 2025): unchanged.

### ✅ No new GCP pricing changes (as of 2026-07-25)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged since 2026-07-18.
- Google Cloud release notes (Jul 17 & Jul 24, 2026): no compute/storage/serverless/database/CDN pricing changes — items were Marketplace private-offers API (GA), Managed Airflow version-support policy change, and Google SecOps Security Tokens metering (out of scope for this KB).
- C4N GA (Jul 8), CUD scope default change (Jun 16), CDN Interconnect increases (May 1) remain in effect as previously documented.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** — ~52 days away. Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.

### ✅ No new Azure base pricing changes (as of 2026-07-25)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged since 2026-07-18.
- Microsoft Foundry model deployment increases (announced Jul 9) remain **effective September 1, 2026** — ~38 days away.
- Azure Reserved VM Instances retirement for legacy series (Av2, Dv3/Dsv3, Ev3/Esv3, etc.) in effect since July 1, 2026.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption stops running **September 30, 2026**; Azure Cache for Redis new-instance creation blocked **October 1, 2026**; Azure GPv1 storage account retirement **October 13, 2026**.

---

## 2026-07-18

### 🆕 Azure: Microsoft Foundry Model Deployment Pricing Update — New APAC Data Zone + Regional Increases (Announced July 9, 2026; Effective September 1, 2026)

- **Announced**: July 9, 2026 ([Microsoft Foundry blog](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/microsoft-foundry-model-deployment-pricing-update/4535385)); **Effective**: September 1, 2026
- Microsoft Foundry (Azure AI Foundry) is raising prices for AI model deployments that run in a specific geography/country (Data Zone and Regional deployments outside the US), and introducing a new **APAC Data Zone**.
- Rationale: serving AI within a specific geography/country at high availability costs more than a shared global pool; pricing now reflects that cost and added value.
- **Global pricing stays the same** and remains the most cost-efficient deployment option. US Data Zone (+10%) and US Regional (+10%) are unchanged.

| Deployment | Price vs. Global | What's changing (eff. Sep 1, 2026) |
|---|---|---|
| Global | Same (baseline) | No change |
| US Data Zone | +10% | No change |
| EU Data Zone | +20% | ⬆️ Increasing (rising to +20%) |
| APAC Data Zone 🆕 | +20% | Newly available |
| Regional — US | +10% | No change |
| Regional — outside US | +25% to +50% | ⬆️ Increasing (varies by region) |

- **Regional premiums effective Sep 1, 2026 (relative to Global):**

| Premium vs. Global | Regions |
|---|---|
| +25% | Australia, India, Indonesia*, Malaysia*, New Zealand* |
| +30% | Austria*, Belgium*, Canada, Denmark*, Germany, Italy, Mexico, Poland, South Africa, Spain, Sweden, Switzerland, UAE |
| +35% | Japan, Korea, Taiwan* |
| +40% | France, Hong Kong, Israel*, Norway, Qatar, UK |
| +50% | Brazil, EU North, EU West, Singapore |

> *\* Newly available regions at this price (no prior rate).* Exact per-model/token rates vary — see the [Azure AI Foundry pricing page](https://azure.microsoft.com/en-us/products/ai-foundry/models/openai/).

- **How the increase applies:**
  - **Standard (pay-as-you-go)**: new premiums apply **only to models launched on or after September 1, 2026**. Customers who stay on their current models see **no price increase**; the higher EU Data Zone / Regional premiums apply only when moving to a model launched on/after Sep 1, 2026.
  - **Provisioned Throughput (PTU)**: the increase applies to **all customers** with EU Data Zone or Regional PTUs outside the US.
- **FinOps action**: AI teams running Foundry model deployments in EU/Regional (non-US) should (1) prefer **Global** deployments where data-residency rules allow, (2) avoid unnecessary model-version churn after Sep 1 to lock in current PAYG rates, and (3) review PTU contracts in affected regions for the Sep 1 uplift.
- Source: [Microsoft Foundry Model Deployment Pricing Update (July 9, 2026)](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/microsoft-foundry-model-deployment-pricing-update/4535385)
- Updated: `providers/azure.md` (new AI / Model Deployment section)

### 🆕 GCP: C4N Network-Optimized VM Series — Generally Available (July 8, 2026; No Published Rate Change)

- **GA**: July 8, 2026 ([Compute Engine release notes](https://docs.cloud.google.com/compute/docs/release-notes)) — C4N moved from Preview to **Generally Available** for Compute Engine and GKE.
- Powered by 5th-gen **Intel Xeon Scalable (Emerald Rapids)**; purpose-built for network- and block-storage-intensive workloads (network/security appliances, high-performance DBs, large-scale analytics, distributed filesystems).
- Specs: up to **400 Gbps** network bandwidth; up to **95 Mpps** sustained packet processing; **Hyperdisk Extreme** up to 25 GiB/s bandwidth and 1M IOPS; predefined shapes with three vCPU:memory ratios; **2–192 vCPUs**, up to **1,488 GB DDR5**.
- **Local SSD on C4N remains in Preview** (request access via form). **M4N** (memory-optimized, enhanced networking) remains in Preview.
- **Pricing**: not separately quoted in the GA announcement — verify on the [Compute Engine pricing page](https://cloud.google.com/compute/all-pricing). Existing C4 resource-based CUDs do **not** transfer to C4N (new CUD purchase required).
- Updated: `providers/gcp.md` (C4N/M4N section — C4N marked GA), `comparisons/compute.md` (C4N/M4N note)

### ✅ No new AWS pricing changes (as of 2026-07-18)
- Lambda, EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-07-17.
- EC2 Capacity Blocks for ML: +20% July 1 rates remain in effect as previously documented.
- G7 instances (RTX PRO 4500): still not listed with published per-hour on-demand rates; check [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/).
- Lambda INIT cold start billing (since Aug 2025): unchanged; optimize heavy JVM/CLR runtimes or use SnapStart.

### ✅ No new GCP pricing changes (as of 2026-07-18)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged. (C4N GA on July 8 is a status change, not a rate change — see above.)
- GCP custom machine type pricing announcement page (cloud.google.com/compute/cmt-pricing-announcement) was refreshed again on 2026-07-17 but still reflects the existing 5% CUD premium policy from 2024 — no new changes (consistent with the 2026-07-13 assessment).
- CUD scope default change (June 16, 2026) and CDN Interconnect increases (May 1, 2026) remain in effect as previously documented.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** — ~59 days away. Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.
- ⚠️ Upcoming: **BigQuery Data Transfer Service SKU label** changes from `DATA_TRANSFER_SERVICE` → `data_transfer_service` on **August 11, 2026** — ~24 days away. Update billing exports/dashboards to match both labels before then.
- Flex-start VMs (DWS): confirmed GA, pricing stable. Key rates: g4-standard-48 Flex-start = **$2.25/hr** (50% off on-demand $4.50/hr); a3-megagpu-8g Flex-start = **$40.32/hr**.

### ✅ No new Azure base pricing changes (as of 2026-07-18)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged. (Microsoft Foundry model deployment pricing change tracked separately above.)
- Azure Reserved VM Instances retirement for legacy series (Av2, Dv3/Dsv3, Ev3/Esv3, etc.) took effect **July 1, 2026** — no new purchases/renewals available for those series.
- Azure Blob Storage 128 KiB minimum object size: still **PAUSED** (June 8, 2026) — no new timeline published.
- Azure Cobalt 200 VMs: still in Early Access Preview; no pricing published. Cobalt 100 remains the baseline for Arm VM pricing.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption **stops running September 30, 2026** — ~74 days away.
- ⚠️ Upcoming: Azure NVv3/NVv4 VM retirement **September 30, 2026** — ~74 days away; migrate to NVadsA10 v5 or NCv6.
- ⚠️ Upcoming: Azure Cache for Redis new-instance creation blocked for **all** customers **October 1, 2026** — ~75 days away; migrate to Azure Managed Redis.
- ⚠️ Upcoming: Azure GPv1 storage account retirement **October 13, 2026** — ~87 days away; auto-migration to GPv2.

---

## 2026-07-17

### 🆕 AWS: Lambda Managed Instances — Region Expansion (Effective June 8, 2026)

- **Announced**: June 8, 2026 ([AWS What's New](https://aws.amazon.com/about-aws/whats-new/2026/06/aws-lambda-managed-instances-region-expansion/))
- **Lambda Managed Instances (LMI)** expanded from its initial limited set of regions to availability in most AWS Regions where Lambda is offered.
- No pricing change — the three-part billing model remains unchanged:
  1. **Requests**: $0.20 per million
  2. **EC2 compute**: Standard EC2 on-demand price for the selected instance type (eligible for Compute Savings Plans, Reserved Instances — discounts apply to EC2 cost only, not the management fee)
  3. **Management fee**: **+15%** on top of EC2 on-demand price per instance-hour
- **Customer reference**: SmugMug/Flickr reported up to **80% cost reduction** on their Flickr photo API workload vs. standard Lambda, using C8g (Graviton4) instances + Compute Savings Plans with LMI's multi-request concurrency model.
- Previously only documentd as "initial GA" in `providers/aws.md`; region expansion note added.
- Updated: `providers/aws.md` (Lambda Managed Instances section — region expansion note + customer example added)

| LMI Component | Rate |
|---|---|
| Requests | $0.20 / million |
| EC2 on-demand (example: m7g.xlarge) | $0.1632/hr (us-east-1) |
| Management fee | +15% of EC2 on-demand = $0.02448/hr |
| Total instance cost | $0.1877/hr before SP/RI discounts |

### ✅ No new AWS pricing changes (as of 2026-07-17)
- Lambda, EC2 on-demand/Savings Plans, S3, RDS, Aurora, DynamoDB, CloudFront — rates confirmed unchanged since 2026-07-13.
- EC2 Capacity Blocks for ML: +20% July 1 rates remain in effect as previously documented.
- G7 instances (RTX PRO 4500): still not listed with published per-hour on-demand rates; check [EC2 pricing page](https://aws.amazon.com/ec2/pricing/on-demand/).
- Lambda INIT cold start billing (since Aug 2025): unchanged; optimize heavy JVM/CLR runtimes or use SnapStart.

### ✅ No new GCP pricing changes (as of 2026-07-17)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged.
- CUD scope default change (June 16, 2026) and CDN Interconnect increases (May 1, 2026) remain in effect as previously documented.
- ⚠️ Upcoming: **NVIDIA P100 GPU end of support** on **September 15, 2026** — 60 days away. Migrate N1+P100 workloads to G4 (RTX PRO 6000), A3, or L4-based VMs.
- Flex-start VMs (DWS): confirmed GA, pricing stable. Key rates: g4-standard-48 Flex-start = **$2.25/hr** (50% off on-demand $4.50/hr); a3-megagpu-8g Flex-start = **$40.32/hr**.

### ✅ No new Azure pricing changes (as of 2026-07-17)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — rates confirmed unchanged.
- Azure Reserved VM Instances retirement for legacy series (Av2, Dv3/Dsv3, Ev3/Esv3, etc.) took effect **July 1, 2026** as previously documented — no new purchases/renewals available for those series.
- Azure Blob Storage 128 KiB minimum object size: still **PAUSED** (June 8, 2026) — no new timeline published.
- Azure Cobalt 200 VMs: still in Early Access Preview; no pricing published. Cobalt 100 remains the baseline for Arm VM pricing.
- ⚠️ Upcoming: Azure Functions runtime v3 on Linux Consumption **stops running September 30, 2026** — 75 days away.
- ⚠️ Upcoming: Azure NVv3/NVv4 VM retirement **September 30, 2026** — 75 days away; migrate to NVadsA10 v5 or NCv6.
- ⚠️ Upcoming: Azure GPv1 storage account retirement **October 13, 2026** — 88 days away; auto-migration to GPv2.

---

## 2026-07-15

### 🆕 Azure: Front Door Edge Actions — Public Preview (Announced July 10–14, 2026)

- **Announced**: July 10–14, 2026 (Azure Update ID: 567402; Blog post July 14, 2026); **Effective**: now in **Public Preview**
- Azure Front Door now supports **edge actions** — lightweight JavaScript functions that execute inside Azure Front Door's request pipeline at the edge POP, powered by **Hyperlight** (Microsoft's secure micro-VM technology).
- Analogous to AWS CloudFront Functions / Lambda@Edge and Cloudflare Workers in concept.
- **Pricing model**: Two-part — per **invocation** + per **execution time beyond 1 ms** per invocation. Specific dollar rates are published on the [Azure Front Door pricing page](https://azure.microsoft.com/pricing/details/frontdoor/); not yet extracted into a standalone table (Preview pricing).
- Key constraints during Preview:
  - Max code size: **16 KB** per edge action
  - Max execution time: **10 ms** (request terminated without processing if exceeded)
  - Up to **3 versions** per edge action resource
  - Max **100 edge action resources** per subscription
  - Language: **JavaScript only** (current preview)
- Use cases: A/B testing, canary deployments, header manipulation, request filtering, dynamic origin selection, URL rewrites, authentication at the edge, real-time personalization.
- Invoked during the **client request phase** via Azure Front Door Rules Engine; future roadmap includes response invocations and edge inferencing.
- Available: all Azure Front Door Standard and Premium profiles (not Classic).
- Source: [Azure Update ID 567402](https://azure.microsoft.com/updates?id=567402); [Blog announcement July 14, 2026](https://techcommunity.microsoft.com/blog/azurenetworkingblog/introducing-azure-front-door-edge-actions---bringing-secure-programmable-logic-t/4531928); [Edge actions documentation](https://learn.microsoft.com/azure/frontdoor/edge-actions)
- Updated: `providers/azure.md` (CDN section — new edge actions row)

| Capability | Detail |
|---|---|
| Execution environment | Hyperlight micro-VM (hardware-backed isolation) |
| Language | JavaScript |
| Max execution time | 10 ms |
| Invocation point (Preview) | Client request phase only |
| Billing | Per-invocation + per-ms beyond 1 ms |
| Availability | Public Preview (July 14, 2026) |

### ✅ No new AWS pricing changes (as of 2026-07-15)
- Lambda, EC2, S3, RDS, DynamoDB, CloudFront, EKS — rates confirmed unchanged since 2026-07-13.
- ElastiCache: Valkey node pricing remains 20% below Redis OSS on-demand; Valkey Serverless remains 33% cheaper than Redis OSS Serverless. No new changes.
- All previously documented changes remain in effect.

### ✅ No new GCP pricing changes (as of 2026-07-15)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged.
- CUD scope default change (June 16, 2026) and CDN Interconnect increases (May 1, 2026) remain in effect as previously documented.
- P100 GPU end-of-support (September 15, 2026) remains the next upcoming GCP change.

---

## 2026-07-13

### 🆕 AWS: EKS Auto Mode & ECS Managed Instances — GPU Management Fees Reduced 35–60% (Effective July 1, 2026)

- **Announced**: July 7, 2026 (AWS What's New posts); **Effective**: July 1, 2026 (retroactive to start of month)
- **EKS Auto Mode**: GPU/accelerated instance management fees reduced
  - **G-series (G4, G5, G6, G7, G7e)**: management fee **−35%**
  - **P-series (P4, P5, P6) and AWS Trainium**: management fee **−60%**
- **ECS Managed Instances**: identical reductions applied simultaneously
  - **G-series**: management fee **−35%**
  - **P-series and AWS Trainium**: management fee **−60%**
- Reductions apply **automatically** to all existing clusters/managed instances — no action required.
- Applies in all AWS Regions where EKS Auto Mode / ECS Managed Instances is available.
- Context: EKS Auto Mode normally charges a ~+15% management fee on top of underlying EC2 on-demand rates (as documented in `providers/aws.md`). This reduction applies specifically to GPU/accelerated instance types only; general-purpose instance management fees are unchanged.
- Source: [EKS Auto Mode GPU price reduction](https://aws.amazon.com/about-aws/whats-new/2026/07/amazon-eks-auto-mode-gpu-price/); [ECS Managed Instances GPU price reduction](https://aws.amazon.com/about-aws/whats-new/2026/07/amazon-ecs-managed-instances-gpu-price/)
- Updated: `providers/aws.md` (EKS Auto Mode section)

| Instance series | Old EKS/ECS management fee premium | New management fee premium (eff. Jul 1, 2026) |
|---|---|---|
| G-series (G4, G5, G6, G7, G7e) | +15% over EC2 on-demand | **+9.75%** over EC2 on-demand (−35%) |
| P-series (P4, P5, P6) + Trainium | +15% over EC2 on-demand | **+6%** over EC2 on-demand (−60%) |
| General-purpose (M, C, R, T, etc.) | +15% | unchanged at +15% |

### 🆕 Azure/Microsoft: Annual Local Currency Pricing Cadence Changed (Announced July 8, 2026)

- **Announced**: July 8, 2026 (Microsoft Partner Center July 2026 announcements)
- Beginning **FY27 (July 1, 2026)**, Microsoft is transitioning to **annual local currency pricing updates every January** for Commercial Cloud services.
- **Next local currency update**: January 1, 2027 (then annually each January thereafter).
- **Previously**: Local currency adjustments could occur at any time throughout the year when FX rates moved significantly.
- No immediate price change — this is a structural change to the cadence of FX-driven pricing updates.
- Notifications with guidance on the upcoming year's pricing updates will be issued every November.
- Any product-specific price adjustments (like the July 1, 2026 M365 increases) continue to be communicated separately from the FX cadence.
- Source: [Microsoft Partner Center July 2026 announcements](https://learn.microsoft.com/en-us/partner-center/announcements/2026-july)
- Updated: `providers/azure.md` (Upcoming Changes section)

### 🆕 Azure Blueprints: Retirement Timeline Extended to January 31, 2027 (Announced June 25, 2026)

- **Azure Update ID**: 564806; announced June 25, 2026; retroactively noted here as it falls after the June 27, 2026 changelog entry.
- Originally announced to retire **July 11, 2026**; now extended to **January 31, 2027**.
- **Phased retirement schedule**:
  - **July 31, 2026**: Cannot create new blueprint definitions or versions
  - **October 31, 2026**: Cannot modify definitions or create new assignments
  - **December 31, 2026**: Cannot modify existing assignments
  - **January 31, 2027**: Full retirement — API stops responding
- No pricing impact (Azure Blueprints had no separate charge); purely a management/governance retirement.
- Migrate to: **Azure Deployment Stacks** or **Bicep** (the recommended replacements).
- Source: [Azure Update ID 564806](https://azure.microsoft.com/updates?id=564806)
- Updated: `providers/azure.md` (Upcoming Changes section)

### ✅ No new GCP pricing changes (as of 2026-07-13)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged.
- GCP custom machine type pricing announcement page (cloud.google.com/compute/cmt-pricing-announcement) was last updated July 10, 2026 but reflects the existing 5% CUD premium policy from 2024 — no new changes.
- Cloud Run Service Health (cross-region failover) reached GA in the week of July 6–10, 2026 — no pricing change (standard Cloud Run rates apply).

---

## 2026-07-11

### ⏸️ Azure: Blob Storage 128 KiB Minimum Object Size — **OFFICIALLY PAUSED (confirmed July 11, 2026)**

- **Source**: [Azure Update ID 559756](https://azure.microsoft.com/updates?id=559756), last modified **June 8, 2026** — verified directly from Microsoft's official Azure Updates page today.
- Microsoft has **officially paused** the introduction of a minimum billable object size for the Cool, Cold, and Archive access tiers.
- **Billing behavior will NOT change on July 1, 2026 for either new or existing storage accounts.**
- The previous changelog entry (2026-06-27) incorrectly overrode an earlier "PAUSED" status based on secondary sources. The direct Microsoft source confirms the pause is real and authoritative.
- Microsoft will provide an update on a revised approach and timeline in a future Azure Update.
- **No action required from customers at this time.**
- Status corrected in:
  - `providers/azure.md` — Block Blob Access Tiers note updated; changelog entry label changed from "NOW ACTIVE" to "OFFICIALLY PAUSED"
  - `comparisons/storage.md` — Min billable object size row and callout updated

| What changed | Before (incorrect) | After (correct) |
|---|---|---|
| Policy status | "NOW ACTIVE (new accounts)" | ⏸️ **OFFICIALLY PAUSED** |
| New accounts (Jul 1, 2026) | 128 KiB minimum applies | ❌ No change |
| Existing accounts (Jul 1, 2027) | 128 KiB minimum applies | ❌ No change (pending revised timeline) |
| Customer action needed? | Yes — audit object sizes | No — wait for revised Microsoft announcement |

### ✅ No new AWS pricing changes (as of 2026-07-11)
- Lambda, EC2 on-demand/Savings Plans, S3, RDS, DynamoDB, CloudFront — rates confirmed unchanged.
- EC2 Capacity Blocks for ML remain at July 1, 2026 rates (last updated per 2026-07-09 entry).

### ✅ No new GCP pricing changes (as of 2026-07-11)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — rates confirmed unchanged.
- GCP CDN Interconnect / Direct Peering / Carrier Peering increase (May 1, 2026) remains in effect as previously documented.

---

## 2026-07-09

### ✅ AWS: EC2 Capacity Blocks +20% — **CONFIRMED IN EFFECT (July 1, 2026)**
- All GPU/accelerator Capacity Block families increased +20% effective July 1, 2026, as previously tracked.
- No new rate changes detected since July 1. Current rates:
  - p6-b300.48xlarge: **$112.32/hr** ($14.04/accel)
  - p6-b200.48xlarge: **$98.84/hr** ($12.355/accel)
  - p5e.48xlarge: **$47.76/hr** ($5.97/accel)
  - p5en.48xlarge (US): **$54.92/hr** ($6.865/accel)
  - P6e UltraServer (72× B200): $761.904/hr — **unchanged**
- On-Demand and Savings Plans rates are **unchanged**.
- Source: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ Azure: Blob Storage 128 KiB Minimum Object Size — **NOW ACTIVE for New Accounts (July 1, 2026)**
- As of July 1, 2026, all **new storage accounts** apply a minimum billable object size of **128 KiB** for Cool, Cold, and Archive tiers.
- Existing accounts remain on old billing until **July 1, 2027**.
- Hot tier has no minimum — unaffected.
- Status updated in `providers/azure.md` from "effective tomorrow" to "NOW ACTIVE".

### ✅ Azure: Microsoft 365 Commercial Pricing — **NOW IN EFFECT (July 1, 2026)**
- All M365 commercial price increases effective July 1, 2026 for new customers and renewals.
- Previously tracked in full; status label updated to "NOW IN EFFECT" in `providers/azure.md`.

### 🆕 GCP: Resource-Based CUD Scope Default Changed to Billing Account (June 16, 2026)
- **Effective June 16, 2026**: GCP changed the default scope for resource-based Committed Use Discounts.
- **New billing accounts** and **existing accounts without active commitments** were automatically switched to **billing-account scope** (CUD sharing across all projects enabled by default).
- **Existing accounts with active commitments** on June 16 are unchanged — they remain at project scope until those commitments expire.
- **Before June 16**: Default was project scope — CUDs only covered usage within the purchasing project unless sharing was explicitly enabled.
- **After June 16**: Default is billing-account scope — a single commitment covers eligible usage across all projects linked to the billing account.

| Account type | Before June 16 | After June 16 |
|---|---|---|
| New billing accounts | Project scope | Billing account scope (CUD sharing ON) |
| Existing, no active commitments | Project scope | Billing account scope (auto-switched) |
| Existing, active commitments | Project scope | Unchanged (project scope) |

- **FinOps action**: Teams using project-level cost chargebacks or isolation should audit CUD scope in the Google Cloud Console (Billing → Commitments → CUD scope & settings) and verify commitments aren't subsidizing unintended projects. For new commitments, explicitly set project scope if isolation is needed — billing-account scope is now the default.
- Source: [Usage.ai GCP June 2026 Updates](https://www.usage.ai/blogs/gcp/monthly-updates/gcp-june-2026/); [GCP CUD sharing docs](https://docs.cloud.google.com/compute/docs/committed-use-discounts/share-resource-cuds-across-projects)
- Updated: `providers/gcp.md` (new CUD scope table added in Discounts section)

### 🆕 GCP: Hyperdisk Balanced HA — Maximum Throughput Doubled to 2,400 MiB/s (June 2026, No Price Change)
- **Effective June 2026**: Maximum throughput for Hyperdisk Balanced High Availability disks increased from **1,200 MiB/s → 2,400 MiB/s** (+100%).
- **No price change** — same pricing tier, double the throughput ceiling.
- **C4D machine series** now also supports Hyperdisk Balanced HA (previously limited to other families).
- Benefit for engineers: database workloads (PostgreSQL, MySQL, SAP HANA) on HA-replicated block storage can now sustain 2× the I/O without upgrading to a more expensive disk tier. Reduces the need to over-provision disk throughput for HA setups.
- Source: [GCP June 2026 Updates](https://www.usage.ai/blogs/gcp/monthly-updates/gcp-june-2026/)
- Updated: `providers/gcp.md` (new section added after Hyperdisk ML throughput entry)

### ✅ No new GCP base pricing changes found (as of 2026-07-09)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — all rates confirmed unchanged.
- GCP Cloud Run MCP Server reached GA in June 2026 (developer tooling, no pricing change).
- G4 fractional GPUs and Flex-Start VMs in MIGs confirmed GA (documented previously; no rate changes).
- BigQuery Data Transfer Service label change (August 11, 2026): ~33 days away — update billing dashboards to handle both `DATA_TRANSFER_SERVICE` and `data_transfer_service` labels.

### ✅ No new AWS base pricing changes found (as of 2026-07-09)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront — all rates confirmed unchanged.
- Lambda Managed Instances, Durable Functions: rates unchanged.
- S3 Intelligent-Tiering 128 KB minimum object size threshold: unchanged.
- G7 instances (RTX PRO 4500, GA June 18, 2026): pricing not yet published on EC2 pricing page; monitor [EC2 pricing](https://aws.amazon.com/ec2/pricing/on-demand/).

### ✅ No new Azure IaaS/PaaS pricing changes found (as of 2026-07-09)
- Azure Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN, Azure Functions — all rates unchanged.
- Azure Sentinel 50-GB tier promo extended through Dec 31, 2026 (announced June 26, 2026): already documented in `providers/azure.md`.
- Windows 365 GPU Enterprise Select 256 GB SKU: available July 1, 2026 (new VM SKU, not a pricing change to existing tiers).
- Azure NVv3/NVv4 retirement (Sep 30, 2026): 83 days away — begin migration to NVadsA10 v5 or NCv6.
- Azure GPv1 retirement (Oct 13, 2026): 96 days away.
- Azure Cache for Redis (all customers blocked Oct 1, 2026): 84 days away.

---

## 2026-06-27

### ✅ AWS: EC2 Capacity Blocks +20% — **NOW IN EFFECT as of July 1, 2026** (4 days away)
- Previously announced June 23, 2026; takes effect **July 1, 2026**.
- All GPU/accelerator Capacity Block families increase ~20% on reserved rates. On-Demand and Savings Plans unchanged.
- New per-accelerator rates: P6-B300 $14.04/hr, P6-B200 $12.355/hr, P5e $5.97/hr, P5en (US) $6.865/hr, P5en (non-US) $6.241/hr, P5 (US) $5.191/hr, P5 (non-US) $4.72/hr, P4de (US) $2.214/hr.
- **Action**: Lock in any planned Capacity Block reservations before July 1 to secure current (pre-hike) rates.
- Source: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### 🔄 Azure: Blob Storage 128 KiB Minimum Object Size — **STATUS CORRECTION (NOW CONFIRMED PROCEEDING)**
- **Previous status (Jun 8–Jun 25 in this repo)**: Marked as "PAUSED" based on Azure Update ID 559756.
- **Corrected status (Jun 27, 2026)**: Multiple independent sources from April–June 2026 confirm the policy **is proceeding** on the original schedule. The "pause" appears to have been a very brief or misinterpreted hold.
- **Confirmed timeline**:
  - **July 1, 2026** (4 days): 128 KiB minimum applies to all **new storage accounts** created on/after this date.
  - **July 1, 2027**: Applies to all existing storage accounts.
- **What it means**: Objects in Cool, Cold, or Archive tiers smaller than 128 KiB are billed as 128 KiB. Hot tier is unaffected.
- **Impact example**: 1M × 4 KiB files in Cool → billed as 128 GB instead of ~4 GB (32× cost multiplier for micro-objects).
- **Mitigations**: Pack small objects before tiering; use Smart Tier (GA) to keep objects ≤128 KiB in Hot automatically.
- New Blob Types `BlockBlobSmall` and `Azure Data Lake Storage Small` added to Blob Capacity metrics to support auditing.
- Sources: [nOps (Jun 7, 2026)](https://www.nops.io/blog/azure-storage-pricing/), [Directions on Microsoft (Apr 22, 2026)](https://www.directionsonmicrosoft.com/reports/azure-storage-gets-minimum-billing-size/), [Azure Update (Apr 14, 2026)](https://azure.microsoft.com/en-us/updates/)
- Updated: `providers/azure.md`, `comparisons/storage.md`

### ✅ No new GCP base pricing changes found (as of 2026-06-27)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Functions — all rates confirmed unchanged.
- GCS multi-region price changes (Nearline ↑ $0.010→$0.015; Archive ↓ $0.004→$0.0024 in US/EU) — already in effect and documented.
- BigQuery Data Transfer Service label change (Aug 11, 2026): 45 days away — update billing dashboards.

---

## 2026-06-25

### ⚠️ AWS: EC2 Capacity Blocks — **July 1, 2026 Price Update Published** (Effective in 6 Days)
- **Source**: AWS EC2 Capacity Blocks pricing page (confirmed live, last modified June 23, 2026)
- AWS has published the **July 2026 quarterly price update** for EC2 Capacity Blocks for ML. All affected families increase approximately **+20%** vs current rates. Effective **July 1, 2026**.
- New per-accelerator and per-instance rates (8-accelerator instances except where noted):

| Instance | GPU | Current $/hr (instance) | **New $/hr (effective Jul 1)** | Change |
|---|---|---|---|---|
| p6-b300.48xlarge | 8× B300 | $93.60 ($11.70/accel) | **$112.32** ($14.04/accel) | **+20%** |
| p6-b200.48xlarge | 8× B200 | $82.368 ($10.296/accel) | **$98.84** ($12.355/accel) | **+20%** |
| p5e.48xlarge | 8× H200 | $39.799 ($4.975/accel) | **$47.76** ($5.97/accel) | **+20%** |
| p5en.48xlarge (US) | 8× H200 | $45.768 ($5.721/accel) | **$54.92** ($6.865/accel) | **+20%** |
| p5en.48xlarge (non-US) | 8× H200 | $41.612 ($5.202/accel) | **$49.928** ($6.241/accel) | **+20%** |
| p5.48xlarge (US) | 8× H100 | $34.608 ($4.326/accel) | **$41.528** ($5.191/accel) | **+20%** |
| p5.48xlarge (non-US) | 8× H100 | ~$33.6 (~$4.20/accel) | **~$37.76** ($4.72/accel) | **+12–20%** |
| p4de.24xlarge (US) | 8× A100 (80G) | ~prev rate | **$17.712** ($2.214/accel) | see note |

- **On-Demand and Savings Plans rates are not affected** — only Capacity Blocks reservation fees change.
- History: Jan 2026 (+15%), May 2026 p5en US (+10%), Jul 2026 (+20% across all families). This is the third upward adjustment in 2026 for Capacity Blocks.
- **Action**: Any Capacity Block reservations purchased before July 1 are locked in at current rates. Lock in now if you have near-term reservations planned.
- Source: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/) — updated `providers/aws.md`

### 🆕 AWS: EC2 G7 Instances (NVIDIA RTX PRO 4500 Blackwell) — **Generally Available (June 18, 2026)**
- **GA: June 18, 2026** — AWS is the first major cloud provider to offer NVIDIA RTX PRO 4500 Blackwell Server Edition GPUs
- GPU specs: **32 GB GDDR7 per GPU**, 5th-Gen Tensor Cores, 4th-Gen RT Cores
- CPU: **Custom 6th-Gen Intel Xeon Scalable** processors
- Up to **4.6× AI inference performance** and **2.1× graphics performance** vs G6 instances
- Up to 8 GPUs per instance; up to 192 vCPU; up to 768 GiB RAM; up to 7.6 TB local NVMe; up to **700 Gbps EFA** networking
- Available in: **US East (Ohio)**, **US West (Oregon)** — 7 sizes
- Purchase options: On-Demand, Savings Plans, Spot Instances, Dedicated Instances (12xl, 24xl, 48xl)
- Pricing: Not published in announcement — check [EC2 Pricing page](https://aws.amazon.com/ec2/pricing/on-demand/) for current rates
- **Note**: G7 (RTX PRO 4500, 32 GB/GPU) is distinct from G7e (RTX PRO 6000, 96 GB/GPU, GA Jan 2026). G7 targets graphics/inference/VDI; G7e targets large LLM inference.
- Updated: `providers/aws.md` (new G7 section added), `comparisons/compute.md` (GPU table updated)

### ✅ Azure: Microsoft 365 Commercial Pricing — **NOW IN EFFECT (July 1, 2026)**
- **Status as of 2026-06-25**: Price increases are **now in effect** for new customers and customers renewing on/after July 1, 2026.
- Final confirmed rates (per user/month, annual commitment, USD):
  | SKU | New Price | Change |
  |---|---|---|
  | Microsoft 365 Business Basic | **$7.00** | +16% |
  | Microsoft 365 Business Standard | **$14.00** | +12% |
  | Microsoft 365 E3 | **$39.00** | +8% |
  | Microsoft 365 E5 | **$60.00** | +5% |
  | Office 365 E3 | **$26.00** | +13% |
  | Microsoft 365 F1 | **$3.00** | +33% |
  | Microsoft 365 F3 | **$10.00** | +25% |
- New capabilities bundled: Copilot Chat, Microsoft Defender for Office 365 Plan 1, expanded Intune, +50 GB mailbox storage
- Government GCC/GCC High rates also increased ~8% on affected plans
- Updated: `providers/azure.md` (M365 table updated from "upcoming" to current)

### ✅ Azure: Legacy VM Reserved Instances Discontinuation — **NOW IN EFFECT (July 1, 2026)**
- **Status as of 2026-06-25**: New purchases and renewals of RIs on affected series are now **blocked**.
- No new Reserved VM Instances can be purchased or renewed for: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2, Dv3, Dsv3, Ev3, Esv3
- Existing RIs continue through their purchased term; auto-renew on affected series will fail silently
- Migration: newer VM series (Dv5, Ev5, etc.) + Azure Savings Plan for Compute remain available
- Updated: `providers/azure.md` (moved from Upcoming Changes to current; `comparisons/compute.md`)

### ✅ No new GCP pricing changes found (as of 2026-06-25)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — all rates confirmed unchanged
- GCP CDN Interconnect/Peering price increases (effective May 1, 2026) remain in effect; no further changes
- GCP Datastream perpetual free tier (100 GiB/month for AlloyDB/Spanner → BigQuery, effective June 2, 2026) — no changes
- BigQuery Data Transfer Service label change (upcoming Aug 11, 2026): 47 days away — update billing dashboards to handle both `DATA_TRANSFER_SERVICE` and `data_transfer_service` labels before then

---

## 2026-06-23

### ⏰ Azure: Microsoft 365 Commercial Pricing Increases — **8 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-23**: 8 days until the effective date. **Last realistic window to renew before June 30.**
- No new information since the June 21 entry — all previously confirmed price increases remain on schedule.
- Key reminder (per user/month, annual commitment, USD):
  | SKU | Old Price | New Price | Change |
  |---|---|---|---|
  | Microsoft 365 Business Basic | $6.00 | **$7.00** | +16% |
  | Microsoft 365 Business Standard | $12.50 | **$14.00** | +12% |
  | Microsoft 365 E3 | $36.00 | **$39.00** | +8% |
  | Microsoft 365 E5 | $57.00 | **$60.00** | +5% |
  | Office 365 E3 | $23.00 | **$26.00** | +13% |
  | Microsoft 365 F1 | $2.25 | **$3.00** | +33% |
  | Microsoft 365 F3 | $8.00 | **$10.00** | +25% |
- Packaging changes (Copilot Chat, Defender for Office 365 Plan 1, Intune expansions) rolling out in tenants starting June 2026 — expect Message Center notifications 30 days prior.
- Source: [microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates](https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates)

### ⏰ Azure: Legacy VM Reserved Instances Discontinuation — **8 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-23**: 8 days remaining. Final opportunity to purchase or renew RIs on affected series.
- No new information since June 21 — deadline and affected series list unchanged:
  - **1-year RIs ending**: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2
  - **1-year and 3-year RIs ending**: Dv3, Dsv3, Ev3, Esv3
- Existing RIs continue through their current purchased term; **auto-renew will silently fail** post-July 1 on these series.
- Migration path: newer VM series (Dv5, Ev5, Lsv3) + Azure Savings Plan for Compute.
- Source: [Azure Update ID 560948](https://azure.microsoft.com/en-us/updates/) / [Transition guide](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/manage-legacy-vm-reservations-after-july-1-2026)

### ⏰ AWS: EC2 Capacity Blocks for ML — July 2026 Pricing Review Still Pending
- **Status as of 2026-06-23**: AWS pricing page still reads **"current prices are scheduled to be updated next in July, 2026."** No rate change published yet.
- All Capacity Block rates confirmed unchanged (verified June 23, 2026):
  - **p5e.48xlarge** (8× H200): $39.799/hr (most regions); $49.749/hr (US West N. California)
  - **p5en.48xlarge** (8× H200): $45.768/hr (US regions); $41.612/hr (EU/Asia)
  - **p6-b200.48xlarge** (8× B200): $82.368/hr ($10.296/accelerator)
  - **p6-b300.48xlarge** (8× B300): $93.60/hr ($11.70/accelerator)
  - **P6e UltraServer u-p6e-gb200x72** (72× B200): $761.904/hr (US East Dallas Local Zone)
- On-Demand and Savings Plans rates for all EC2 instances remain **unchanged**.
- Watch: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new AWS base pricing changes found (as of 2026-06-23)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront — all rates confirmed unchanged.
- Lambda free tier unchanged: 1M requests + 400,000 GB-seconds/month (permanent).
- S3 pricing stable: Standard $0.023/GB (first 50 TB), $0.022/GB (51–500 TB), $0.021/GB (>500 TB).
- AWS Free Tier (credit-based model for accounts ≥ Jul 15, 2025): $100 signup credit + up to $100 earned credit — no changes.

### ✅ No new GCP pricing changes found (as of 2026-06-23)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — all rates confirmed unchanged.
- GCP CDN Interconnect/Peering price increases (effective May 1, 2026) remain in effect; no further changes.
- N4A (Axion ARM), G4 (RTX PRO 6000), Fractional G4, TPU v7 Ironwood — all at previously documented rates.
- GCP Datastream perpetual free tier (100 GiB/month for AlloyDB/Spanner → BigQuery) effective June 2, 2026 — no changes.
- BigQuery Data Transfer Service label change (upcoming Aug 11, 2026): still on schedule — update billing dashboards to handle both `DATA_TRANSFER_SERVICE` and `data_transfer_service` labels before then.

### ✅ No new Azure base pricing changes found (as of 2026-06-23)
- Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN — all rates confirmed unchanged.
- Azure Blob Storage 128 KiB minimum object size: still **PAUSED** (paused June 8, 2026) — no new timeline published.
- Azure Cobalt 200 VMs (Early Access Preview since June 2, 2026): pricing still not published.
- Azure NVv3/NVv4 GPU retirement (Sep 30, 2026): 99 days away — no new developments.
- Azure Cache for Redis existing-customer new-instance block (Oct 1, 2026): 100 days away — no new developments.

---

## 2026-06-21

### ⏰ Azure: Microsoft 365 Commercial Pricing Increases — **10 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-21**: 10 days until the effective date. Renew **before June 30** to lock in current rates for one additional year.
- Increases apply to new customers and renewing customers on their first renewal after July 1, 2026
- Key price changes confirmed (per user/month, annual commitment, USD):
  | SKU | Old Price | New Price | Change |
  |---|---|---|---|
  | Microsoft 365 Business Basic | $6.00 | **$7.00** | +16% |
  | Microsoft 365 Business Standard | $12.50 | **$14.00** | +12% |
  | Microsoft 365 Business Premium | $22.00 | $22.00 | — no change |
  | Microsoft 365 E3 | $36.00 | **$39.00** | +8% |
  | Microsoft 365 E5 | $57.00 | **$60.00** | +5% |
  | Office 365 E3 | $23.00 | **$26.00** | +13% |
  | Office 365 E5 | $38.00 | **$41.00** | +8% |
  | Microsoft 365 F1 | $2.25 | **$3.00** | +33% |
  | Microsoft 365 F3 | $8.00 | **$10.00** | +25% |
- Also increasing: Office 365 E3 without Teams: $14.45 → $17.45 (+14%); M365 E3 without Teams: $27.45 → $30.45 (+11%)
- Standalone components also increasing: Windows E3 +15%, EMS E3 +13%, Entra Plan 1 +16%, M365 Apps +17%
- Bundled new capabilities: Copilot Chat, Microsoft Defender for Office 365 Plan 1, expanded Intune, +50 GB mailbox storage
- **Government GCC/GCC High**: same effective date, ~8% increases on affected plans
- **Education**: no changes. **Consumer**: no changes.
- Note: For large enterprises combining this increase with the Nov 2025 removal of EA volume discount tiers (Levels B–D), the effective cost rise may be closer to 15–20%
- Source: [microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates](https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates)

### ⏰ Azure: Legacy VM Reserved Instances Discontinuation — **10 Days Away** (Effective July 1, 2026)
- **Status as of 2026-06-21**: 10 days until the hard deadline. **No new purchases or renewals after June 30, 2026.**
- After July 1: affected RIs cannot be purchased or renewed — auto-renew silently blocked; workloads fall back to pay-as-you-go when the RI expires
- Full affected series (unchanged):
  - **1-year RIs ending**: Av2, Amv2, Bv1, D, Ds, Dv2, Dsv2, F, Fs, Fsv2, G, Gs, Ls, Lsv2
  - **1-year and 3-year RIs ending**: Dv3, Dsv3, Ev3, Esv3
- Highest-impact: **Dv3/Dsv3 and Ev3/Esv3** — widely deployed general-purpose and memory-optimized series
- Existing RIs remain valid through their full purchased term; only new purchases/renewals are blocked
- Migration paths: newer series (Dv5, Ev5, Lsv3) + Azure Savings Plan for Compute
- Source: [Azure Update ID 560948](https://azure.microsoft.com/en-us/updates/) / [Transition guide](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/manage-legacy-vm-reservations-after-july-1-2026)

### ⏰ AWS: EC2 Capacity Blocks for ML — July 2026 Pricing Review Imminent
- **Status as of 2026-06-21**: AWS pricing page still states "current prices are scheduled to be updated next in July, 2026." No rate changes have published yet. The July review could arrive any day.
- All Capacity Block rates remain unchanged (confirmed live from pricing page as of June 21, 2026):
  - **p5e.48xlarge** (8× H200): $39.799/hr (most regions); $49.749/hr (US West N. California)
  - **p5en.48xlarge** (8× H200): $45.768/hr (US regions); $41.612/hr (EU/Asia)
  - **p6-b200.48xlarge** (8× B200): $82.368/hr ($10.296/accelerator)
  - **p6-b300.48xlarge** (8× B300): $93.60/hr ($11.70/accelerator)
  - **P6e UltraServer u-p6e-gb200x72** (72× B200): $761.904/hr ($10.582/accelerator, US East Dallas Local Zone)
  - **P6e UltraServer u-p6e-gb200x36** (36× B200): $380.952/hr ($10.582/accelerator, US East Dallas Local Zone)
- On-Demand and Savings Plans rates for all EC2 instances remain **unchanged**
- History: Jan 2026 +15% hike; Apr 2026 review passed without base-rate change; next review = July 2026
- **Watch**: [AWS EC2 Capacity Blocks Pricing](https://aws.amazon.com/ec2/capacityblocks/pricing/)

### ✅ No new AWS base pricing changes found (as of 2026-06-21)
- Lambda, S3, RDS, Aurora, EKS, DynamoDB, CloudFront — all rates confirmed unchanged
- S3 pricing structure stable: Standard $0.023/GB (first 50 TB), $0.022/GB (51–500 TB), $0.021/GB (>500 TB)
- AWS Free Tier: credit-based model for accounts ≥ Jul 15, 2025 unchanged ($200 credit, 6-month Free Plan)

### ✅ No new GCP pricing changes found (as of 2026-06-21)
- Compute Engine, Cloud Run, Cloud SQL, BigQuery, GKE, Cloud Storage, Cloud Functions — all rates confirmed unchanged
- GCP CDN Interconnect/Peering price increases (effective May 1, 2026) remain in effect; no further changes since
- N4A (Axion ARM), G4 (RTX PRO 6000), Fractional G4, TPU v7 Ironwood — all at previously documented rates
- No new GCP pricing announcements found in June 2026 press releases (GCP London Summit June 17 focused on partnerships, not pricing)

### ✅ No new Azure base pricing changes found (as of 2026-06-21)
- Blob Storage, Azure Files, Azure SQL, AKS, App Service, CDN — all rates confirmed unchanged
- **Azure Blob Storage 128 KiB minimum object size**: still **PAUSED** (paused June 8, 2026) — no new timeline published
- Azure Cobalt 200 VMs (Early Access Preview since June 2, 2026): pricing still not published
- Azure NVv3/NVv4 GPU retirement (Sep 30, 2026): 101 days away — no new developments

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
