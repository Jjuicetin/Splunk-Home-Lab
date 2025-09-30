https://www.linkedin.com/in/jaehyun-gil-417329302/
# Splunk-Home-Lab
Splunk home lab to understand how Splunk works, how to set forwarders up to send logs in real time, what SPL commands to use to extract data out of the logs, detecting brute force attacks and some of MITTRE ATT&amp;CK protocols.



### Overview

Designed and implemented a simulated Security Operations Center (SOC) environment to practice log ingestion and detection engineering using Splunk Enterprise. The lab replicates a small enterprise network with multiple endpoints and log sources. This lab was created for me to get exposure on industry software/tools and to highlight my competancy. 

### Objectives

- Gain hands-on experience with SIEM configuration and log analysis.
- Develop and test detection rules for common attack patterns.
- Practice incident investigation and reporting workflows.

### Environment Components:

- **Splunk Enterprise Server** – Ubuntu Server 22.04 10.0.0.40
- **Forwarder 1** – Ubuntu Server 22.04 (Syslog, Auth logs) 10.0.0.58
- **Forwarder 2** – Windows 10 Pro (Windows Event Logs, Sysmon)

### Data Flow:

1. Endpoints generate logs (Windows Event Logs, Syslog, authentication logs).
2. Splunk Universal Forwarders securely transmit logs to Splunk Enterprise over TCP/SSL.
3. Splunk indexes and stores logs for search, correlation, and visualization.

 ### Tools & Technologies
 
- Splunk Enterprise & Universal Forwarder
- Ubuntu Server 22.04, Windows 10 Pro
- MITRE ATT&CK Framework (simulate MITRE ATT&CK on Windows VM)
- Oracle VirtualBox
- Atomic Red Team
- Kali Linux Hydra (simulate brute force attacks using a list of passwords and specified user)
- PowerShell, Bash scripting

### Network Setup

All virtual machines are configured with **bridged adapters**, meaning they appear on the same local network as my physical host machine.  
This allows them to communicate with each other directly as if they were separate physical devices on my LAN.

**Host and VM IP Addresses**
- **Splunk Enterprise Server (Ubuntu 22.04):** 10.0.0.58
- **Linux Client (Ubuntu 22.04):** 10.0.0.40
- **Windows 10 Client:** 10.0.0.41
- **Host Machine (Windows 10):** 10.0.0.31

**Communication Flow**
1. The **Linux client** and **Windows client** forward their logs to the Splunk server.
   - Linux uses the **Universal Forwarder** to send `syslog` and `auth.log`.
   - Windows uses the **Universal Forwarder** to send Security, Application, System and Sysmon logs.
2. The **Splunk Enterprise Server** (10.0.0.58) listens on TCP port **9997** for incoming logs from forwarders.
3. I use my **host machine** to connect to Splunk Web (`http://10.0.0.58:8000`) for dashboards, searches, and detections.

<img width="401" height="511" alt="splunk lab diagram(1)" src="https://github.com/user-attachments/assets/c260d92d-0f61-49b0-9b7a-d375e75c5e35" />


### Detections
This lab was configured to detect:
1. Failed SSH login brute force
   Used Hydra on Kali to simulate brute force attacks from a list of passwords.
2. T1107 Bits Job MITTRE ATT&CK
   Used Atomic Red Team to simulate a T1107 persistance attack on Windows 10.

   Refer to attacks.md to see the simulated attacks & Logs generated!
   Refer to detections.md to see the queries and results.
