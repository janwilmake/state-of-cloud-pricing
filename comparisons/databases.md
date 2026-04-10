# Managed Database Pricing Comparison — AWS vs GCP vs Azure

> Last updated: 2026-04-10  
> All prices are on-demand, primary US regions, single-instance unless noted. Prices in USD.

## Managed PostgreSQL

### Entry-Level (1–2 vCPU, shared or burstable)

| Provider | Service | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | RDS PostgreSQL (db.t3.micro) | 2 | 1 GB | $0.018 | $13.14 | Single-AZ |
| AWS | RDS PostgreSQL (db.t3.medium) | 2 | 4 GB | $0.068 | $49.64 | Single-AZ |
| GCP | Cloud SQL (db-f1-micro) | shared | 0.6 GB | $0.015 | $10.95 | |
| GCP | Cloud SQL (db-g1-small) | shared | 1.7 GB | $0.050 | $36.50 | |
| Azure | PostgreSQL Flex (B1ms) | 1 | 2 GB | $0.021 | $15.33 | |

### Production (2 vCPU / 8 GB RAM)

| Provider | Service | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | RDS PostgreSQL (db.m5.large) | 2 | 8 GB | $0.171 | $124.83 | Single-AZ |
| AWS | RDS Multi-AZ (db.m5.large) | 2 | 8 GB | $0.342 | $249.66 | Multi-AZ |
| GCP | Cloud SQL (db-custom-2-4096) | 2 | 4 GB | $0.104 | $75.92 | |
| GCP | Cloud SQL (db-custom-2-8192) | 2 | 8 GB | ~$0.183 | ~$133.59 | Approx. |
| Azure | PostgreSQL Flex (D2s v3) | 2 | 8 GB | $0.170 | $124.10 | |

### Production (4 vCPU / 16 GB RAM)

| Provider | Service | vCPU | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|---|
| AWS | RDS PostgreSQL (db.m5.xlarge) | 4 | 16 GB | $0.342 | $249.66 | Single-AZ |
| GCP | Cloud SQL (db-custom-4-8192) | 4 | 8 GB | $0.208 | $151.84 | |
| Azure | PostgreSQL Flex (D4s v3) | 4 | 16 GB | $0.340 | $248.20 | |

### Storage Pricing

| Provider | $/GB-mo | I/O |
|---|---|---|
| AWS RDS (gp3) | $0.125 | $0.02/million I/O (gp2 only; gp3 I/O included) |
| GCP Cloud SQL (SSD) | $0.170 | Included |
| Azure PostgreSQL Flex (Premium SSD) | $0.115 | Included |

---

## Serverless / Autoscaling Postgres

| Provider | Service | Notes |
|---|---|---|
| AWS | Aurora Serverless v2 | Scales in 0.5 ACU increments; $0.12/ACU-hr; min 0 ACUs (pause) |
| GCP | AlloyDB Omni / Cloud SQL autoscale | Limited autoscaling; AlloyDB from $0.6952/vCPU-hr |
| Azure | Azure SQL Serverless | Auto-pauses; billed per vCore-second |

---

## Aurora vs Cloud Spanner vs Azure SQL — Enterprise Tier

### Amazon Aurora (PostgreSQL-compatible, us-east-1)

| Instance | vCPU | RAM | $/hr |
|---|---|---|---|
| db.r4.2xlarge | 8 | 61 GB | $1.16 |
| db.r5.2xlarge | 8 | 64 GB | $1.20 |

Storage: $0.10/GB-mo. I/O: $0.20/million requests. No charge for replicas in read-heavy workloads (Aurora I/O-Optimized tier available).

### GCP Cloud Spanner

| Config | $/node-hr | $/GB-mo storage |
|---|---|---|
| Regional | $0.90 | $0.30 |
| Multi-regional | $3.00 | $0.50 |

Note: Spanner is a globally distributed NewSQL database — not a direct Postgres equivalent.

### Azure SQL Database (General Purpose, 8 vCores)

| vCores | $/hr | $/mo |
|---|---|---|
| 8 | $1.4496 | $1,058.21 |

Storage: $0.115/GB-mo.

---

## Redis / In-Memory Cache

### Managed Redis Comparison (1 instance, standard tier)

| Provider | Service | RAM | $/hr | $/mo | Notes |
|---|---|---|---|---|---|
| AWS | ElastiCache cache.t3.micro | 0.5 GB | $0.017 | $12.41 | |
| AWS | ElastiCache cache.m5.large | 6.38 GB | $0.136 | $99.28 | |
| AWS | ElastiCache cache.r6g.large | 13.07 GB | $0.171 | $124.83 | Graviton2 |
| GCP | Memorystore Basic | — | $0.049/GB-hr | — | Per GB-hr |
| GCP | Memorystore Standard (HA) | — | $0.098/GB-hr | — | Per GB-hr |
| Azure | Cache for Redis Basic C0 | 250 MB | $0.022 | $16.06 | No replication |
| Azure | Cache for Redis Standard C1 | 1 GB | $0.093 | $67.89 | Replicated |
| Azure | Cache for Redis Premium P1 | 6 GB | $0.554 | $404.42 | HA + clustering |

> **GCP Memorystore** pricing is per GB-hour. A 6 GB Standard instance: 6 × $0.098 = $0.588/hr → ~$429/mo.

---

## NoSQL / Key-Value Databases

| Provider | Service | Write | Read | Storage |
|---|---|---|---|---|
| AWS | DynamoDB On-Demand | $1.25/million WRUs | $0.25/million RRUs | $0.25/GB-mo (25 GB free) |
| GCP | Firestore | $0.18/100K writes | $0.06/100K reads | $0.18/GB-mo |
| Azure | Cosmos DB Serverless | $0.282/million RUs | — | $0.25/GB-mo |

---

## Free Tier Summary

| Provider | Service | Free Allowance | Expiry |
|---|---|---|---|
| AWS | RDS (db.t3.micro) | 750 hr/mo + 20 GB storage | 12 months |
| AWS | DynamoDB | 25 GB + 25 WCU + 25 RCU/mo | Permanent |
| GCP | Cloud SQL | None | — |
| GCP | Firestore | 1 GB + 50K reads + 20K writes/day | Permanent |
| Azure | Azure SQL | 250 GB S0 instance | 12 months |
| Azure | Cosmos DB | 1,000 RU/s + 25 GB | Permanent |
