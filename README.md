# VeeamScripts

> PowerShell tools for troubleshooting and operating **Veeam Backup for Microsoft 365** and **Veeam Data Cloud** — built in the field, during real support cases.

![PowerShell](https://img.shields.io/badge/powershell-5.1%2B-blue)
![Veeam M365](https://img.shields.io/badge/Veeam%20M365-v8.x-green)
![License: MIT](https://img.shields.io/badge/license-MIT-yellow)

---

## Why this repo exists

Day-to-day Veeam M365 operations and support hit the same friction points: one-liners that fail on partial matches, irreversible destructive commands with no safety net, and performance investigations that require manual PostgreSQL legwork.

These scripts wrap those rough edges into guided, auditable workflows. They are shared **as-is** — they worked in production support scenarios and may help others in similar environments.

> ⚠️ These tools are **not officially supported or maintained by Veeam**. Test against a non-production environment first. Destructive operations on backup data are **irreversible**.

---

## Tools

| Script | Category | What it solves |
|---|---|---|
| [`Remove-VBOSiteData.ps1`](SharePoint/DeleteSites/) | SharePoint / OneDrive | Interactive, **safe** removal of a site's backed-up data from a VB365 repository — client-side search by title *and* URL, mandatory `-WhatIf` dry-run, typed confirmation, and an audit transcript. |
| [`SQLPerfCollector.ps1`](SQLPerformance/) | Performance / PostgreSQL | Enables `pg_stat_statements` and exports query performance metrics to CSV from the VB365 PostgreSQL backend — two-phase workflow (initialize, then collect after workload runs). |

---

## Quick start

```powershell
# Clone
git clone https://github.com/Silva-Sec/VeeamScripts.git
cd VeeamScripts

# Each tool has its own README with full usage details
```

**Requirements (varies per tool — see each folder's README):**

| Requirement | Detail |
|---|---|
| PowerShell | 5.1+ (Windows) |
| VB365 module | `Veeam.Archiver.PowerShell` (ships with VB365, tested on v8.x) |
| Permissions | Account with access to the VB365 server / repository management |
| PostgreSQL tools | For SQLPerfCollector: local `psql` with superuser access |

---

## Repository structure

```
VeeamScripts/
├── SharePoint/
│   └── DeleteSites/
│       ├── README.md                 # Full docs: why, usage, safety model
│       └── Remove-VBOSiteData.ps1    # Interactive site data removal
├── SQLPerformance/
│   ├── README.md                     # Full docs: pg_stat_statements workflow
│   └── SQLPerfCollector.ps1          # PostgreSQL performance collector
└── LICENSE                           # MIT
```

---

## Roadmap

- [ ] Mailbox / OneDrive variants of the interactive removal workflow
- [ ] Job health & session report collector
- [ ] Repository capacity trending export

More scripts from my local toolkit get published here as they're cleaned up and documented. Requests and case reports are welcome via [Issues](../../issues).

---

## Author

**Jonathan Silva** — Security Researcher & Infrastructure Specialist, 17+ years in IT (Microsoft, Verizon, Reuters, Acronis, Veeam).

- 🌐 [silvasec.com](https://silvasec.com)
- ✍️ [silvasec.seg.br](https://www.silvasec.seg.br) — write-ups and articles
- 🐦 [@SilvaSec](https://x.com/SilvaSec)

## License

[MIT](LICENSE) © 2026 Jonathan Silva
