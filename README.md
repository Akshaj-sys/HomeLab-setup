#  Cybersecurity Home Lab Setup

**Objective**

Set up a local cybersecurity lab with VirtualBox, Ubuntu, and Kali Linux. This safe environment enables hands-on learning of real-world attack and defense techniques, such as network scanning, firewall configuration, and traffic analysis with industry-standard tools.

**Skills Learned**

- Practising Virtualisation by installing Virtual box and setting up Ubuntu and Kali Linux VMs on it
- Basic Linux system hardening by upgrading, updating and cleaning the system
- Learn networking by running simulated attacks with Nmap. Using UFW (Uncomplicated Firewall) to set firewall rules. Analyze network traffic using Wireshark
- Linux command line basics

**Tools Used**

- *VirtualBox* 7.0.26 + Extension Pack
- *Ubuntu 24.04.2*
- *Kali Linux 2025.2*
- *Nmap* – Active network scanner
- *Wireshark* – Network traffic analyser
- *UFW(uncomplicated firewal)* – Host-based firewall (Ubuntu)

**Steps**

**1. Initial Setup & Virtualization**

*Step 1: Installed VirtualBox & Extension Pack* <br>
Downloaded the latest version of VirtualBox from <https://www.virtualbox.org> and installed the extension pack for USB, RDP, and networking support.

*Step 2: Download OS Images*

- Ubuntu 24.04.2 LTS from [ubuntu.com](https://ubuntu.com/download)
- Kali Linux 2025.2 (64-bit) from kali.org

*Step 3: Created VMs*

- Created "Ubuntu" and "Kali Linux" virtual machines in VirtualBox
- Assigned resources (RAM, CPU, disk space) based on system availability
- Attached the respective ISO files to each VM and installed the OS normally
- Created usernames and passwords during OS setup

**2. Network Configuration**

*Step 4: Configured VirtualBox NAT Network*

- Went to File > Tools > Network Manager
- Created a *NAT Network* with:
  - IPv4 Prefix: 10.0.2.0/24
  - Enabled DHCP
- Set each VM’s network adapter to *NAT Network*
  - Adapter Type: Intel PRO/1000 MT Desktop (82540EM)
  - Checked "Cable Connected"

*Step 5: Verified Connectivity*

- Powered on both VMs
- Ran ip a to check IP addresses
- Used ping to confirm connectivity between the two machines

**3. System Preparation**

*Step 6: System Update & Package Installation*

_On Ubuntu:_

```bash
sudo apt update && sudo apt upgrade -y

sudo apt autoremove && sudo apt clean

sudo reboot

sudo apt install -y build-essential git curl wget
```

_On Kali Linux:_

``` bash
sudo apt update && sudo apt upgrade -y

sudo apt autoremove && sudo apt clean

sudo reboot

sudo apt install -y nmap wireshark metasploit-framework
```

*Screenshot* Ubuntu Terminal – installing essential tools

Kali Terminal – installing scan and analysis tools

<img width="1893" height="814" alt="Screenshot 2025-07-29 215321" src="https://github.com/user-attachments/assets/c6cc8106-fa18-40c4-a4a5-8f772227a639" />



**4. Simulated Network Attack & Defense**

*Step 7: Initial Recon Using Nmap*
From Kali Linux, scanned Ubuntu VM using:

` nmap -A 10.0.2.15 `

*Screenshot*  Nmap scan results and OS fingerprinting:
<img width="803" height="684" alt="Screenshot 2025-07-30 133446" src="https://github.com/user-attachments/assets/3127c2c0-158a-4977-b6d1-ac32d96e269c" />



*Step 8: Configured Ubuntu Firewall*

``` bash
sudo apt install ufw

sudo ufw enable

sudo ufw allow ssh

sudo ufw allow from 10.0.2.4

sudo ufw status
```

*Step 9: Analyzed Network Traffic on Ubuntu*  
Installed Wireshark:

``` bash
sudo apt install wireshark

sudo wireshark
```

Ran a second nmap scan from Kali and captured traffic in Wireshark.

 *Screenshot*: Wireshark capturing TCP/UDP packets  
<img width="1086" height="869" alt="Screenshot 2025-07-30 133510" src="https://github.com/user-attachments/assets/a0c7dd13-d26c-4902-a328-1eab1126e155" />


Saved the capture file as:  
attack.pcapng

** 5. VM Power-Off**

*Step 10: Clean Shutdown*

` sudo poweroff `

Shutdown both VMs cleanly

**Network Diagram**

*Screenshot* Simple topology showing how the attack simulation took place:

<img width="604" height="325" alt="Screenshot 2025-07-30 095114" src="https://github.com/user-attachments/assets/1c9e0d84-35e9-4e8d-b8cd-67d8c365a612" />



**Impact**

This project gave me hands-on experience with:

- VM-based lab environments
- Linux OS management and hardening
- Basic attack and defence simulation using open-source tools

It prepared the ground for deeper work in:

- Intrusion detection/prevention
- SIEM-based alerting
- Threat detection and log analysis  
    A foundational milestone in my journey toward becoming a *Cybersecurity Analyst*.
