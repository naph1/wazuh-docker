# 🛡️ Enterprise Threat Detection Lab: 30DaysOfSOC (Wazuh SIEM & XDR)

An enterprise-grade Security Information and Event Management (SIEM) and Extended Detection and Response (XDR) lab deployed, configured, and hardened over an intensive 30-day security engineering challenge. Powered by **Wazuh** and **Docker**.

---

## 🏗️ Architecture & Deployment
This lab simulates a multi-tier SOC monitoring environment utilizing containerized architecture:
* **Wazuh Server / Manager**: Handles log collection, agent communication, threat analysis, and rule evaluation.
* **Wazuh Indexer**: A secure OpenSearch cluster managing log indexing and data retention.
* **Wazuh Dashboard**: The unified web UI for security analytics, threat hunting, and compliance monitoring.
* **Endpoints**: Monitored virtual machines and host nodes reporting telemetry via Wazuh agents.

---

## 🛠️ Technical Implementation & Hardening
* **Container Orchestration**: Deployed and managed via Docker Compose (`docker-compose.yml`), resolving permission boundaries and volume mounts for production-like stability.
* **SSL/TLS Security**: Enforced secure communication clusters across indexer nodes using generated administrator certificates (`certs.yml`).
* **File Integrity Monitoring (FIM)**: Configured real-time monitoring on critical system binaries and configuration directories to flag unauthorized modifications.
* **Custom Detection Engineering**: Created tailored XML detection rules and decoders (`local_rules.xml`) to catch targeted simulated attacks.

---

## 📊 Security Use Cases & Attack Simulations Tested
| Attack / Scenario | Telemetry Source | Wazuh Module Triggered | MITRE ATT&CK Mapping |
| :--- | :--- | :--- | :--- |
| **Brute-Force Attack** | Authentication Logs | Log Analysis & Active Response | T1110 (Brute Force) |
| **System Binary Modification** | OS Filesystem | File Integrity Monitoring (FIM) | T1565 (Data Manipulation) |
| **Privilege Escalation** | Sudo / Process Logs | Security Event Monitoring | T1078 (Valid Accounts) |
| **Malicious Process Execution** | Endpoint Telemetry | Sysmon / Process Monitoring | T1204 (User Execution) |

---

## 📂 Repository Structure
```text
wazuh-docker/
├── single-node/       # Single-node production deployment configs & docker-compose
├── multi-node/        # Scalable multi-node cluster architecture configs
├── custom-rules/      # Custom XML detection rules and decoders
└── screenshots/       # Visual evidence of dashboard alerts and threat hunting