## Wiz Scanning Exemption Request

### 📋 Request Summary
- **Target Repository Name:** `owner/repository-name`
- **Requestor / Primary Owner:** `@github-username`
- **Business Justification:** Provide a short explanation of why this repository needs to be excluded from Wiz scanning.

---

### 🛡️ Exemption Qualification Criteria
> **Mandatory Requirement:** You must fulfill at least **TWO (2)** of the following four criteria. Check the boxes that apply and provide brief context below each selection.

- [ ] **Criterion A: Environment Isolation**
  *The repository is strictly isolated to local testing, sandbox, or throwaway environments with zero production code, live customer data, or active deployment keys.*
  * **Details/Evidence:** 

- [ ] **Criterion B: Third-Party / Vendor Code**
  *The repository consists entirely of third-party, open-source, or vendor-managed code that is scanned and maintained upstream.*
  * **Details/Evidence:** 

- [ ] **Criterion C: Air-Gapped / Alternative Scanner Coverage**
  *The repository is deployed in an air-gapped environment inaccessible to Wiz, and is monitored by an alternate internal scanner (e.g., Trivy, SonarQube).*
  * **Details/Evidence:** 

- [ ] **Criterion D: Archived / Read-Only**
  *The repository is officially archived or set to read-only state with zero active maintenance, commits, or automated deployment pipelines.*
  * **Details/Evidence:** 

---

### 📝 Checklist for Requestor
- [ ] I have edited `exclusions.yml` following the required YAML structure.
- [ ] I have fulfilled at least **2 criteria** above with necessary justification.
- [ ] I understand that if approved, this repository will be removed from Wiz vulnerability/inventory monitoring.

---

### 🔒 Security Team Approval Section (For Security Reviewers Only)
- [ ] Verified criteria fulfillment (at least 2/4 valid).
- [ ] Justification meets internal risk tolerance thresholds.
- [ ] Approved for Wiz exclusion.

**Reviewed by:** `@security-reviewer`