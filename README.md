
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


## Here are the steps to Deploy a Mythic Command and Control Server 🚀:

### A. Choose Your Cloud Provider (Azure or Vultr Example)
- Head to your chosen cloud provider.
- For this guide, we're using **Vultr**.
- Deploy a new server by selecting **Deploy New Server**.

**Server Specifications**:
- **Cloud Compute (Shared CPU)**
- **Location**: London 🇬🇧
- **OS**: Ubuntu 22.04 LTS 🐧
- **Specs**: 2 vCPUs, 4GB RAM (crucial for smooth operation).
- **Storage**: 80GB SSD 💾
- Uncheck **Auto Backups** and **IPv6**.

📌 **Tip**: You can name the server as you like. Once configured, hit **Deploy Now** and wait for the server to spin up.

---

### B. Connect to Your Server 🔐
- Once the server is up, SSH into it via **PowerShell** (Windows) or your terminal (Linux/Mac).
  
```bash
ssh root@<your-server-ip>
```
- Enter the password found in your Vultr console. Now, you’re connected!

---

### C. Update & Upgrade Your Server 🔄
- Run these commands to ensure your system is fully updated:

```bash
apt-get update && apt-get upgrade -y
```

---

### D. Install Docker Compose & Make ⚙️
- Install **Docker Compose**:

```bash
apt install docker-compose
```

- Install **Make**:

```bash
apt install make
```

---

### E. Clone the Mythic Repository 📁
- Clone Mythic from GitHub:

```bash
git clone https://github.com/its-a-feature/Mythic
```

- Navigate to the Mythic directory:

```bash
cd Mythic
```

- Run the installation script:

```bash
./install_docker_ubuntu.sh
```

- After installation, restart Docker and check its status:

```bash
systemctl restart docker
systemctl status docker
```

---

### F. Start Mythic 💻
- To start Mythic, run:

```bash
make
```

- Start the Mythic Command-Line Interface (CLI):

```bash
./mythic-cli start
```

---

### G. Configure Your Firewall 🔒
- Head back to **Vultr** to set up a firewall.
- Create a **Firewall Group** and allow only trusted IPs (like your own).

---

### H. Access the Mythic Web GUI 🌐
- Open your browser and navigate to the Mythic Web GUI:

```url
https://<your-mythic-ip>:7443
```

- The default username is **mythic_admin**. To get the password:

```bash
ls -la
cat .env
```

- Look for `MYTHIC_ADMIN_PASSWORD=` in the output and use it to log in!

 ![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570396_w.jpg)
---

### ✅ Mythic Overview
Once logged in, you’ll see the **Mythic dashboard**. Here, you can manage agents, profiles, and more.

📅 **Next Steps**: Explore your new Mythic C2 setup!

---

### 2.2 **🔑 Brute-Force Attack Initiation**  

 ![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Mapping-a-Simulated-Attack-Path/photo_6010098396611854206_w.jpg)
- Used a Kali Linux machine to initiate a brute-force attack targeting the Windows VM's RDP using a custom wordlist (brute.txt).  
- Successfully cracked the credentials and accessed the target VM via XFREERDP.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6039540521979986956_y.jpg)

---

### 2.3 **🛡️ Defense Evasion**  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Mapping-a-Simulated-Attack-Path/photo_6010098396611854208_w.jpg)
- Disabled Windows Security features on the compromised VM to avoid detection.  
- Whitelisted the path `C:\Users\auroravm\Downloads` to evade antivirus scans.

![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6039540521979986970_w.jpg)

---

### 2.4 **💻 Payload Creation Deployment and Execution**  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6010098396611854209_w.jpg)

#### Payload Created
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570395_w.jpg)

#### Payload Deployed
- Generated a payload named `svcanonymous.exe` using Mythic C2, designed to establish a secure connection back to the C2 server.  
- Downloaded the payload onto the target VM’s whitelisted path.  
  ![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6039540521979986973_w.jpg)
#### Payload - Executed using PowerShell IEX to activate the C2 connection. 
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6039540521979986974_w.jpg)
---

### 2.5 **📡 Command and Control (C2) Operation**  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6010098396611854210_w.jpg)
- Established a C2 connection between the attacker’s Mythic server and the compromised VM.  
- Set up persistence mechanisms for continued access to the VM, even after reboots.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6039540521979986978_w.jpg)

---

### 2.6 **📥 File Exfiltration**  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6010098396611854211_w.jpg)
- Located the decoy file `AdminPass.txt` on the target VM.  
- Successfully exfiltrated the file back to the attacker’s Mythic server, simulating data theft.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/Stage%202/photo_6041792321793671784_w.jpg)

---

## 3️⃣ **Detection and Response Using Microsoft Sentinel**  

### 3.1 **📊 Analytics Rule Creation**  
- Created custom detection rules in Microsoft Sentinel to monitor for:  
   - Process creation events (4688) for commands like `powershell.exe` and `cmd.exe`.  
   - Network connection events (5156) indicating potential C2 activities.  
- Configured Sentinel to trigger alerts for these activities.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570391_w.jpg)

---

### 3.2 **👥 User & Group Management**  
- Created user accounts and organized them into a SecOps Group for incident management.
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570372_w.jpg)
  
- Implemented role-based access control (RBAC) to assign the Microsoft Sentinel Contributor role to the SOC Team Lead.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570387_w.jpg)

---

### 3.3 **🤖 Automation & Incident Response**  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570390_w.jpg)
- Built an automation rule in Sentinel to:  
   - Trigger high-priority alerts.  
   - Assign incidents to the SOC Team Lead.  
   - Run a playbook that sends email notifications to the SOC Lead and SOC Manager.  
![SOC](https://github.com/Virus192/Azure-SOAR-Automation-and-Incident-Response/blob/main/Images/photo_6035328477617570393_w.jpg)

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
