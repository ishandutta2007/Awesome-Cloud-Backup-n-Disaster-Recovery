# Awesome-Cloud-Backup-n-Disaster-Recovery

# Top Cloud Backup & Disaster Recovery Platforms Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**
*Focused on Data Protection, Ransomware Resilience, SaaS Backup & Kubernetes Disaster Recovery*
**Last updated: September 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Cloud Backup & Disaster Recovery**. These tools help organizations protect workloads across on-premises, cloud, and SaaS environments—from VM backup and Kubernetes disaster recovery to Microsoft 365 and Google Workspace data protection.

**Examples** include Veeam, Acronis, Druva, Cohesity, HYCU, Rubrik, CrashPlan, Backblaze Business, Spanning, and Keepit (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom backup pipelines, and transparent data protection—ideal for organizations that need full control over their backup infrastructure without per-workload SaaS fees or vendor lock-in.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Veeam](https://www.veeam.com/)**
  Industry-standard backup and recovery platform for virtual, physical, cloud, and SaaS workloads. Provides Veeam Backup & Replication, Veeam Backup for Microsoft 365, and Veeam Kasten for Kubernetes data protection. SOC 2 Type II compliant.

- **[Acronis](https://www.acronis.com/)**
  Cyber protection platform combining backup, disaster recovery, and cybersecurity. Provides image-based backup, ransomware protection, and cloud-to-cloud backup for Microsoft 365.

- **[Druva](https://www.druva.com/)**
  Cloud-native data protection platform for endpoints, SaaS applications, and cloud workloads. Provides centralized management, retention, search, and compliance reporting.

- **[Cohesity](https://www.cohesity.com/)**
  Data management platform consolidating backup, recovery, and data security. Provides immutable backups and ransomware detection.

- **[HYCU](https://www.hycu.com/)**
  Purpose-built backup and recovery for Nutanix, VMware, and cloud workloads. Provides application-aware protection with granular recovery.

- **[Rubrik](https://www.rubrik.com/)**
  Zero trust data security platform with immutable backups and ransomware recovery. Provides data observability and governance.

- **[CrashPlan](https://www.crashplan.com/)**
  Endpoint backup and recovery for small businesses. Provides continuous backup, version history, and cross-platform restore.

- **[Backblaze Business](https://www.backblaze.com/)**
  Cloud storage and backup platform. Provides unlimited endpoint backup and B2 cloud storage for offsite data protection.

- **[Spanning (Kaseya)](https://spanning.com/)**
  SaaS backup and recovery for Microsoft 365, Google Workspace, and Salesforce. Protects over 24,000 organizations with automated daily backups and infinite retention .

- **[Keepit](https://www.keepit.com/)**
  Independent cloud backup for SaaS applications including Microsoft 365, Google Workspace, and Salesforce. Provides immutable data protection and instant recovery.

## Open-Source GitHub Projects

### Cross-Platform Backup Engines

- **[Bareos](https://github.com/bareos/bareos)**
  **The most mature open-source enterprise backup solution.** Cross-network backup and recovery licensed under **AGPLv3** with **no open-core restrictions** . Supports Linux, Windows, FreeBSD, macOS, and other major operating systems. **Key features**: Flexible storage targets (disk, tape, S3-compatible object storage); deduplication-friendly storage optimized for ZFS, VDO, or btrfs; **Always Incremental** backup scheme for file-based backups; role-based ACLs; encrypted communication and backup encryption; Bareos WebUI for administration and restore; **virtualization plugins** for VMware vSphere, Hyper-V, and Proxmox; **bare-metal recovery** with Relax-and-Recover (Linux) and Barri (Windows); NDMP SAN backups; tape library and WORM media support . Bareos 25 adds Hyper-V Plugin, Proxmox Plugin, Bareos Recovery Imager for Windows, and Libcloud Plugin for S3-compatible object backup .

- **[Restic](https://github.com/restic/restic)**
  **Fast, efficient, secure open-source backup program.** **35.8k stars, actively maintained** . Features encryption, deduplication, snapshots, and multiple storage backends including local, SFTP, REST, and S3-compatible stores. **BSD-2-Clause license**. Widely adopted as the foundational backup engine for many higher-level tools. Foundation for **Zmanda Pro** .

- **[BorgBackup](https://github.com/borgbackup/borg)**
  **Deduplicating backup program with authenticated encryption and compression.** **13.7k stars, actively maintained** . Optimized for Unix-like systems. Stores only unique data blocks (no redundancy), making it highly space-efficient. Supports compression and authenticated encryption. **Reliable and fast in incremental mode**: after first full backup, subsequent backups copy only changes. Can operate in server mode (deploy Borg repository on NAS or remote server accessible via SSH). **Vorta** provides a GUI for Borg . **BSD-3-Clause license**.

- **[Kopia](https://github.com/kopia/kopia)**
  **Cross-platform backup tool with lock-free deduplication, encryption, snapshots, and pruning.** **5.7k stars, actively maintained** . Supports local disk, SFTP, and many cloud storage backends. **Apache-2.0 license**. Used by **Kanister** for Kubernetes data protection .

### Kubernetes Backup & Disaster Recovery

- **[Velero](https://github.com/vmware-tanzu/velero)**
  **The most mature open-source Kubernetes backup and disaster recovery tool.** Provides backup and restore of Kubernetes resources (Deployments, Services, ConfigMaps) and persistent volumes. **Persistent volume snapshots** accelerate restore. Supports **selective restores** (specific namespaces, resource groups, or individual objects) without restoring entire cluster. **Scheduled backups** for regular protection. Integrates with cloud storage buckets (AWS S3, GCP Storage, Azure Blob) and S3-compatible systems. Deployment via Helm chart, YAML manifests, or CLI . **Velero is the foundation for Kubernetes DR**, with **community support rated 5/5** in comparative evaluations . **Key limitation**: Plugin-based architecture, CRD version drift, and debugging complexity can make it finicky for critical production restores .

- **[Kanister](https://github.com/kanisterio/kanister)**
  **CNCF sandbox project for application-level data management on Kubernetes.** Originally created by the **Veeam Kasten team**. Provides cohesive APIs for defining and curating data operations. **Kubernetes-native**: APIs implemented as Custom Resource Definitions (CRDs). **Storage agnostic**: transfers backup data between services and object storage of your choice. **Pre-built blueprints** for AWS RDS, Cassandra, Couchbase, Elasticsearch, etcd, FoundationDB, MongoDB, MySQL, PostgreSQL, and Redis. **Secured via RBAC**, with observability through Prometheus, Grafana, and Loki. **Apache-2.0 license** .

- **[Stash by AppsCode](https://github.com/stashed/stash)**
  **Declarative, GitOps-native open-source alternative to Velero.** Leverages **Restic** for backups. Define backup strategy directly with CRDs alongside your application: specify what to back up (PVC, database), where to put it (Repository), and how often (BackupConfiguration). **Streamlined operational model** compared to Velero's plugin system for simple use cases. Efficient and encrypted backups. **Restore process is straightforward** .

- **[Kasten K10](https://www.kasten.io/)**
  **Enterprise-grade Kubernetes data protection (commercial, Veeam).** **Application-aware**, policy-driven automation, and multi-cluster disaster recovery. **Excellent technical support and UI**, but **commercial licensing** and **smaller community** than Velero . Best for enterprises with complex stateful applications and strict DR requirements .

### Cloud & Virtualization Backup

- **[Plakar](https://github.com/PlakarKorp/plakar)**
  **Open-source backup engine with zero-trust resilience architecture.** Supports **end-to-end encryption with native zero-knowledge encryption**—keys never leave the source. **Client-side deduplication and compression** achieve **90%+ lower storage and network costs** . **Petabyte-scale performance** with index-in-snapshot architecture (no central database bottleneck). **Vendor-neutral archive format** (PTAR & Kloset) ensures data remains readable 50+ years from now. **Plakar Control Plane** (free plan available) provides self-hosted backup management with web interface, inventories, integrations, policies, and scheduling . Available as pre-built binaries for macOS, FreeBSD, Alpine, Debian, Arch, RPM, Linux, OpenBSD, and Windows .

- **[Zmanda Pro](https://github.com/zmanda/zmanda)**
  **High-performance, open-source, restic-based backup and recovery solution for hybrid cloud environments** . **Key features**: centralized management with backup policies and schedules; flexible media options (disk, optical, Amazon S3, Wasabi, GCP, Azure); **wide platform support** (Linux, Windows, macOS; MS SQL, MongoDB, MySQL, Oracle; Hyper-V, VMware); **client-side deduplication** saving up to 89% storage; **forever incremental backups**; ransomware protection with air-gapped backups; **Microsoft 365 Backup** (Outlook, OneDrive for Business, SharePoint, Teams); **bare-metal recovery (BMR)**; continuous updates and 24x7 support .

- **[DaliBackup-OSS](https://github.com/daliranas/DaliBackup-OSS)**
  **Sovereign, lightweight backup and disaster recovery engine for Microsoft Hyper-V, Proxmox VE (QEMU & LXC), and IMAP Mailboxes.** **Zero external database dependencies** (embedded SQLite) . **Ultra-lightweight**: runs on Node.js 22 LTS with native embedded SQLite—no heavy MariaDB, Redis, or MinIO required. **Hyper-V Engine**: continuous streaming GZip compression, VSS application-consistent checkpoints, multi-disk capture, instant disaster recovery. **Proxmox VE Integration**: QEMU VM and LXC container backup via Proxmox REST API 2.0 and native vzdump hook. **Universal IMAP Email Sync**: incremental email synchronization with UID tracking and .tar.gz export. **Multi-protocol storage**: POSIX/NFS, SFTP (SSH key/password), FTP/FTPS. **Zero-Trust Security**: AES-256-GCM hardware encryption for secrets at rest and machine-bound agent tokens . **Docker deployment** with one-click run .

### SaaS & Email Backup

- **[Open Archiver](https://github.com/LogicLabs-OU/OpenArchiver)**
  **Secure, sovereign, open-source platform for email archiving.** Provides self-hosted solution for archiving, storing, indexing, and searching emails from **Google Workspace (Gmail), Microsoft 365, PST files, and generic IMAP inboxes** . **Key features**: universal ingestion (initial bulk imports + continuous real-time sync); secure storage in standard `.eml` format with **deduplication and compression**; **pluggable storage backends** (local filesystem, S3-compatible object storage); **full-text search** across emails and attachments (PDF, DOCX); **thread discovery**; **compliance & retention policies**; **file hash and encryption** for tamper-proof records; **immutable audit trail**. **Tech stack**: SvelteKit frontend, Node.js/Express backend, Meilisearch for search, PostgreSQL for metadata, Docker Compose deployment .

- **[Spanning Backup for Microsoft 365 API](https://github.com/SpanningCloudApps/SB365-Powershell)**
  PowerShell module for managing Spanning Backup for Microsoft 365. Spanning provides cloud-to-cloud data protection for Microsoft 365, Google Workspace, and Salesforce, protecting over **24,000 organizations and 2.5 million users** with automated daily backups, unlimited on-demand backups, infinite retention, and granular point-in-time restore . RESTful APIs for license management and data export .

### Additional Strong Open-Source Options

- **Enterprise Backup**: **Bareos** (AGPLv3, no open-core, hypervisor plugins, tape support) .
- **Backup Engines**: **Restic** (35.8k stars, S3/SFTP backends) , **BorgBackup** (13.7k stars, dedup, compression) , **Kopia** (5.7k stars, lock-free dedup) , **Plakar** (zero-knowledge, petabyte-scale) .
- **Kubernetes DR**: **Velero** (most mature, community 5/5) , **Kanister** (CNCF sandbox, application-aware blueprints) , **Stash** (GitOps-native, Restic-based) .
- **SaaS/Email**: **Open Archiver** (M365/Gmail/IMAP archiving, full-text search) .
- **Virtualization**: **DaliBackup-OSS** (Hyper-V, Proxmox, IMAP, Docker) .

**Frameworks for building custom systems**: Combine **Bareos** for cross-platform enterprise backup with hypervisor plugins and tape support, **Restic** or **Kopia** for efficient deduplicated backup to cloud storage, **Velero** for Kubernetes cluster and volume backup, **Kanister** for application-level database backups on Kubernetes, **Plakar** for zero-trust encrypted backup at petabyte scale, and **Open Archiver** for SaaS email archiving. Add **PostgreSQL** for metadata persistence and **Docker** for deployment.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Cloud backup and disaster recovery platforms handle sensitive organizational data; ensure compliance with data protection regulations and internal security policies.
- **Open-source reality**: The open-source ecosystem for backup and disaster recovery is **mature and production-ready** at the **backup engine** (**Restic**, **BorgBackup**, **Kopia**, **Plakar**), **enterprise backup** (**Bareos**), and **Kubernetes DR** (**Velero**, **Kanister**, **Stash**) layers. **DaliBackup-OSS** provides focused virtualization backup for Hyper-V and Proxmox . **Open Archiver** delivers sovereign email archiving for M365/Gmail/IMAP . However, **commercial platforms** (Veeam, Rubrik, Cohesity, Druva) provide **unified management consoles, application-aware recovery at scale, ransomware detection, and enterprise SLAs** that open-source alternatives require significant integration and engineering investment to match. The open-source path is most viable for organizations with strong infrastructure engineering capacity or for specific workloads (Kubernetes, VMs, email archiving).

---

**Made for infrastructure engineers, backup administrators, SREs, and data protection teams.**
Let's make cloud backup and disaster recovery more open, transparent, and resilient.
