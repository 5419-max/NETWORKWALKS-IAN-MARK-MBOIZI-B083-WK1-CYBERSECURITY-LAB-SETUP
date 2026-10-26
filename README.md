# NETWORKWALKS-IAN-MARK-MBOIZI-B083-WK1-CYBERSECURITY-LAB-SETUP
Isolated virtual lab built with VirtualBox and Kali Linux for cybersecurity testing and penetration testing practice.
<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Waqas%20Karim%20CCIE-C00000?style=flat-square" />
</p>

📌 Project Overview

This project sets up an isolated virtual cybersecurity lab on my own laptop using VirtualBox and Kali Linux. The lab runs on a private NAT Network so I can practice scanning, reconnaissance and security tools safely, without putting my real machine or home network at risk.

More machines (Windows, Android, CTF targets) can be added to the same network later for authorized testing.

🎯 Objectives
Install and configure VirtualBox
Import Kali Linux as the attacker machine
Create a NAT Network on 10.0.0.0/24
Give Kali the fixed IP 10.0.0.2/24 with full internet access
Enable clipboard and drag/drop
Share the host Downloads folder with Kali
Take a clean snapshot
Document the setup, the mistakes and the lessons

🏗️ Lab Architecture

Lab architecture

Additional VMs will join the same NatNetwork in future projects.

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 11         |
| 🧠 Host RAM        | 16 GB              |
| ⚡ Processor       | AMD Ryzen 3        |    
| 🧰 Hypervisor      | VirtualBox 7.2.22  |
| 🐉 Security OS     | Kali Linux 2026.2  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

🪜 Lab Setup Procedure
Step 1. Install 7-Zip

Kali's VirtualBox image is distributed as a .7z archive, so 7-Zip is needed to extract it.

Step 2. Install VirtualBox

Installed VirtualBox 7.2.22 from virtualbox.org.

Step 3. Create the NAT Network

Opened the network manager with Ctrl+H (or File → Tools → Network), then went to the NAT Networks tab, clicked Create, and set:
Name:        NatNetwork
IPv4 Prefix: 10.0.0.0/24
DHCP:        Enabled
IPv6:        Disabled

<img width="870" height="937" alt="image" src="https://github.com/user-attachments/assets/b175ce00-a0f6-48b0-b8eb-8e387db84ae4" />


NatNetwork settings

A NAT Network was chosen instead of plain NAT because VMs on the same NAT Network can talk to each other and still reach the internet. Plain NAT isolates every VM from the others.

Step 4. Import Kali Linux

<img width="839" height="401" alt="Screenshot 2026-10-26 124202" src="https://github.com/user-attachments/assets/940174a8-a7bb-4f20-9af6-e623ee5976f0" />


Downloaded the VirtualBox build of Kali from kali.org, extracted it with 7-Zip, and imported it by opening the .vbox file.

Network adapter in Settings → Network → Adapter 1:

Attached to:      NAT Network
Name:             NatNetwork
Promiscuous Mode: Allow All

<img width="956" height="631" alt="image" src="https://github.com/user-attachments/assets/11172351-7cca-4887-8778-1525cb0cc89e" />


Kali adapter settings

Step 5. Clipboard, Drag/Drop and Shared Folder
Settings → General → Advanced: Shared Clipboard = Bidirectional, Drag'n'Drop = Bidirectional
Settings → Shared Folders: added the Windows Downloads folder with Auto-mount and Make Permanent ticked

Clipboard and shared folder

Step 6. Set the static IP in Kali

Network icon → Edit Connections → Wired connection 1 → IPv4 Settings:
Method:  Manual
Address: 10.0.0.2
Netmask: 24
Gateway: 10.0.0.1
DNS:     8.8.8.8
Kali IPV4 settings

<img width="954" height="463" alt="Screenshot 2026-10-26 121125" src="https://github.com/user-attachments/assets/24cd7051-7f7c-4b5c-ba7c-66fec5128c2b" />

