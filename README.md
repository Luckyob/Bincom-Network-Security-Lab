# 🛡️ Network Security Fundamentals

## 📌 Project Overview

This project was completed as part of a cybersecurity onboarding practical focused on network security fundamentals. The exercise involved network reconnaissance, service enumeration, packet capture and traffic analysis, host-based firewall configuration, and post-hardening verification.

The practical environment consisted of **Kali Linux** as the testing workstation and **Ubuntu Server 24.04.5 LTS** hosted on **Microsoft Azure** as the target system. Docker-based lab deployment is also being incorporated into the project.

## 🎯 Objectives

- Perform network reconnaissance and TCP port scanning.
- Identify exposed services and their versions.
- Conduct service enumeration and OS fingerprinting.
- Capture and analyse network traffic using tcpdump and Wireshark.
- Examine TCP connection establishment and SSH communication.
- Configure UFW firewall rules to restrict inbound network traffic.
- Perform post-hardening scans to evaluate network exposure.
- Document findings and provide evidence of practical activities.

## 🧪 Lab Environment

| Component | Description |
|---|---|
| 💻 Testing workstation | Kali Linux |
| 🎯 Target system | Ubuntu Server 24.04.5 LTS |
| ☁️ Infrastructure | Microsoft Azure Virtual Machine |
| 🗺️ Network scanner | Nmap |
| 📦 Packet capture | tcpdump |
| 🦈 Traffic analysis | Wireshark |
| 🧱 Firewall | UFW |
| 🐳 Container platform | Docker |

## ⚙️ Activities Performed

### 1. 🔍 Network Reconnaissance and Service Enumeration

Nmap was used to conduct TCP port scanning, service version detection, OS fingerprinting, and detailed enumeration.

**📝 Activities included:**

- Host discovery and connectivity testing
- TCP SYN scanning
- Full TCP port scanning
- Service and version detection
- OS fingerprinting
- Detailed enumeration

**🔑 Key findings:**

| Port | Service | Notes |
|---|---|---|
| 22/tcp | 🔐 SSH | OpenSSH 9.6p1 running on Ubuntu |
| 587/tcp | 📧 Submission | Open, identified as `tcpwrapped`; service could not be fully identified |

- OS fingerprinting produced limited results because of network filtering and scan conditions.

### 2. 📡 Packet Capture and Traffic Analysis

Network traffic was captured using tcpdump and analysed using Wireshark.

**Activities included:**

- Capturing TCP traffic associated with SSH
- Examining TCP connection establishment
- Analysing SSH protocol negotiation
- Identifying SSH key exchange activity
- Observing encrypted traffic following key exchange
- Examining TCP acknowledgements and connection termination

**👀 Key observations:**

- The TCP three-way handshake was observed.
- SSH client and server banners were identified.
- SSH key exchange packets were observed.
- Application traffic was encrypted following SSH negotiation.

### 3. 🔥 Host-Based Firewall Hardening

UFW was configured on the Ubuntu target to implement basic host-based firewall controls.

**🛠️ Configuration:**

- Default incoming traffic policy: **Deny** 🚫
- Default outgoing traffic policy: **Allow** ✅
- SSH access: **Allowed** 🔐
- HTTP access: **Allowed** 🌍

**💻 Commands used:**

```bash
sudo ufw allow OpenSSH
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
```

Firewall status was subsequently checked to confirm that UFW was active.

### 4. ✅ Post-Hardening Validation

Nmap scans were conducted after firewall configuration to examine externally visible ports.

**📊 Validation included:**

- Scanning selected TCP ports
- Scanning the first 1,000 TCP ports
- Comparing externally observed port states
- Confirming continued SSH accessibility

Port 22 and port 587 remained externally detectable as open during validation. Port 80 was observed as filtered during an earlier scan.

> 💡 **Note:** Further investigation would be required to determine the interaction between UFW, Azure Network Security Groups, Docker networking, and externally observed port states.

### 5. 🐳 Docker-Based Lab

A Docker-based testing environment is being incorporated to demonstrate container deployment and network service exposure.

**🚀 Planned activities:**

- [ ] Deploy a containerised service
- [ ] Inspect running containers
- [ ] Identify exposed container ports
- [ ] Perform Nmap scans against the Docker host
- [ ] Analyse container-related network traffic
- [ ] Evaluate network isolation and firewall behaviour

## 🧰 Tools Used

- 🐉 Kali Linux
- 🐧 Ubuntu Server
- 🗺️ Nmap
- 📦 tcpdump
- 🦈 Wireshark
- 🧱 UFW
- 🐳 Docker
- ☁️ Microsoft Azure

## 📁 Repository Structure

```text
bincom-network-security-fundamentals/
├── README.md
├── Network_Security_Onboarding_Report.pdf
└── evidence/
    ├── Nmap scan outputs
    ├── Packet capture files
    ├── Firewall configuration evidence
    └── Screenshots
```
