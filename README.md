
# **Advanced Incident Detection and Response Using Microsoft Security Stack**

## **Project Overview**  
In preparation for the Microsoft SC-200 exam, I simulated a real-world attack scenario using a Mythic C2 server and conducted thorough detection, investigation, and response activities using Microsoft Sentinel and Microsoft Defender for Endpoint. This project involved simulating multi-staged cyber attacks, analyzing threat indicators, and automating responses to enhance incident management and improve the security posture of the environment.

---

## **Table of Contents**  
🔹 **Project Introduction**  
🔹 **Mythic C2 Attack Simulation**  
   - Mythic C2 Deployment  
   - Brute-Force Attack Initiation  
   - Defense Evasion  
   - Payload Creation and Deployment  
   - Command and Control (C2) Operation  
   - File Exfiltration  
🔹 **Detection and Response Using Microsoft Sentinel**  
   - Analytics Rule Creation  
   - User & Group Management  
   - Automation & Incident Response  
🔹 **Incident Investigation and Remediation**  
   - Verification and Initial Investigation  
   - Affected Assets & Isolation  
   - Live Response & File Analysis  
   - Incident Closure & Reporting  
🔹 **Preventive Measures**  
🔹 **Conclusion and Key Takeaways**  
🔹 **References**

---

## **1. Project Introduction**  
This project was undertaken to simulate advanced cyber threats using the Mythic C2 server, which allowed for hands-on experience in incident detection and response using Microsoft Sentinel and Microsoft Defender for Endpoint. The simulation included a mix of brute-force attacks, defense evasion, and data exfiltration, closely reflecting real-world attack scenarios.

💻 **Tools Used:**  
   - Mythic C2 with Apollo Agent  
   - Microsoft Sentinel  
   - Microsoft Defender for Endpoint (MDE)  
   - PowerShell  
   - Azure Virtual Machine  
   - Intune for Endpoint Onboarding  

---

## **2. Mythic C2 Attack Simulation**  
### **2.1 Mythic C2 Deployment**  
🚀 Configured the Mythic C2 Server and set up an Apollo Agent.  
⚙️ Created an HTTP profile for agent communication with the attacker’s machine.  
💻 Provisioned an Azure Virtual Machine (VM) as the target environment and onboarded it to Microsoft Defender for Endpoint using Intune.  
🔐 Configured firewall settings and deployed a decoy file named `AdminPass.txt` for detection testing.  
🖼️ *[Insert screenshots of Mythic C2 configuration, VM setup, and decoy file deployment]*  

### **2.2 Brute-Force Attack Initiation**  
🔨 Used Kali Linux to initiate a brute-force attack targeting the Windows VM's RDP, successfully cracking the credentials.  
🔑 Accessed the target VM via XFREERDP.  
🖼️ *[Insert screenshots of brute-force attack and successful login]*  

### **2.3 Defense Evasion**  
❌ Disabled Windows Security features to avoid detection.  
✔️ Whitelisted a specific path to bypass antivirus scans for malware deployment.  
🖼️ *[Insert screenshots of disabled Windows Security and whitelisting process]*  

### **2.4 Payload Creation and Deployment**  
🛠️ Generated a payload using Mythic C2 and downloaded it onto the target VM's whitelisted path.  
▶️ Executed the payload using PowerShell IEX to establish a secure connection.  
🖼️ *[Insert screenshots of payload creation and execution]*  

### **2.5 Command and Control (C2) Operation**  
🔗 Established a C2 connection between the attacker’s Mythic server and the compromised VM.  
📌 Set up persistence mechanisms for continued access to the VM.  
🖼️ *[Insert screenshots of active C2 connection]*  

### **2.6 File Exfiltration**  
📁 Located and exfiltrated the decoy file `AdminPass.txt` to simulate data theft.  
🖼️ *[Insert screenshots of file exfiltration]*  

---

## **3. Detection and Response Using Microsoft Sentinel**  
### **3.1 Analytics Rule Creation**  
📊 Created custom rules to monitor process creation events and potential C2 activities.  
🔔 Configured Sentinel to trigger alerts based on suspicious behavior.  
🖼️ *[Insert screenshots of analytics rule configuration in Sentinel]*  

### **3.2 User & Group Management**  
👥 Created user accounts and organized them into a SecOps Group for incident management.  
🔑 Implemented role-based access control (RBAC) for SOC Team Lead.  
🖼️ *[Insert screenshots of user and group management in Azure AD]*  

### **3.3 Automation & Incident Response**  
⚙️ Built automation rules to trigger high-priority alerts and assign incidents to the SOC Team Lead.  
✉️ Configured playbooks to send email notifications to the SOC team.  
🖼️ *[Insert screenshots of automation rules and playbook configuration]*  

---

## **4. Incident Investigation and Remediation**  
### **4.1 Verification and Initial Investigation**  
🔍 Investigated Sentinel alerts for Mythic C2 detection, reviewing evidence like suspicious files and IPs.  
🖼️ *[Insert screenshots of Sentinel dashboard and evidence collection]*  

### **4.2 Affected Assets & Isolation**  
🛑 Isolated the compromised VM using Microsoft Defender for Endpoint to prevent further threats.  
🖼️ *[Insert screenshots of isolation process in MDE]*  

### **4.3 Live Response & File Analysis**  
📂 Used MDE's Advanced Live Response to access the compromised machine and analyze the malware.  
🖼️ *[Insert screenshots of live response session and analysis results]*  

### **4.4 Incident Closure & Reporting**  
📄 Documented the incident for internal review and released the isolated VM after remediation.  
🖼️ *[Insert sample incident report or screenshots of Sentinel reporting]*  

### **4.5 Preventive Measures**  
🔒 Blocked identified IPs and malicious file hashes.  
🚫 Updated firewall rules and enforced stricter password policies.  
🖼️ *[Insert screenshots of preventive measures]*  

---

## **5. Conclusion and Key Takeaways**  
This project provided invaluable hands-on experience in managing advanced threats with Microsoft Sentinel and Defender for Endpoint. It emphasized the importance of proactive defense, automation, and incident management to maintain a secure environment in the face of evolving cyber threats.

---

## **6. References**  
📚 **Microsoft Learn Documentation:** Microsoft Sentinel  
📚 **Mythic C2 Framework:** Mythic Documentation  
📚 **Microsoft Defender for Endpoint:** MDE Documentation  

---
