# Serverless Pricing Comparison — Lambda vs Cloud Functions vs Azure Functions

> Last updated: 2026-04-26  
> All prices are for primary US regions unless noted. Prices in USD.

## Invocation / Request Pricing

| Provider | Service | $/million requests | Free tier (monthly) |
|---|---|---|---|
| AWS | Lambda | $0.20 | 1M requests (permanent) |
| GCP | Cloud Run Functions (2nd gen) | $0.40 | 2M invocations (permanent) |
| Azure | Functions (Consumption) | $0.20 | 1M requests (permanent) |

> GCP is **2× more expensive** per request than AWS and Azure at list price, but includes a larger free tier (2M vs 1M).

## Duration / Compute Pricing

| Provider | Service | Architecture | $/GB-second | Notes |
|---|---|---|---|---|
| AWS | Lambda | x86 | $0.0000166667 | |
| AWS | Lambda | ARM (Graviton2) | $0.0000133334 | ~20% cheaper |
| GCP | Cloud Run Functions (2nd gen) | x86 | $0.0000025/GB-s + $0.000024/vCPU-s | Separate memory and CPU billing |
| Azure | Functions (Consumption) | x86 | $0.000016 | |

> **GCP bills memory and CPU separately** for 2nd gen functions. For a 1 vCPU / 256 MB function running 1 second:  
> GCP: (0.25 GB × $0.0000025) + (1 vCPU × $0.000024) = ~$0.0000243  
> AWS (x86): 0.25 GB × $0.0000166667 = ~$0.0000042  
> AWS (ARM): 0.25 GB × $0.0000133334 = ~$0.0000033  
> Azure: 0.25 GB × $0.000016 = ~$0.000004

## Free Tier Comparison

| Provider | Requests/month | Compute/month | Egress | Expiry |
|---|---|---|---|---|
| AWS Lambda | 1M | 400,000 GB-seconds | — | Permanent |
| GCP Cloud Run Functions | 2M | 400,000 GB-s memory + 200,000 vCPU-s | 5 GB network/mo | Permanent |
| Azure Functions (Consumption) | 1M | 400,000 GB-seconds | — | Permanent |

## Memory & Runtime Limits

| Provider | Min Memory | Max Memory | Max Timeout | Min Billing Unit |
|---|---|---|---|---|
| AWS Lambda | 128 MB | 10,240 MB | 15 min | 1 ms |
| GCP Cloud Run Functions (2nd gen) | 128 MB | 32 GB | 60 min | 100 ms |
| Azure Functions (Consumption) | 128 MB | 1,536 MB | 5 min (default) / 10 min (max) | 1 ms |
| Azure Functions (Premium) | up to 14 GB (EP3) | — | Unlimited | per second |

## Cold Start Behavior

