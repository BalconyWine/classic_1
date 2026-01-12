# 2 - APS DAI - Support Request Framework

**Owner:** APS Data & AI Team
**Scope:** PROD & NPR Environments

This page defines the standard operating procedure (SOP) for raising, tracking, and managing support requests and incidents for the **APS Data & AI** perimeter.

> **ℹ️ Zero-Friction Support**
> Selecting the correct portal and providing mandatory metadata (Environment, Squad, Priority) is critical to ensure your ticket is routed to the correct backlog and processed within SLA.

---

## 1. Decision Matrix: Select the Right Portal
Use the matrix below to determine the appropriate channel based on the nature of your request.

| Request Classification | Definition | Target Portal | Scope |
| :--- | :--- | :--- | :--- |
| **Incident** | Unplanned interruption or quality degradation of an IT service. | **ServiceNow** | All Environments (PROD / NPR) |
| **Request** | Standard service fulfillment (e.g., Access, Resources). | **ServiceNow** | All Environments |
| **Change** | Modification to production infrastructure or deployment. | **ServiceNow** | **PRODUCTION Only** |
| **Problem** | Root cause analysis (RCA) for recurring incidents. | **ServiceNow** | All Environments |
| **Project / IT Dev** | Development tasks, User Stories, or NPR-specific configurations. | **Jira** | NPR / Project Mode |

---

## 2. Jira Workflow (Project & NPR Support)
**Context:** This workflow applies to all development tasks, feature requests, and NPR-specific needs.

**⚠️ Prerequisite:** Access to the specific Jira project is required. If you lack access, please contact **Anh Vinh** or **Oussama**.

### 2.1 Ticket Configuration
To ensure proper backlog prioritization, please strictly adhere to the following schema:

* **Issue Type:** Must be set to **"Story"**.
* **Mandatory Fields:**
    * **Component:** Select your specific **Squad**.
    * **Priority:** Select based on the SLA definitions below.
    * **Description:** Provide a technical description of the need or user story.

> *[Placeholder for Screenshot: Jira 'Create Issue' modal highlighting "Story" type and "Component" field]*

### 2.2 Service Level Agreements (SLA)
*Note: Initial priority assignment serves as a signal; the Technical Team reserves the right to re-prioritize based on capacity and impact analysis.*

| Priority Level | Resolution SLA |
| :--- | :--- |
| **Very High** (Très haute) | 2 Days |
| **High** (Haute) | 5 Days |
| **Medium** (Moyenne) | 1 Week |
| **Low** (Basse) | 2 Weeks |
| **Very Low** (Très basse) | 3 Weeks |

### 2.3 Lifecycle Management
The ticket will transition through the following states.
**⛔ Do Not Assign:** Please do not assign tickets to a specific individual. The APS team operates on a pull-model from the backlog.

1.  **BACKLOG:** Request registered; pending prioritization.
2.  **READY:** Acknowledged; queued for next sprint/cycle.
3.  **IN PROGRESS:** Currently under development/resolution.
4.  **DONE:** Deployment or task completed.

---

## 3. ServiceNow Routing Cheat Sheet
For standard ITIL processes, accurate routing is essential. Please use the exact **Assignment Groups** or **Categories** listed below to prevent routing delays.

| Ticket Type | Field to Configure | Value / Group Code |
| :--- | :--- | :--- |
| **Incident** (All Envs) | Category | `BNPP_CARDIF_FR_APS_DATA_AI_INCIDENT` |
| **Request** (Standard) | Assignment Group | `BNPP_CARDIF_FR_APS_DATA_AI_REQ` |
| **Change** (Production) | Assignment Group | `BNPP_CARDIF_FR_APS_DATA_AI_CHANGE` |
| **Problem** (RCA) | Assignment Group | `BNPP_CARDIF_FR_APS_DATA_AI_PROBLEM` |

> **Note:** For Incidents, please specify the **Environment** (PROD/NPR) and provide a clear description of the error.
