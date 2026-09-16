# 🛡️ Microsoft Sentinel SOC Lab

A hands-on **Security Operations Center (SOC) lab** built using **Microsoft Sentinel** in a Windows environment to practice SIEM-based security monitoring, log analysis, detection engineering, alert investigation, and MITRE ATT&CK mapping.

---

## 📌 Project Overview

This project focuses on using **Microsoft Sentinel as a cloud-native SIEM** to collect, query, monitor, and investigate Windows security events.

The lab was designed to simulate practical SOC activities such as:

* Security event monitoring
* Failed authentication analysis
* Process creation analysis
* KQL-based investigation
* Scheduled analytics rules
* Alert and incident investigation
* Security event correlation
* MITRE ATT&CK mapping
* Security monitoring visualization through workbooks

The project was developed as a hands-on learning environment to understand how security telemetry can be transformed into actionable detections and investigations.

---

## 🎯 Objectives

The primary objectives of this lab were to:

* Understand the workflow of Microsoft Sentinel as a SIEM.
* Collect and analyze Windows security telemetry.
* Use **Kusto Query Language (KQL)** for security investigations.
* Create and test scheduled analytics rules.
* Investigate Windows authentication events.
* Analyze process creation activity.
* Understand the relationship between events, alerts, and incidents.
* Build security-monitoring visualizations using Sentinel workbooks.
* Map observed activities to the **MITRE ATT&CK framework**.

---

## 🖥️ Lab Environment

| Component        | Details                      |
| ---------------- | ---------------------------- |
| SIEM             | Microsoft Sentinel           |
| Operating System | Windows                      |
| Cloud Platform   | Microsoft Azure              |
| Query Language   | Kusto Query Language (KQL)   |
| Telemetry        | Windows Security Events      |
| Key Event IDs    | 4625, 4688                   |
| Detection        | Scheduled Analytics Rules    |
| Visualization    | Microsoft Sentinel Workbooks |
| Framework        | MITRE ATT&CK                 |

---

## 🏗️ Lab Architecture

```text
┌──────────────────────────┐
│     Windows Endpoint     │
│                          │
│ Windows Security Events  │
│ Process Activity         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│     Data Collection      │
│      / Connector         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   Log Analytics          │
│      Workspace           │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   Microsoft Sentinel     │
│                          │
│  KQL Queries             │
│  Analytics Rules         │
│  Incidents               │
│  Workbooks               │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│     SOC Investigation    │
│                          │
│ Triage → Analysis →      │
│ Findings → Documentation │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    MITRE ATT&CK Mapping  │
└──────────────────────────┘
```

Detailed architecture:

**[Architecture Diagram](architecture/sentinel-lab-architecture.png)**

---

# 🔎 Security Monitoring & Detection

The lab focused on Windows security telemetry and practical detection scenarios.

## 1. Failed Authentication Monitoring

Windows **Event ID 4625** was analyzed to investigate failed authentication attempts.

The investigation focused on:

* Failed authentication events
* Account involved
* Timestamp
* Computer/host
* Logon type
* Source information where available
* Repeated authentication failures

KQL was used to filter and analyze the events.

📄 [Failed Logon Detection](analytics-rules/failed-logon-rule.md)

📄 [Failed Logon Investigation](investigations/failed-logon-investigation.md)

---

## 2. Process Creation Monitoring

Windows **Event ID 4688** was analyzed to understand process creation activity.

The investigation focused on:

* Process name
* Command line information where available
* Account
* Host
* Timestamp
* Process-related activity

The collected telemetry was queried using KQL to understand process execution within the monitored environment.

📄 [Process Monitoring](analytics-rules/process-monitoring-rule.md)

📄 [Process Investigation](investigations/process-investigation.md)

---

# 📊 KQL Investigation

Kusto Query Language was used to search, filter, and analyze security telemetry.

The repository contains separate KQL queries for different investigation scenarios.

### Failed Logons

```text
kql/failed-logons.kql
```

Used to investigate Windows Event ID 4625 and identify patterns in failed authentication activity.

### Process Events

```text
kql/process-events.kql
```

Used to investigate Windows process creation events, including Event ID 4688.

### Event Analysis

```text
kql/event-analysis.kql
```

Contains additional queries used for filtering, analyzing, and understanding security-event trends.

---

# ⚙️ Scheduled Analytics Rules

Scheduled analytics rules were created and tested to demonstrate automated security detection.

The general workflow was:

```text
Security Telemetry
       ↓
KQL Detection Query
       ↓
Scheduled Analytics Rule
       ↓
Condition Evaluated
       ↓
Alert / Incident
       ↓
SOC Investigation
```