Step 7. Take a clean snapshot

Machine → Take Snapshot, named Clean Kali - Network Setup. This is my known-good baseline to roll back to after risky experiments.

# 🔎 Lab Verification

| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | Correct Kali IP displayed (10.0.0.2/24)      |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping -c 3 8.8.8.8`             | Successful replies              |
| 🔎 Test DNS resolution        | `ping -c 3 google.com`          | Domain resolves                 |
| 🧰 Verify Nmap                | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot            | Restore snapshot and run `ip a` | Baseline configuration restored |

### Example Results

```text
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```

---

🐞 Problems Encountered & Solutions
Problem 1. I could not find the Network menu

VirtualBox 7.2 did not show Network where I expected, and the manager looked empty because a fresh install has no networks.

Fix: The network manager opens with Ctrl+H or File → Tools → Network. A fresh install has no NAT networks, so I had to create NatNetwork myself. The command line also works as a backup:

```text

VBoxManage natnetwork add --netname NatNetwork --network "10.0.0.0/24" --enable --dhcp on

```

Problem 2. "Destination Host Unreachable" from 10.0.0.2

After setting the static IP, both ping 8.8.8.8 and ping google.com failed with From 10.0.0.2 ... Destination Host Unreachable.

Failed ping

What it meant: google.com still resolved to an IP address, so DNS was fine. The failure was in the route out. Kali could not reach a working gateway.

Fix attempts

```text

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"

```

This dad-timeout fix is the known workaround for static IPs on VirtualBox 7 with newer Kali.

Problem 3. My workaround route used the wrong gateway

To get internet working quickly I ran:

```text

sudo ip route replace default via 10.0.2.2 dev eth0

```

Internet worked, but this was a mistake in my setup, not a real fix:

10.0.2.2 is the gateway of VirtualBox's plain NAT mode, not my NAT Network (10.0.0.0/24, gateway 10.0.0.1).
The route is temporary and would disappear after a reboot.
It did not match the lab requirement and could break communication with other VMs later.

Root cause: When I checked Settings → Network → Adapter 1, the Kali VM was attached to plain NAT, not NAT Network. That is why only the 10.0.2.2 gateway answered. My static IP and gateway (10.0.0.x) were correct, but the VM was plugged into the wrong virtual network.

Fix: I switched Adapter 1 to NAT Network → NatNetwork, reverted to the correct gateway, and re-tested:
```text

sudo ip route replace default via 10.0.0.1 dev eth0
ip route
ping -c 3 8.8.8.8
Internet then worked with default via 10.0.0.1, matching the task.

```

💡 What I Learned
NAT vs NAT Network. Plain NAT gives each VM its own isolated network (gateway 10.0.2.2). NAT Network puts VMs on one shared private network (here 10.0.0.0/24, gateway 10.0.0.1) so they can talk to each other.
Read error messages carefully. "Destination Host Unreachable" from my own IP plus a working DNS lookup told me the problem was the gateway/route, not DNS.
A fix that works is not always the right fix. My 10.0.2.2 workaround restored internet but hid a configuration mismatch. I now check why something works.
Temporary vs permanent changes. ip route replace is lost on reboot. Permanent settings belong in NetworkManager (Edit Connections).
Useful troubleshooting commands: ip a, ip route, ping, and nmcli.
Snapshots. Take one when everything works, before risky experiments.
Documentation. Writing down commands, screenshots, errors and fixes is part of professional security work.

🔐 Security & Ethical Use

This lab is for education only. Only test systems that I own or have explicit permission to test.

🔗 Tools & Resources
7-Zip: https://7-zip.org/download.html
VirtualBox: https://virtualbox.org/wiki/Downloads
Kali Linux: https://kali.org/get-kali 

👤 Author

Mboizi Ian Mark Cybersecurity & Networking Student, Kampala, Uganda Networkwalks Academy: Week 01, Project 1 LinkedIn: [add your link]
