Design and Implementation of a Multi-LAN FTP System Using Dynamic Routing

Project Overview
This project demonstrates the design and implementation of a multi-LAN campus network using Cisco Packet Tracer. The network supports multiple departments (Students, Faculty, and Admin) and provides role-based file sharing using the File Transfer Protocol (FTP).

The network uses dynamic routing (RIP v2) to interconnect multiple routers and integrates a DNS server to enable hostname-based access to FTP servers.

Network Architecture
The project follows a hierarchical core–access model.

Access Routers:
- Student Router
- Faculty Router
- Admin Router

Core Router:
- Interconnects all access routers
- Directly connects all servers

Servers:
- Student FTP Server
- Faculty FTP Server
- Admin FTP Server
- DNS Server

IP Addressing Scheme

Department LANs:
Students LAN: 192.168.10.0/24 (Gateway: 192.168.10.1)
Faculty LAN: 192.168.20.0/24 (Gateway: 192.168.20.1)
Admin LAN: 192.168.30.0/24 (Gateway: 192.168.30.1)

Router-to-Router Links:
Student Router ↔ Core Router: 10.0.0.0
Faculty Router ↔ Core Router: 11.0.0.0
Admin Router ↔ Core Router: 12.0.0.0

Server Networks
Each server is connected to a separate FastEthernet interface on the core router and therefore uses a unique subnet.

Student FTP Server:
IP Address: 192.168.100.10
Gateway: 192.168.100.1

Faculty FTP Server:
IP Address: 192.168.200.10
Gateway: 192.168.200.1

Admin FTP Server:
IP Address: 192.168.150.10
Gateway: 192.168.150.1

DNS Server:
IP Address: 192.168.250.10
Gateway: 192.168.250.1

Routing Protocol
RIP version 2 is enabled on all routers with auto-summary disabled. RIP dynamically advertises all department LANs, router backbone networks, and server networks, allowing automatic route discovery and scalability.

FTP Server Configuration

Student FTP Server:
Users:
- 4 Student users
- 3 Faculty users
- 2 Admin users

Permissions:
- Students: Read and List access
- Faculty: Full access
- Admin: Full access

Faculty FTP Server:
Users:
- 3 Faculty users
- 2 Admin users

Permissions:
- Faculty: Full access
- Admin: Full access

Admin FTP Server:
Users:
- Admin users only

Permissions:
- Full administrative control

DNS Server Configuration
A dedicated DNS server is used to resolve FTP server names into IP addresses, enabling hostname-based access.

DNS Records:
student.ftp.local → 192.168.100.10
faculty.ftp.local → 192.168.200.10
admin.ftp.local → 192.168.150.10

All PCs are configured with the DNS server IP address to enable name resolution.

Testing and Verification
The following tests were successfully performed:
- ICMP ping between all LANs and servers
- FTP login from Student, Faculty, and Admin PCs
- File download and upload based on user roles
- DNS name resolution using ping and ftp commands
- Dynamic routing convergence using RIP

Key Concepts Demonstrated
- LAN segmentation
- Dynamic routing using RIP
- Core–access network design
- Client–server communication
- FTP protocol
- DNS name resolution
- Role-based access control
- Multi-router network architecture

Tools Used
- Cisco Packet Tracer
