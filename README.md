
# 🚨 **Advanced Incident Detection and Response Using Microsoft Security Stack**

## 📄 **Project Overview**  
In preparation for the Microsoft SC-200 exam, I simulated a real-world attack scenario using a Mythic C2 server and conducted thorough detection, investigation, and response activities using Microsoft Sentinel and Microsoft Defender for Endpoint. This project involved simulating multi-staged cyber attacks, analyzing threat indicators, and automating responses to enhance incident management and improve the security posture of the environment.

---

## 🗂️ **Table of Contents**  
- 🔍 **Project Introduction**  
- 🎯 **Mythic C2 Attack Simulation**  
   - 🚀 **Mythic C2 Deployment**  
   - 🔑 **Brute-Force Attack Initiation**  
   - 🛡️ **Defense Evasion**  
   - 💻 **Payload Creation and Deployment**  
   - 📡 **Command and Control (C2) Operation**  
   - 📥 **File Exfiltration**  
- 🛠️ **Detection and Response Using Microsoft Sentinel**  
   - 📊 **Analytics Rule Creation**  
   - 👥 **User & Group Management**  
   - 🤖 **Automation & Incident Response**  
- 🕵️ **Incident Investigation and Remediation**  
   - 📝 **Verification and Initial Investigation**  
   - 🖥️ **Affected Assets & Isolation**  
   - 🛠️ **Live Response & File Analysis**  
   - 📈 **Incident Closure & Reporting**  
   - 🔐 **Preventive Measures**  
- 📚 **Conclusion and Key Takeaways**  
- 📑 **References**  

---

## 1️⃣ **Project Introduction**  
This project was undertaken to simulate advanced cyber threats using the Mythic C2 server, which allowed for hands-on experience in incident detection and response using Microsoft Sentinel and Microsoft Defender for Endpoint. The simulation included a mix of brute-force attacks, defense evasion, and data exfiltration, closely reflecting real-world attack scenarios.

**🛠️ Tools Used:**
- 🖥️ Mythic C2 with Apollo Agent  
- 🛡️ Microsoft Sentinel  
- 🔒 Microsoft Defender for Endpoint (MDE)  
- 💻 PowerShell  
- ☁️ Azure Virtual Machine  
- 🔗 Intune for Endpoint Onboarding  

---

## 2️⃣ **Mythic C2 Attack Simulation**  

### 2.1 **🚀 Mythic C2 Deployment**  
- Configured the Mythic C2 Server and set up an Apollo Agent.  
- Created an HTTP profile for agent communication with the attacker’s machine.  
- Provisioned an Azure Virtual Machine (VM) as the target environment.  
- Onboarded the VM to Microsoft Defender for Endpoint using Intune.  
- Configured firewall settings to allow all inbound network traffic to facilitate the simulation.  
- Deployed a decoy file named AdminPass.txt in the target VM for threat detection.  
🖼️ [Insert screenshots of Mythic C2 configuration, VM setup, and decoy file deployment]

---

### 2.2 **🔑 Brute-Force Attack Initiation**  
- Used a Kali Linux machine to initiate a brute-force attack targeting the Windows VM's RDP using a custom wordlist (brute.txt).  
- Successfully cracked the credentials and accessed the target VM via XFREERDP.  
🖼️ [Insert screenshots of Kali Linux brute-force attack commands and successful login]

---

### 2.3 **🛡️ Defense Evasion**  
- Disabled Windows Security features on the compromised VM to avoid detection.  
- Whitelisted the path `C:\Users\auroravm\Downloads` to evade antivirus scans.  
🖼️ [Insert screenshots of disabled Windows Security and whitelisting process]

---

### 2.4 **💻 Payload Creation and Deployment**  
- Generated a payload named `svcanonymous.exe` using Mythic C2, designed to establish a secure connection back to the C2 server.  
- Downloaded the payload onto the target VM’s whitelisted path.  
- Executed the payload using PowerShell IEX to activate the C2 connection.  
🖼️ [Insert screenshots of payload creation and PowerShell command execution]

