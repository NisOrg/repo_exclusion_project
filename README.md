# GitOps Repository Excluder for GitHub App (Wiz Scanner)

An enterprise-ready, automated GitOps utility that enables security teams to enforce repository exclusions for the Wiz GitHub App—even when the underlying application does not natively support repository exclusion filters.

---

## 📌 Architecture Overview

To scale securely across large enterprise environments (supporting 3,000+ repositories) without manual overhead, this utility uses a **selective scope sync model**.


### ⚙️ How It Works:
1. **The Core Block:** When an App is set to "All repositories", GitHub restricts programmatic changes to its scope. This pipeline transitions the app's scope to **"Only select repositories"** using a one-time setup.
2. **The Sync Pipeline (`sync.py`):**
   * Automatically queries all repositories across the organization (handling pagination natively).
   * Parses the security team's `exclusions.yml` file.
   * Compares the active organization repos with the exclusions list.
   * Programmatically adjusts the Wiz application's scope—adding newly discovered repos and removing excluded ones using the working `/user/installations` REST API.

---

## 🛠️ One-Time Setup (Onboarding)

To unlock the automated API scope modification, a GitHub Organization Admin must perform a one-time manual switch in the UI:

1. Navigate to your GitHub Organization Settings:  
   `https://github.com/organizations/<YOUR_ORG>/settings/installations`
2. Click **Configure** next to the **Wiz** application.
3. Scroll down to **Repository access** and change the selection from **All repositories** to **Only select repositories**.
4. Search for and select **exactly one** repository (e.g., your administrative workflow repository where this script runs) to allow GitHub to save the configuration.
5. Click **Save**.

*The Wiz GitHub App is now permanently configured for selective access. The automated sync pipeline will immediately populate the other allowed repositories on its next run.*

---

## 📝 Managing Exclusions

Exclusions are managed declaratively inside the `exclusions.yml` file in the root of this repository.

### `exclusions.yml` Format:

```yaml
requested_by: "platform-request-user"
approved_by: "security-reviewer"

excluded_repositories:
  - name: "sandbox-sandbox-testing"
    reason: "Local sandbox testing, no production data present"
    approved_by: "security-reviewer-ldap"

  - name: "development-temporary-test"
    reason: "Temporary playground repository"
    approved_by: "security-reviewer-ldap"
