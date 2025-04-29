# SailPoint IdentityIQ Customization Repository

## Overview

This repository contains customizations, configurations, and utilities for **SailPoint IdentityIQ (IIQ)** — an enterprise Identity Governance and Administration (IGA) platform.

The contents of this repository help organizations extend and tailor IdentityIQ to better meet business needs such as onboarding, access certification, policy enforcement, and compliance reporting.

Even if you are **not a SailPoint expert**, this README will help you understand how the pieces fit together!

## Repository Structure

| Folder | Description |
|:-------|:------------|
| `/rules` | SailPoint *Rules* written in BeanShell Java, used for advanced processing (ex: connector rules, provisioning rules, certification rules). |
| `/workflows` | Workflow XML files that automate multi-step processes (ex: Joiner workflows, Termination processes). |
| `/buildmaps` | BuildMap rules and files used for translating database/application records into SailPoint schema objects. |
| `/identitytriggers` | Scripts that trigger during Identity refresh events, like detecting job title changes or disabling orphaned accounts. |
| `/lifecycle-events` | Configuration and code for automated Lifecycle Events (ex: Birthright provisioning, access removal). |
| `/transformations` | SailPoint Transformations that modify or map incoming data (ex: reformatting usernames, deriving display names). |
| `/connectors` | Custom connector extensions or configurations (ex: JDBC Connector customization, REST API Connector modifications). |
| `/ui-customizations` | Changes or additions to the SailPoint UI — including forms, custom pages, and branding. |
| `/reports` | Custom Reports definitions for governance, compliance, and operational insight. |
| `/documentation` | Supplemental documentation explaining business logic, design choices, and implementation steps. |
| `/scripts` | Automation scripts (like PowerShell, Python) used for integrating SailPoint with other systems (ex: Active Directory, ServiceNow). |

## Getting Started

> **Pre-requisites:**
> - SailPoint IdentityIQ environment (Development, QA, or Production).
> - Admin access to **IdentityIQ Console** or **debug pages**.
> - Familiarity with **basic Java**, **XML**, and **SailPoint Concepts** (Identity, Application, Entitlement, Policy, Certification).

1. **Clone the repository**
    ```bash
    git clone https://github.com/your-org/sailpoint-identityiq-customizations.git
    ```

2. **Set up a local environment**
    - Install an XML editor (ex: Visual Studio Code + XML extensions).
    - Install a Java IDE if modifying Rules heavily.
    - Set up Postman if testing REST APIs.

3. **Understand the code**
    - Read `/documentation/Overview.md`.
    - Review example workflows, rules, and forms.

4. **Deployment Strategy**
    - Always deploy in **Dev** or **QA** first.
    - Use the SailPoint **Import Utility** (`iiq console` → `import filename.xml`).
    - Validate changes.
    - Promote to Production via Change Management.

## Common Terms

| Term | Meaning |
|:-----|:--------|
| **Identity** | A digital representation of a person or thing. |
| **Application** | A system that SailPoint connects to. |
| **Entitlement** | A specific permission within an application. |
| **Certification** | A review process to confirm users still need their access. |
| **Connector** | The method SailPoint uses to talk to an application. |
| **Rule** | Custom Java code for logic extensions. |
| **Lifecycle Event** | Triggered by identity changes. |

## How to Contribute

1. Fork the repository
2. Create a new branch (`feature/my-new-feature`)
3. Commit with clear messages
4. Open a Pull Request with explanation

## Example: Workflow Customization

1. A **new employee** joins.
2. SailPoint detects from Workday.
3. **Joiner Workflow** triggers:
    - Creates AD account.
    - Assigns entitlements.
    - Sends welcome email.
4. Rules ensure conditional logic.

> Failures handled by alerts or retries.

## Helpful Resources

- [SailPoint Developer Portal](https://developer.sailpoint.com/)
- [IdentityIQ Documentation](https://documentation.sailpoint.com/identityiq/)

## Disclaimer

This repository contains custom code and configurations. Always test in non-production environments.

## License

MIT License. See `LICENSE`.

## Quick Visual: Typical Flow

```plaintext
Source System → IdentityIQ → Identity → Workflows → Provisioning / Certification / Reporting
```