---

### 2.5 **📡 Command and Control (C2) Operation**  
- Established a C2 connection between the attacker’s Mythic server and the compromised VM.  
- Set up persistence mechanisms for continued access to the VM, even after reboots.  
🖼️ [Insert screenshots of active C2 connection and persistence settings]

---

### 2.6 **📥 File Exfiltration**  
- Located the decoy file `AdminPass.txt` on the target VM.  
- Successfully exfiltrated the file back to the attacker’s Mythic server, simulating data theft.  
🖼️ [Insert screenshots of file exfiltration process]

---

## 3️⃣ **Detection and Response Using Microsoft Sentinel**  

### 3.1 **📊 Analytics Rule Creation**  
- Created custom detection rules in Microsoft Sentinel to monitor for:  
   - Process creation events (4688) for commands like `powershell.exe` and `cmd.exe`.  
   - Network connection events (5156) indicating potential C2 activities.  
- Configured Sentinel to trigger alerts for these activities.  
🖼️ [Insert screenshots of analytics rule configuration in Microsoft Sentinel]

---

### 3.2 **👥 User & Group Management**  
- Created user accounts and organized them into a SecOps Group for incident management.  
- Implemented role-based access control (RBAC) to assign the Microsoft Sentinel Contributor role to the SOC Team Lead.  
🖼️ [Insert screenshots of user and group management in Azure AD]

---

### 3.3 **🤖 Automation & Incident Response**  
- Built an automation rule in Sentinel to:  
   - Trigger high-priority alerts.  
   - Assign incidents to the SOC Team Lead.  
   - Run a playbook that sends email notifications to the SOC Lead and SOC Manager.  
🖼️ [Insert screenshots of automation rules and playbook configuration]

---

## 4️⃣ **Incident Investigation and Remediation**  

### 4.1 **📝 Verification and Initial Investigation**  
- Received an alert for Mythic C2 detection.  
- Investigated the alert in Microsoft Sentinel, reviewing evidence such as:  
   - Suspicious file `svcanonymous.exe`.  
   - Mode of entry (brute-force attack).  
   - IPs involved in the attack.  
🖼️ [Insert screenshots of Sentinel incident dashboard and evidence collection]

---

### 4.2 **🖥️ Affected Assets & Isolation**  
- Isolated the compromised VM using Microsoft Defender for Endpoint.  
- Prevented lateral movement and further network access.  
🖼️ [Insert screenshots of isolation process in MDE]

---

### 4.3 **🛠️ Live Response & File Analysis**  
- Utilized MDE's Advanced Live Response to access the compromised machine.  
- Deleted the malicious file and ran a detailed analysis in a sandbox environment.  
🖼️ [Insert screenshots of live response session and sandbox analysis results]

---

### 4.4 **📈 Incident Closure & Reporting**  
- Released the isolated VM after remediation.  
- Documented the incident for internal review and future training.  
🖼️ [Insert sample incident report or screenshots of reporting in Microsoft Sentinel]

---

### 4.5 **🔐 Preventive Measures**  
- Blocked identified IP addresses and malicious SHA1 hashes.  
- Updated firewall rules to restrict unauthorized access.  
- Enforced stricter password policies and disabled unsigned script execution.  
🖼️ [Insert screenshots of preventive measures and updated configurations]

---

## 5️⃣ **Conclusion and Key Takeaways**  
This project provided invaluable insights into the practical application of Microsoft Sentinel and Microsoft Defender for Endpoint in detecting and responding to sophisticated threats. The simulation emphasized the importance of automation, proactive threat hunting, and effective incident management in modern security operations.

---

## 6️⃣ **References**  
- 📚 Microsoft Learn Documentation: Microsoft Sentinel  
- 🛠️ Mythic C2 Framework: Mythic Documentation  
- 🔒 Microsoft Defender for Endpoint: MDE Documentation  
