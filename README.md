# 🛠️ EC2 Cloud Governance Auditor

A specialized automation tool designed to help support engineers monitor, audit, and optimize EC2 resource usage across multiple AWS regions.

The EC2 Cloud Governance Auditor provides real-time visibility into instance lifecycles, ensuring that temporary lab environments are cleaned up and cloud costs remain within budget.

## 🎯 Project Goals

The goal of this project is to build a shared governance platform for support engineers that:

* **Provides automated monitoring** for EC2 instances across the APAC theatre.
* **Enforces resource accountability** by identifying instances missing critical `OwnerContact` tags.
* **Reduces unnecessary cloud spend** by alerting engineers to resources exceeding a 5-day lifespan.
* **Centralizes communication** by integrating alerts directly into team Slack channels.
* **Encourages FinOps best practices** and cloud cost awareness.

## 🏗️ Architecture Overview

The EC2 Cloud Governance Auditor consists of three primary components:

### 1. Multi-Region Scanner
A bash-based engine that utilizes the AWS CLI to query instances across Sydney, Singapore, Tokyo, and Osaka simultaneously.

### 2. Logic & Mapping Engine
A processing layer that calculates instance age, filters for active states, and maps technical user IDs to friendly names.

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
  * Scaling the current ANZ-focused scan to cover the entire **APAC theatre**, ensuring 100% visibility of our engineering footprint.
* **Self-Healing Capabilities**
  * Adding optional logic to automatically stop (not terminate) untagged or expired resources after a 24-hour warning period.

---

### 📝 Technical Requirements
* **AWS CLI v2** (Configured with `EC2:Describe` permissions)
* **jq** (Command-line JSON processor)
* **Slack Webhook URL** (Configured for the `#alert-ranchersupport-cloudops` channel)# ec2-cloud-auditor
