# Linux Log Ingestion Validation – Splunk Enterprise

[![Validation Status](https://img.shields.io/badge/Validation-PASS-brightgreen)](https://github.com/)

This document provides a detailed record of the **Linux log ingestion pipeline validation** in a controlled lab environment prior to production onboarding.

---

## 1. Objective

<details>
<summary>Click to expand</summary>

Validate that Linux logs from monitored endpoints:

- Are securely forwarded to Splunk Enterprise
- Land in the designated custom index (`techthrone_ubuntu`)
- Retain accurate timestamps
- Correctly attribute the originating host
- Remain searchable for detection and incident response use cases

</details>

---

## 2. Environment Overview

<details>
<summary>Click to expand</summary>

| Component | OS / Version | Role |
|-----------|-------------|------|
| Linux Endpoint | Ubuntu Desktop 24.04 | Monitored system |
| Splunk Universal Forwarder | 9.4 | Forward logs to indexer |
| Splunk Enterprise | 9.4, Kali Linux | Indexer / SIEM platform |
| Virtualization | Oracle VirtualBox | Hosts VM environment |

**Data Flow:**  
`Linux Endpoint → Universal Forwarder → TCP 9997 → Splunk Enterprise Indexer → Custom Index: techthrone_ubuntu`

</details>

---

## 3. Validation Approach

<details>
<summary>Click to expand</summary>

1. Generate a controlled test log:

```text
"THIS IS JUST A TEST LOG"

2. Trace end-to-end ingestion from the Linux Endpoint → Universal Forwarder → Splunk Indexer → Custom Index (`techthrone_ubuntu`).

3. Validate the following criteria:

- **Log Ingestion:** The test log appears in Splunk without delay.
- **Index Segregation:** Event is stored in the designated `techthrone_ubuntu` index only.
- **Host Attribution:** The `host` field correctly reflects the originating Linux system.
- **Timestamp Integrity:** `_time` and `_indextime` match the system timestamp.
- **Event Searchability:** Test log is searchable using index, host, keyword, and time filters.

## 4. Validation Results

<details>
<summary>Click to expand</summary>

| Validation Control        | Result |
|---------------------------|--------|
| Log Ingestion             | PASS   |
| Index Segregation         | PASS   |
| Host Attribution          | PASS   |
| Timestamp Integrity       | PASS   |
| Searchability             | PASS   |

**Observation:** No ingestion failures or parsing errors were detected. Residual risk is assessed as low.

</details>

## Recommendations

<details>
<summary>Click to expand</summary>

### Security Hardening
- Enable **SSL/TLS** for forwarder traffic  
- Restrict **TCP port 9997** to authorized IP addresses only  
- Enforce **strong authentication** between forwarder and indexer

### Operational Monitoring
- Implement **forwarder health monitoring**  
- Configure **ingestion monitoring alerts**  
- Establish alerts for **ingestion delays or anomalies**

### Time Governance
- Ensure **NTP synchronization** across all production endpoints  
- Periodically validate **timestamp consistency** between host and index

### Index Governance
- Document and approve **index retention policies**  
- Confirm alignment with **internal log management standards**

</details>

## Key Takeaways

<details>
<summary>Click to expand</summary>

- A SIEM is **not production-ready** until logs are validated for:  
  - Data integrity  
  - Host attribution  
  - Timestamp alignment  
  - Searchability

- Controlled lab validation **reduces operational risk** before production onboarding  
- Architecture diagrams and validation evidence provide a **reference for future deployments**

</details>

