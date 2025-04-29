SailPoint IdentityIQ Customization Repository
Overview
This repository contains customizations, configurations, and utilities for SailPoint IdentityIQ (IIQ) — an enterprise Identity Governance and Administration (IGA) platform.

The contents of this repository help organizations extend and tailor IdentityIQ to better meet business needs such as onboarding, access certification, policy enforcement, and compliance reporting.

Even if you are not a SailPoint expert, this README will help you understand how the pieces fit together!

Repository Structure

Folder	Description
/rules	SailPoint Rules written in BeanShell Java, used for advanced processing (ex: connector rules, provisioning rules, certification rules).
/workflows	Workflow XML files that automate multi-step processes (ex: Joiner workflows, Termination processes).
/buildmaps	BuildMap rules and files used for translating database/application records into SailPoint schema objects.
/identitytriggers	Scripts that trigger during Identity refresh events, like detecting job title changes or disabling orphaned accounts.
/lifecycle-events	Configuration and code for automated Lifecycle Events (ex: Birthright provisioning, access removal).
/transformations	SailPoint Transformations that modify or map incoming data (ex: reformatting usernames, deriving display names).
/connectors	Custom connector extensions or configurations (ex: JDBC Connector customization, REST API Connector modifications).
/ui-customizations	Changes or additions to the SailPoint UI (user interface) — including forms, custom pages, and branding.
/reports	Custom Reports definitions for governance, compliance, and operational insight.
/documentation	Supplemental documentation explaining business logic, design choices, and implementation steps.
/scripts	Automation scripts (like PowerShell, Python) used for integrating SailPoint with other systems (ex: Active Directory, ServiceNow).
Getting Started
Pre-requisites:

SailPoint IdentityIQ environment (Development, QA, or Production).

Admin access to IdentityIQ Console or debug pages.

Familiarity with basic Java, XML, and SailPoint Concepts (Identity, Application, Entitlement, Policy, Certification).

Clone the repository

bash
Copy
Edit
git clone https://github.com/your-org/sailpoint-identityiq-customizations.git
Set up a local environment (optional but recommended)

Install an XML editor (ex: Visual Studio Code + XML extensions).

Install a Java IDE if modifying Rules heavily (ex: IntelliJ IDEA, Eclipse).

Set up Postman if testing REST APIs.

Understand the code

Read /documentation/Overview.md (if available).

Review example workflows, rules, and forms to understand structure.

Deployment Strategy

Always deploy in Dev or QA first.

Use the SailPoint Import Utility (iiq console → import filename.xml) to bring in changes.

Validate changes in IdentityIQ Admin UI.

Promote to Production via standard Change Management practices.

Common Terms

Term	Meaning
Identity	A digital representation of a person or thing (user, contractor, bot).
Application	A system that SailPoint connects to (like Active Directory, SAP, Workday).
Entitlement	A specific permission within an application (ex: "Admin Role" in Salesforce).
Certification	A review process to confirm users still need their access.
Connector	The method SailPoint uses to talk to an application.
Rule	Small piece of custom Java code that adds logic (ex: determine Manager relationship).
Lifecycle Event	An automatic trigger for identity changes (ex: user promotion, departure).
How to Contribute
We welcome contributions!

To contribute:

Fork the repository

Create a new branch (feature/my-new-feature)

Commit your changes with clear messages

Open a Pull Request explaining what you changed and why

Please ensure:

Code is tested against your local Dev/QA environments.

Documentation is updated for any new workflows, rules, or connectors.

Example: How a Typical Workflow Customization Works
A new employee joins.

SailPoint detects the event from an authoritative source (like Workday).

A Joiner Workflow triggers:

Creates Active Directory account.

Assigns default entitlements.

Sends welcome email.

Rules or scripts ensure special access is provisioned based on department or title.

If anything fails, error handling rules or lifecycle events will retry or alert admins.

Helpful Resources
SailPoint Developer Portal

IdentityIQ Product Documentation

BeanShell Language Basics

Disclaimer
This repository contains custom code and configurations that are intended for educational or demonstration purposes. Always thoroughly test in non-production environments before moving to live systems.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Quick Visual: Typical Flow
plaintext
Copy
Edit
Source System (ex: Workday) 
    ↓
IdentityIQ (Import & Correlation) 
    ↓
Identity Creation / Update 
    ↓
Lifecycle Events, Rules, Workflows 
    ↓
Provisioning / Certification / Reporting
Would you also like me to generate a slightly shorter version for internal-only teams? (for example, if you're sharing it with just your SailPoint developers, it can be even crisper.)
Would you also like a sample /documentation/Overview.md template next? That'll make this even better!
