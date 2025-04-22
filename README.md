# 🏫 University Campus Network Design – Cisco Packet Tracer
This project presents a comprehensive network infrastructure for a university campus, meticulously designed and simulated using Cisco Packet Tracer. It encompasses multiple departments and facilities, ensuring seamless communication, resource sharing, and centralized services

---

## 📌 Table of Contents

1. [Project Overview](#project-overview)
2. [Network Topology](#network-topology)
3. [IP Addressing Scheme](#ip-addressing-scheme)
4. [Routing Configuration](#routing-configuration)
5. [Server Implementations](#server-implementations)
6. [Testing & Validation](#testing--validation)
7. [Getting Started](#getting-started)
8. [Screenshots](#screenshots)
9. [Contributors](#contributors)
10. [License](#license)

---

## 🔍 Project Overvie

The objective of this project is to design and implement a robust and scalable network for a university campus using Cisco Packet Tracer. This network integrates multiple academic and administrative buildings, allowing for efficient data sharing, resource access, dynamic routing, and deployment of essential services like DNS, DHCP, FTP, and Mail serves.

---

## 🗺️ Network Topoloy

The campus comprises several buildings, each employing distinct network topologes:

| Building                          | Topology Used | Devices Used                          |
|-----------------------------------|---------------|----------------------------------------|
| Administration Building 1         | Star          | Switch, 8 PCs, Mail Server             |
| Administration Building 2         | Star          | Hub, 8 PCs                             |
| Administration Building 3         | Mesh          | Switch, 8 PCs                          |
| Library                           | Hybrid        | Switch, Hub, 10 PCs, DHCP Server       |
| Computer Science Department 1     | Mesh          | Hub, 12 PCs, DNS Server                |
| Computer Science Department 2     | Mesh          | Switches, 12 PCs                       |
| Engineering Department            | Bus           | Hub, 5 PCs, FTP Server                 |

**Devices Utilized:**

- **Switch PT*: Facilitates high-performance interconnections in mesh and hybrid setps.
- **Hub PT*: Enables shared medium communication in star and bus layots.
- **Routers*: Provide inter-building connectivity and routng.
- **Servers*: Deployed for DHCP, DNS, Mail, and FTP functionalites.
- **PCs*: Serve as end-user devies.
- **Cables*: Straight-through for PC-to-switch/hub; cross cables for switch-to-switch/router connectins.

---

## 🧮 IP Addressing Schme

The network utilizes Fixed-Length Subnet Masking (FLSM), starting with the base network `172.11.0.0/16`. Each LAN is assigned a `/28` subnet to accommodate end devices and servers, while `/30` subnets are used for router interconnectons.

**Sample Subnet Allocation:**

| Subnet No. | Network Address | Usable IP Range           | Broadcast Address |
|------------|-----------------|---------------------------|-------------------|
| 1          | 172.11.0.0      | 172.11.0.1 – 172.11.0.14  | 172.11.0.15       |
| 2          | 172.11.0.16     | 172.11.0.17 – 172.11.0.30 | 172.11.0.31       |
| 3          | 172.11.0.32     | 172.11.0.33 – 172.11.0.46 | 172.11.0.47       |
| ...        | ...             | ...                       | ...              |

Router-to-router links utilize `/30` subnets from `172.11.1.0/30` upwrds.

---

## 🔁 Routing Configuraion

Dynamic routing is implemented using RIP version 2 to facilitate efficient route propagation across the nework.

**Configuration Steps:**

```bash
Router> enable
Router# config terminal
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 172.11.0.0
Router(config-router)# network 172.11.1.0
``


This setup ensures automatic route updates between all routers, enhancing scalability and manageablity.

---

## 🖥️ Server Implementaions

Each building hosts specific network services to cater to the campus's diverseneeds:

| Building                     | Server Type   | Purpose                                                                 |
|------------------------------|---------------|-------------------------------------------------------------------------|
| Library                      | DHCP Servr   | Automatically assigns IP addresses to clients within the libray LAN.  |
| CS Department 1              | DNS Serve    | Resolves domain names like `ftp.local`, `mail.local` to IP addesses.  |
| Engineering Department       | FTP Serve    | Hosts files for upload/download across the ampus.                     |
| Admin Building 1             | Mail Servr   | Manages internal mail services (SMTP +POP3).                          |

**Sample DNS Records:**

| Domain Name      | Mapped IP       |
|------------------|-----------------|
| www.campus.local | 172.11.0.33     |
| mail.local       | 172.11.0.62     |
| ftp.local        | 172.11.0.110    |

---

## ✅ Testing & Validtion

To ensure network reliability and functionality, the following tests were conucted:

- **Inter-Building Connectivty:** Utilized the `ping` command to test communication between PCs across different buidings.

  ```bash
  ping <target IP>
  ```

- **Service Accessibilty:** Verified access to FTP, Mail, and DNS services from various nodes within the ntwork.

- **DHCP Functionalty:** Confirmed automatic IP address assignment to client devices within the Libray LAN.

---

## 🚀 Getting Started

To explore or modify the network setup:

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/Peeyush-04/Networking.git
   ```

2. **Open the Project:*

   - Launch Cisco PacketTracer
   - Open the `.pkt` file located in the cloned repository. 
