# Wiz Scanning Scope Management Architecture

## Overview
This repository manages the scanning scope for the Wiz GitHub App integration at the organization level. It provides an automated, security-governed mechanism to exclude specific repositories from Wiz scanning and inventory ingestion without requiring manual UI configuration in GitHub or Wiz.

---

## Workflow Diagram

```text
  [ Developer ]
       │
       ▼
1. Creates Branch & Edits `exclusions.yml`
2. Opens Pull Request against `main`
       │
       ├──► [ PR Checklist Validation ] (Enforces 2/4 Security Criteria)
       │
       ▼
3. [ CODEOWNERS Verification ]
       │  (Only @your-org/security-team can approve)
       │
       ├───► REJECTED ──► PR Closed ──► Repo stays in Wiz Scan Scope
       │
       ▼
4. APPROVED & MERGED to `main`
       │
       ▼
5. [ GitHub Action Triggered ] (push to main on exclusions.yml / daily cron)
       │
       ▼
6. [ GitHub REST API Sync ] ──► Updates Wiz App Scope (Excludes requested repos)