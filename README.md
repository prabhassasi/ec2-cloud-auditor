# 🛠️ Cloud Governance Auditor

A specialized automation tool designed to monitor, audit, and optimise resource usage across multiple cloud platforms.

The Cloud Governance Auditor provides real-time visibility into instance lifecycles, ensuring that temporary lab environments are cleaned up and cloud costs remain within budget.

## 🚀 Strategic Objectives

The goal of this project is to build a governance platform that:

* **Provides automated monitoring** of resources across all the regions.
* **Enforces resource accountability** by identifying instances missing critical `OwnerContact` tags.
* **Reduces unnecessary cloud spend** by triggering alerts for resources exceeding a 5-day lifespan.
* **Centralises communication** by integrating alerts directly into team Slack channels.
* **Encourages FinOps best practices** and cloud cost awareness.

## ⚙️ Core System Framework

The Cloud Governance Auditor consists of three primary components, which initially focus on the AWS platform

### 1. Multi-Region Scanner
A bash-based engine that utilises the AWS CLI to query instances across all the regions simultaneously.

### 2. Logic & Mapping Engine
A processing layer that calculates instance age, filters for active states, and accurately maps instances to the correct User IDs for precise accountability.

### 3. Slack Integration Layer
A notification service that formats technical data into actionable Markdown alerts and delivers them via secure Webhooks.

## 🗺️ Future Roadmap

The project is currently in its initial monitoring phase. Future development will focus on expanding geographic reach and adding interactive governance features:

* **Multi-Cloud Expansion**
  * Extending support to **Azure** and **DigitalOcean** environments to provide a "Single Pane of Glass" view across all cloud providers.
* **Deviation & Approval Workflow**
  * Implementing a manager-approved "Exception" process for long-term reproduction labs.
  * Approved instances will receive an `ExpiryDate` tag to temporarily silence automated alerts.
* **Expanded Region Coverage**
  * Scaling the scan to cover the entire **region**, ensuring 100% visibility of our engineering footprint.
* **Self-Healing Capabilities**
  * Adding optional logic to automatically stop (not terminate) untagged or expired resources after a 24-hour warning period.

---
