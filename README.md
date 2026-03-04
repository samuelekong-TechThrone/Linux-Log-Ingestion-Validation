# Linux Log Ingestion Validation – Splunk Enterprise

[![Validation Status](https://img.shields.io/badge/Validation-PASS-brightgreen)](https://github.com/)

This repository documents the **end-to-end validation of a Linux log ingestion pipeline** in a controlled lab environment prior to production onboarding. It demonstrates secure log forwarding, index segregation, host attribution, timestamp integrity, and searchability within Splunk Enterprise.

---

## Overview

The objective of this project is to ensure that Linux system logs:

- Are securely forwarded to Splunk Enterprise
- Land in the designated custom index (`techthrone_ubuntu`)
- Retain accurate timestamps
- Correctly attribute the originating host
- Are fully searchable for detection and incident response use cases

This repository provides both **high-level documentation** and detailed **technical validation evidence**.

---