The rules were designed around security events observed during the lab.

📄 [Failed Logon Rule](analytics-rules/failed-logon-rule.md)

📄 [Process Monitoring Rule](analytics-rules/process-monitoring-rule.md)

---

# 🚨 Incident Investigation

The investigation process followed a basic SOC workflow:

```text
Alert / Event
      ↓
Initial Triage
      ↓
Validate Activity
      ↓
Collect Supporting Evidence
      ↓
Analyze Timeline
      ↓
Determine Finding
      ↓
MITRE ATT&CK Mapping
      ↓
Document Investigation
```

The purpose was to understand how a SOC analyst moves from an individual security event toward a documented investigation.

---

# 📈 Microsoft Sentinel Workbooks

Sentinel workbooks were explored for security monitoring and visualization.

The workbook concepts included:

* Incidents by severity
* Failed logons over time
* Top affected users
* Security event trends
* MITRE ATT&CK-related visibility

📄 [Workbook Documentation](workbooks/workbook-documentation.md)

---

# 🧪 Investigation Scenarios

The project included investigation of Windows security telemetry generated during controlled testing.

### Failed Authentication

**Event ID:** 4625

Purpose:

> Analyze failed authentication activity and understand the associated account, host, timestamp, and logon information.

### Process Creation

**Event ID:** 4688

Purpose:

> Analyze process creation activity and investigate executable and command-line information where available.

The observations from the lab were documented rather than treating every generated event as malicious.

---

# 🧩 MITRE ATT&CK Mapping

Observed security activity was mapped to the **MITRE ATT&CK framework** where the available evidence supported a technique mapping.

The mapping process followed:

```text
Observed Activity
       ↓
Security Event
       ↓
Detection / Investigation
       ↓
Behavior Analysis
       ↓
MITRE ATT&CK Technique
       ↓
ATT&CK Tactic
```

📄 [MITRE ATT&CK Mapping](mitre-mapping/attack-mapping.md)

---

# 📸 Project Evidence

Screenshots from the actual lab environment are provided in the `screenshots/` directory.

### Sentinel Incidents

![Sentinel Incidents](screenshots/incidents.png)

### Analytics Rule

![Analytics Rule](screenshots/analytics-rule.png)

### Sentinel Workbook

![Sentinel Workbook](screenshots/workbook.png)

---

# 📁 Repository Structure

```text
microsoft-sentinel-soc-lab/
│
├── README.md
│
├── architecture/
│   └── sentinel-lab-architecture.png
│
├── analytics-rules/
│   ├── failed-logon-rule.md
│   └── process-monitoring-rule.md
│
├── kql/
│   ├── failed-logons.kql
│   ├── process-events.kql
│   └── event-analysis.kql
│
├── investigations/
│   ├── failed-logon-investigation.md
│   └── process-investigation.md
│
├── workbooks/
│   └── workbook-documentation.md
│
├── screenshots/
│   ├── incidents.png
│   ├── analytics-rule.png
│   └── workbook.png
│
└── mitre-mapping/
    └── attack-mapping.md
```

---

# 🧠 Skills Demonstrated

### Security Operations

* SIEM Monitoring
* Alert Triage
* Security Event Analysis
* Log Analysis
* Incident Investigation
* Event Correlation
* Threat Detection

### Microsoft Sentinel

* Sentinel configuration
* Windows security monitoring
* Scheduled Analytics Rules
* Incident investigation
* Workbooks
* KQL

### Windows Security

* Windows Security Events
* Event ID 4625
* Event ID 4688
* Authentication monitoring
* Process creation analysis

### Framework

* MITRE ATT&CK
* Security investigation methodology

---

# 📚 Key Learning Outcomes

Through this lab, I developed practical understanding of:

* How SIEM platforms collect and analyze security telemetry.
* How Windows security events can be investigated using KQL.
* How detection logic can be converted into scheduled analytics rules.
* How alerts and incidents can support SOC investigations.
* How security activity can be mapped to MITRE ATT&CK.
* How dashboards and workbooks can support security monitoring.
* How to document security investigations and findings.

---

# ⚠️ Lab Disclaimer

This repository documents activities performed in a controlled learning environment for cybersecurity education and SOC skill development.

All testing was performed against systems and data within the authorized lab environment.

---

## 👤 Author

**Adorn Cyriac Mathew**

Cybersecurity Researcher | Aspiring SOC Analyst

**Focus:** Security Operations • SIEM • Threat Detection • Incident Investigation • Blue Teaming
