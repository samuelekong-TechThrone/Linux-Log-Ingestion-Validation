# Screenshots & Architecture Diagrams

This document provides visual evidence for the **Linux log ingestion validation** in Splunk Enterprise. It includes the lab environment setup, test logs, and architecture diagram.

---

## 1. Architecture Diagram

![Architecture Diagram](screenshots/architecture_diagram.png)  
*Figure 1: End-to-end architecture of Linux log forwarding to Splunk Enterprise.*  

---

## 2. Test Log Validation

![Test Log in Splunk](screenshots/test_log_screenshot.png)  
*Figure 2: Test log ("THIS IS JUST A TEST LOG") successfully ingested and searchable in Splunk.*  
**Notes:**  
- Event stored in **custom index `techthrone_ubuntu`**  
- Host correctly attributed to the monitored Linux system  
- Timestamp matches the original system log  
- Event fully searchable using **index, host, keyword, and time filters**

---

## 3. Custom Index

![Custom Index](screenshots/Custom_index.png)  
*Figure 3: Custom index (`techthrone_ubuntu`) created and writable in Splunk Enterprise.*  

---

## 4. Forwarder Configuration
  
![Forwarder Config 2](screenshots/Forwarder_config_2.png)  
*Figure 4: Splunk Universal Forwarder configuration.*  

---

## 5. Forwarder Installation

![Forwarder Installation](screenshots/forwarder_installation.png)  
*Figure 5: Configuration of Splunk Universal Forwarder on the Linux endpoint.*  

---

## 6. Splunk Indexer Setup

![Indexer Setup](screenshots/indexer_setup.png)  
*Figure 6: Splunk Enterprise Indexer setup to access GUI.*  
