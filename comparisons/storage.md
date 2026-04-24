# Object Storage Pricing Comparison — S3 vs GCS vs Azure Blob

> Last updated: 2026-04-24  
> All prices are for primary US regions (us-east-1 / us-central1 / East US LRS). Prices in USD per GB unless noted.

## Storage Tiers — Side-by-Side

| Tier / Use Case | AWS S3 | GCP Cloud Storage | Azure Blob (LRS) |
|---|---|---|---|
| **Frequent access** | Standard: **$0.023/GB** | Standard: **$0.020/GB** | Hot: **$0.018/GB** |
| **Infrequent (~1×/mo)** | Standard-IA: **$0.0125/GB** | Nearline: **$0.010/GB** | Cool: **$0.010/GB** |
| **Rare (~1×/quarter)** | One Zone-IA: **$0.010/GB** | Coldline: **$0.004/GB** | Cold: **$0.0045/GB** |
| **Archival / deep cold** | Glacier Flexible: **$0.0036/GB** | Archive: **$0.0012/GB** | Archive: **$0.00099/GB** |
| **Cheapest archival** | Glacier Deep Archive: **$0.00099/GB** | Archive: **$0.0012/GB** (regional) / **$0.0024/GB** (multi-region) | Archive: **$0.00099/GB** |
| **Intelligent/auto-tiering** | Intelligent-Tiering: $0.023 (frequent) / $0.0125 (infrequent) | — | — |
| **Min storage duration** | None (Standard); 30–180 days (IA/Glacier) | None (Standard); 30–365 days (Nearline–Archive) | None (Hot); 30–180 days (Cool–Archive) |

> **Cheapest hot storage**: Azure ($0.018) > GCP ($0.020) > AWS ($0.023)  
> **Cheapest archive**: AWS Deep Archive ≈ Azure ($0.00099); GCP regional Archive slightly higher ($0.0012)  
> ⚠️ **GCS 2026 multi-region changes**: Nearline multi-region ⬆️ $0.010 → **$0.015/GB**; Archive multi-region ⬇️ $0.004 → **$0.0024/GB** (US/EU)

## Retrieval Fees

| Provider | Tier | Retrieval Fee |
|---|---|---|
| AWS | Standard | None |
| AWS | Standard-IA | $0.01/GB |
| AWS | Glacier Instant | $0.03/GB |
| AWS | Glacier Flexible | $0.01/GB (standard), free (bulk, 5–12 hrs) |
| AWS | Glacier Deep Archive | $0.02/GB (standard) |
| GCP | Standard | None |
| GCP | Nearline | $0.01/GB |
| GCP | Coldline | $0.02/GB |
| GCP | Archive | $0.05/GB |
| Azure | Hot | None |
| Azure | Cool | $0.01/GB |
| Azure | Cold | $0.02/GB |
| Azure | Archive | $0.022/GB (standard rehydration) |

## Egress Costs (to Internet)

| Provider | First | Subsequent | Notes |
|---|---|---|---|
| AWS S3 | 100 GB/mo free | $0.09/GB (up to 10 TB) → $0.085–$0.07 | Tiered discounts at higher volumes |
| GCP Cloud Storage | — | $0.08–$0.15/GiB (by region) | |
| Azure Blob | 5 GB/mo free | $0.087/GB (up to 10 TB) | |

> ⚠️ **GCP CDN Interconnect egress doubling effective May 1, 2026 (7 days away)**:  
> North America: $0.04 → **$0.08/GiB** (+100%)  
> Europe: $0.05 → **$0.08/GiB** (+60%)  
> Asia: $0.06 → **$0.085/GiB** (+42%)  
> Affects CDN Interconnect, Direct Peering, and Carrier Peering. Standard internet egress rates unchanged.  
> Consider migrating to Verified Peering Provider (VPP) — Google's recommended alternative with SLA.

> ⚠️ **Azure GPv1 Storage Retirement (October 13, 2026)**:  
> New GPv1 account creation has been blocked since **March 3, 2026**.  
> Remaining GPv1 accounts will be auto-migrated to GPv2 on October 13, 2026.  
> Migration may change billing: GPv2 uses per-blob tiering and different operation rates.  
> GPv2 is generally cheaper overall once tiering and modern pricing is factored in.

## Inter-Region / Cross-Region Egress

| Provider | Same Region | Cross-Region (US) | Cross-Region (US↔EU) |
|---|---|---|---|
| AWS | Free | $0.02/GB | $0.02/GB |
| GCP | Free | Free (same continent) | ~$0.05/GiB |
| Azure | Free | $0.02/GB | $0.02/GB |

## Operations Pricing

| Operation | AWS S3 | GCP Cloud Storage | Azure Blob (Hot) |
|---|---|---|---|
| PUT / COPY / POST / LIST | $0.005 / 1,000 | $0.05 / 10,000 | $0.0000535 / 10,000 |
| GET / SELECT | $0.0004 / 1,000 | $0.004 / 10,000 | $0.0000044 / 10,000 |

## Free Tier

| Provider | Allowance | Expiry |
|---|---|---|
| AWS S3 | 5 GB Standard + 20K GET + 2K PUT/mo | 12 months (new accounts) |
| GCP Cloud Storage | 5 GB regional storage/mo | Permanent (Always Free) |
| Azure Blob | 5 GB LRS Hot/mo | 12 months (new accounts) |

## File System Access to Object Storage

| Provider | Feature | GA Date | Cost vs Managed File System |
|---|---|---|---|
| AWS | **S3 Files** (NFS v4.2 mount on S3 buckets) | Apr 7, 2026 🆕 | Cached storage: $0.30/GB-mo (hot data only); cold S3 data at $0.023/GB-mo. ~13× cheaper than EFS for large datasets with small active sets |
| GCP | **Cloud Storage FUSE** (gcsfuse) | GA | Free (open-source tool); standard GCS storage + operation charges apply |
| Azure | **NFS 3.0 on Blob Storage** (Premium Block Blob) | GA | $0.15/GB-mo (LRS); higher than standard Blob but lower than Azure Files |

> 🆕 **AWS S3 Files (April 2026)**: S3 Files also works with Lambda as of April 21, 2026 — mount an S3 bucket directly in a Lambda function at no extra charge. Multiple functions can share the same S3 file system simultaneously. Compare: EFS Standard costs $0.30/GB-mo for **all** data; S3 Files charges $0.30/GB-mo only for cached/hot data and $0.023/GB-mo for cold S3 data.

## Key Differences Summary

| Topic | AWS | GCP | Azure |
|---|---|---|---|
| Pricing model | Tiered egress, per-operation | Per-operation + egress | Per-GB + per-operation + egress |
| Intelligent auto-tiering | ✅ S3 Intelligent-Tiering | ❌ (manual lifecycle rules) | ❌ (lifecycle rules available) |
| Cheapest hot tier | $0.023/GB | $0.020/GB | $0.018/GB |
| File system access | ✅ S3 Files (NFS, GA Apr 2026) 🆕 | ✅ gcsfuse (FUSE-based) | ✅ NFS 3.0 on Premium Blob |
| Lambda/serverless mount | ✅ S3 Files (Apr 21, 2026) 🆕 | ✅ gcsfuse via Cloud Run | ❌ (not native on Consumption plan) |
| CDN interconnect | Standard egress | ⚠️ Rising May 2026 | Standard CDN rates |
| Legacy account types | N/A | N/A | ⚠️ GPv1 retiring Oct 2026 |
