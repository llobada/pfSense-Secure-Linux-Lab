# pfSense-Secure-Linux-Lab

## 📌 Project Overview
A hands-on lab project demonstrating network security, firewall rules, port forwarding, and traffic management using pfSense and Debian Linux.

The lab simulates a real-world scenario where an internal Linux server is protected by a firewall while allowing controlled external access from a Windows host.

---

## 🎯 Project Goal
- Build a secure virtual network using pfSense
- Protect an internal Debian server running Nginx
- Allow access only via controlled **Port Forwarding**
- Apply proper network segmentation (WAN / LAN)

---

## 🖥️ Lab Environment
- **Host OS:** Windows 10  
- **Virtualization:** VirtualBox  

### Virtual Machines
- **pfSense** (Firewall)
- **Debian Linux** (Server – CLI only)

---

## 🌐 Network Topology

### pfSense (Firewall VM)
- **WAN Interface**
  - Type: NAT
  - IP Address: `10.0.2.15`
- **LAN Interface**
  - Type: Internal Network
  - IP Address: `192.168.1.1`

### Debian Server
- Network: Internal Network (LAN)
- Static IP: `192.168.1.101`
- Service: Nginx Web Server
- Interface: Command-line only (no GUI)

### Network Diagram
![Topology](screenshots/01-topology.png)

---

## 🔧 Configuration Steps

### 1️⃣ pfSense Interfaces Setup
- WAN and LAN configured correctly
- LAN set as default gateway for internal network

![Interfaces](screenshots/02-pfsense-interfaces.png)

---

### 2️⃣ Debian Network Configuration
- Static IP assigned manually
- Default gateway set to pfSense LAN IP

![Debian IP](screenshots/07-debian-ip-config.png)

---

### 3️⃣ VirtualBox Port Forwarding (Host → pfSense WAN)
| Host Port | pfSense Port | Purpose |
|---------|--------------|--------|
| 8443 | 443 | pfSense Web GUI |
| 9090 | 9090 | Access internal server |

![VB PF](screenshots/04-virtualbox-port-forwarding.png)

---

### 4️⃣ pfSense NAT Port Forward Rule
- Incoming traffic on **WAN port 9090**
- Forwarded to:
  - IP: `192.168.1.101`
  - Port: `80` (Nginx)

![NAT Rule](screenshots/05-pfsense-nat-rule.png)

---

### 5️⃣ Firewall Rules
- Only required ports allowed
- All other traffic blocked by default

![Firewall](screenshots/06-firewall-rules.png)

---

## 🌍 Final Access Points

- **pfSense Web Interface:**  
  `https://127.0.0.1:8443`

- **Nginx Web Server:**  
  `http://127.0.0.1:9090`

![Final Access](screenshots/09-final-access-from-windows.png)

---

## 🔐 Security Highlights
- Network segmentation between WAN and LAN
- No direct access to internal server
- Controlled exposure via NAT & firewall rules
- Linux server running without GUI (reduced attack surface)

---

## 🧠 Skills Demonstrated
- Firewall administration (pfSense)
- NAT & Port Forwarding
- Network segmentation
- Linux server administration
- Secure service exposure
- Virtualized lab design

---

## 📁 Repository Structure
