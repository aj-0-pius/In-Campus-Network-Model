# 🛡️ Zero-Trust Enterprise Campus Network

A highly secure, multi-departmental campus network infrastructure designed for Rajshahi Polytechnic Institute using Cisco Packet Tracer.

## 🚀 Features

Zero-Trust Micro-segmentation: Strict Layer 3 Access Control Lists (ACLs) isolating 9 distinct departments.

The "Admin Mesh": God-mode access for department admins while strictly denying lateral movement for students and faculty.

Enterprise Edge Security: Centralized NAT (Network Address Translation) and firewall routing.

Automated IP Management: Localized DHCP scopes routed via ip helper-address to a secure internal server.

Layer 2 Hardening: Campus-wide deployment of Port Security (Sticky MAC) and Spanning-Tree BPDU Guard.

# 📥 Download & Installation

Due to the extreme detail and sheer volume of configured devices, the simulation file is 29+ MB and exceeds GitHub's standard upload limits.

💻 Usage

To explore and test the security policies of this network:

Open the downloaded file in Cisco Packet Tracer (Version 8.0 or higher recommended).

Test DHCP: Open any Student PC (e.g., in the EMT or CST department), navigate to IP Configuration, and verify it successfully pulls an IP from the local department server.

Test Security (Ping): Open the Command Prompt on a Student PC and attempt to ping a Teacher PC.

# The ICMP request will be actively rejected by the Distribution Switch ACL.
Reply from 172.16.x.1: Destination host unreachable.


Examine Configurations: Enter the CLI of any Distribution switch (3560) and run the following command to view the complex security posture:

Switch# show access-lists


# 🏗️ Departmental Security Policy

Each department is configured as an independent security zone. (Example: EMT Department)

| Entity | VLAN | Subnet | Security Clearance |
| :--- | :--- | :--- | :--- |
| **Local Server** | VLAN 30 | `172.16.30.0/24` | Hosts DHCP/AAA. Isolated globally. |
| **Admin PC** | VLAN 31 | `172.16.31.0/24` | Full local access, global email, internet. |
| **Teacher PCs** | VLAN 32 | `172.16.32.0/24` | Access to Server & Labs. Blocked globally. |
| **Student Labs** | VLAN 33/34 | `172.16.33.0/24` | Internet only. Blocked from lateral movement. |

# 🤝 Contributing

Contributions, issues, and feature requests are welcome!
Feel free to check the issues page.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

Prepared By: Minhajul Abadin Pius
(Diploma in Engineering, CST 6th Semester - Rajshahi Polytechnic Institute)
