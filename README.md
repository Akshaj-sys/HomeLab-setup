# 🔒 Cybersecurity Home Lab Setup

**📌 Objective**

To build a local, controlled cybersecurity lab environment using VirtualBox, Ubuntu, and Kali Linux. This lab enables safe, hands-on learning of real-world attack and defense techniques, including network scanning, firewall configuration, and traffic analysis using industry-standard tools.

**🧠 Skills Learned**

- Practising Virtualisation by installing Virtual box and setting up Ubuntu and Kali Linux VMs on it
- Basic Linux system Hardening by upgrading, updating and cleaning the system
- Networking concepts by Running simulated attacks using Nmap, using UFW (Uncomplicated Firewall) to configure firewall rules, analysing network traffic using Wireshark
- Linux command line basics

**🛠 Tools Used**

- *VirtualBox* 7.0.26 + Extension Pack
- *Ubuntu 24.04.2*
- *Kali Linux 2025.2*
- *Nmap* – Active network scanner
- *Wireshark* – Network traffic analyser
- *UFW* – Host-based firewall (Ubuntu)

**🧩 Steps**

**🛠️ 1. Initial Setup & Virtualization**

*✅ Step 1: Installed VirtualBox & Extension Pack*
Downloaded the latest version of VirtualBox from <https://www.virtualbox.org> and installed the extension pack for USB, RDP, and networking support.

*✅ Step 2: Downloaded OS Images*

- Ubuntu 24.04.2 LTS from [ubuntu.com](https://ubuntu.com/download)
- Kali Linux 2025.2 (64-bit) from kali.org

*✅ Step 3: Created VMs*

- Created "Ubuntu" and "Kali Linux" virtual machines in VirtualBox
- Assigned resources (RAM, CPU, disk space) based on system availability
- Attached respective ISO files to each VM and installed OS normally
- Created usernames and passwords during OS setup

**🌐 2. Network Configuration**

*✅ Step 4: Configured VirtualBox NAT Network*

- Went to **File > Tools > Network Manager**
- Created a **NAT Network** with:
  - IPv4 Prefix: 10.0.2.0/24
  - Enabled DHCP
- Set each VM’s network adapter to **NAT Network**
  - Adapter Type: Intel PRO/1000 MT Desktop (82540EM)
  - Checked "Cable Connected"

*✅ Step 5: Verified Connectivity*

- Powered on both VMs
- Ran ip a to check IP addresses
- Used ping to confirm connectivity between the two machines

**🔧 3. System Preparation**

*✅ Step 6: System Update & Package Installation*

_On Ubuntu:_

<pre>```bash sudo apt update && sudo apt upgrade -y

sudo apt autoremove && sudo apt clean

sudo reboot

sudo apt install -y build-essential git curl wget ```</pre>

_On Kali Linux:_

sudo apt update && sudo apt upgrade -y

sudo apt autoremove && sudo apt clean

sudo reboot

sudo apt install -y nmap wireshark metasploit-framework

*Screenshot*: Ubuntu Terminal – installing essential tools

*Screenshot*: Kali Terminal – installing scan and analysis tools

**🛡️ 4. Simulated Network Attack & Defense**

*✅ Step 7: Initial Recon Using Nmap*
From Kali Linux, scanned Ubuntu VM using:

nmap -A 10.0.2.15

*Screenshot*: Nmap scan results and OS fingerprinting

*✅ Step 8: Configured Ubuntu Firewall*

sudo apt install ufw

sudo ufw enable

sudo ufw allow ssh

sudo ufw allow from 10.0.2.4

sudo ufw status

*✅ Step 9: Analyzed Network Traffic on Ubuntu*  
Installed Wireshark:

sudo apt install wireshark

sudo wireshark

Ran a second nmap scan from Kali and captured traffic in Wireshark.

 *Screenshot*: Wireshark capturing TCP/UDP packets  
_(already included in screenshot)_

Saved the capture file as:  
📄 attack.pcapng

**🔁 5. VM Power-Off**

*✅ Step 10: Clean Shutdown*

sudo poweroff

Shutdown both VMs cleanly

**📉 Network Diagram**

*Screenshot*: Simple topology showing how the attack simulation took place:

 

**📈 Impact**

This project gave me hands-on experience with:

- VM-based lab environments
- Linux OS management and hardening
- Basic attack and defence simulation using open-source tools

It prepared the ground for deeper work in:

- Intrusion detection/prevention
- SIEM-based alerting
- Threat detection and log analysis  
    A foundational milestone in my journey toward becoming a *Cybersecurity Analyst*.