| Provider | Notes |
|---|---|
| AWS Lambda | **August 2025 change**: INIT (cold start initialization) phase is now billed. Previously free. Especially impacts heavy runtimes (Java, C#). |
| GCP Cloud Run Functions | Cold starts typically < 500 ms for Node/Python; heavier for JVM |
| Azure Functions (Consumption) | Cold starts present; Premium plan has always-warm instances |
| Azure Functions (Flex Consumption) | Faster cold starts than standard Consumption; recommended for new apps. ⚠️ **Migrate to this plan if on Linux Consumption + runtime v3** (stops running Sep 30, 2026) |
| Azure Functions (Premium) | No cold starts — at least one instance always warm |

## Networking Costs

| Provider | Outbound Egress |
|---|---|
| AWS Lambda | No direct egress charge for Lambda; data transfer charges apply via VPC/internet gateway |
| GCP Cloud Run Functions | $0.12/GB outbound (above 5 GB free tier) |
| Azure Functions | Standard Azure egress rates apply ($0.087/GB first 10 TB) |

## Feature Comparison

| Feature | AWS Lambda | GCP Cloud Run Functions (2nd gen) | Azure Functions |
|---|---|---|---|
| VNet / Private networking | ✅ | ✅ | ✅ (Premium/Flex) |
| Containers | ✅ (up to 10 GB image) | ✅ | ✅ (Premium) |
| Min instances (always warm) | ✅ (Provisioned Concurrency) | ✅ (min-instances) | ✅ (Premium plan) |
| ARM architecture | ✅ (Graviton2) | ❌ | ❌ |
| Dedicated compute option | ✅ (Lambda Managed Instances, 2026) | ✅ (Cloud Run, separate product) | ✅ (Dedicated plan) |
| Shared file system mount | ✅ S3 Files or EFS (Apr 2026) 🆕 | ✅ gcsfuse (Cloud Storage) | ✅ Azure Files (Premium plan) |
| Max deployment package | 50 MB (zip) / 10 GB (container) | 100 MB (zip) / large containers | 500 MB |

## Lambda S3 Files Integration (New April 21, 2026) 🆕

AWS Lambda now supports mounting Amazon S3 buckets as file systems using **S3 Files** (GA April 7, 2026; Lambda support added April 21, 2026):

- Mount any S3 bucket directly in a Lambda function via NFS v4.2 — no SDK calls needed
- Use standard file operations (`fs.readFile`, `ls`, `cp`, etc.) on the mount path (e.g., `/mnt/s3files`)
- Multiple Lambda functions can connect to the **same** S3 file system simultaneously for shared workspaces
- **No additional charge** beyond standard Lambda and S3 pricing

| Cost Component | Rate |
|---|---|
| Lambda compute | Standard $0.0000166667/GB-s (x86) or $0.0000133334/GB-s (ARM) |
| S3 Files cached storage | $0.30/GB-month (only for actively cached hot data) |
| Large file reads (≥1 MB) | Standard S3 GET rates — no S3 Files surcharge |
| Small file reads (from cache) | $0.03/GB |
| S3 Files writes | $0.06/GB |
| Cold S3 storage | Standard S3 tier rates ($0.023/GB-month Standard) |

> **vs EFS**: EFS Standard = $0.30/GB-month for **all** data; S3 Files = $0.30/GB-month only for cached/active data. For large ML model repositories or training data (e.g., 10 TB total, 200 GB hot), S3 Files can be ~13× cheaper than EFS.  
> **Limitation**: S3 Files is not compatible with Lambda functions configured with a capacity provider.  
> **Ideal for**: Shared ML model serving, shared config/reference data across functions, agentic AI workspaces, large-file ETL pipelines.

## Lambda Managed Instances (New in 2026)

AWS introduced Lambda Managed Instances allowing Lambda to run on dedicated EC2 instance types for high-throughput, latency-sensitive workloads:
- Runs on user-specified EC2 instance types (e.g., m7g.xlarge)
- Request charge: $0.20/million (same as standard Lambda)
- Compute management fee: +15% on top of EC2 on-demand price
- Normal EC2 instance charges apply (Savings Plans and RIs eligible)

## Lambda Tenant Isolation Mode (New November 2025)

For SaaS platforms requiring per-tenant isolation without managing separate functions:
- Additional charge per new tenant execution environment created (based on memory + architecture)
- Example (1,024 MB, ARM): ~$0.000167/environment — 200K environments/month ≈ $33.40/month
- Standard request + duration charges also apply
- Not compatible with Provisioned Concurrency, SnapStart, or Function URLs
- Means more cold starts (each tenant gets its own environment)

## ⚠️ Platform Retirements & Breaking Changes

| Provider | Service | Retirement Date | Action Required |
|---|---|---|---|
| Azure | Functions runtime **v3** on Linux Consumption | **Sep 30, 2026** | Migrate to runtime v4; consider Flex Consumption plan |
| Azure | Functions **Linux Consumption** plan | Sep 30, 2028 | Migrate to Flex Consumption plan |
| AWS | Lambda INIT (cold start) billing | **Live since Aug 2025** | Optimize heavy runtimes; use SnapStart for Java |

> ⚠️ **Azure Functions runtime v3 on Linux Consumption** (announced April 17, 2026, Azure ID 559311):  
> After **September 30, 2026**, Function Apps running on runtime v3 + Linux Consumption will **not start or execute**. Runtime v3 was officially retired December 13, 2022 but continued running — enforcement is now being applied.  
> **Migration path**: Upgrade to runtime v4 **and** migrate the hosting plan to **Flex Consumption** (recommended, supports v4 + ongoing updates) before the deadline.

## Lambda Durable Functions (New 2026)

Built-in checkpoint/replay orchestration — an alternative to Step Functions for tightly-coupled multi-step workflows:
- Standard Lambda compute charges apply for all invocations (including replay sub-invocations)
- **No duration charges while paused** (`wait` operations — function suspends without billing)
- Additional charges for durable operations (start, step complete, wait create, etc.)
- Data write charges per GB of checkpoint data
- Data retention charges per GB-month (1–90 day configurable retention; default 14 days)
- SDKs: JavaScript/TypeScript, Python, Java (GA v1.0.0: March 27, 2026)
- Best for: long-running workflows (hours/days) with human-in-the-loop, LLM pipelines, insurance claims processing
