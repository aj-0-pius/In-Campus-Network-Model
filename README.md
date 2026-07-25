🛡️ Zero-Trust Enterprise Campus Network Architecture

📌 About The Project

This project is a massive, highly detailed Enterprise Campus Network Simulation designed for Rajshahi Polytechnic Institute. Scaling across 9 distinct academic and administrative departments, the architecture abandons traditional flat networks in favor of a modern Zero-Trust Micro-segmentation model.

Due to the extreme detail, physical layout mapping, and sheer volume of configured devices, the simulation file exceeds GitHub's standard upload limits (29+ MB).

🚀 Download the Cisco Packet Tracer Simulation (.pkt) Here

🏗️ Architectural Overview

The network is built using the industry-standard Cisco Hierarchical Model (Core, Distribution, Access) to ensure high availability, scalability, and deterministic traffic flow.

Key Features & Technologies Implemented

Zero-Trust Security Perimeter: Heavy utilization of Extended Access Control Lists (ACLs) at the distribution layer to completely isolate departmental traffic.

The "Admin Mesh": A highly restricted, cross-campus logical mesh allowing designated IT Administrators global access while implicitly denying all lateral student/faculty traffic.

Hierarchical Subnetting: A meticulously calculated IPv4 scheme supporting over 50+ VLANs campus-wide without IP overlap.

Centralized Edge Services: Single-point NAT (Network Address Translation) and Edge Firewall routing for secure internet access.

Automated IP Management: Departmental servers handling localized DHCP scopes via ip helper-address forwarding.

Layer 2 Hardening: Campus-wide deployment of Port Security (Sticky MAC) and Spanning-Tree BPDU Guard to mitigate rogue access and broadcast storms.

Enterprise AAA & Telemetry: TACACS+ authentication for infrastructure hardware, backed by a dual-tier Syslog and NTP architecture.

🔒 Departmental Security Policy (Zero-Trust)

Each of the 9 departments (e.g., CST, EMT, Civil, Mechanical) is an independent, self-sufficient security zone.

Logical Entity

VLAN (EMT Example)

Subnet

Security Clearance

Local Server

VLAN 30

172.16.30.0/24

Hosts DHCP/AAA. Isolated from outside departments.

Admin PC

VLAN 31

172.16.31.0/24

God Mode: Full local access, global email, internet.

Teacher PCs

VLAN 32

172.16.32.0/24

Access to Server & Labs. Can email Admin. Blocked globally.

Student Lab 1

VLAN 33

172.16.33.0/24

DHCP enabled. Internet only. Blocked from lateral movement.

Student Lab 2

VLAN 34

172.16.34.0/24

DHCP enabled. Internet only. Blocked from lateral movement.

Traffic Flow Logic

To achieve true isolation, traffic routing is handled exclusively by Multilayer Distribution Switches (Cisco 3560) using dot1q trunking. All Inter-VLAN traffic is filtered through strict inbound ACLs before being routed. For instance, a Student PC in Lab 1 can reach 8.8.8.8 (Internet) but is cryptographically blocked from pinging the Teacher PC located just one room over.

🛠️ How to Explore the Simulation

If you download the .pkt file from the Google Drive link above, follow these steps to verify the network integrity:

Open in Cisco Packet Tracer (Version 8.0 or higher recommended).

Test DHCP: Open any Student PC in any department, switch IP Configuration to DHCP, and watch it successfully pull an IP from the local department server.

Test Isolation (Ping): Attempt to ping a Teacher PC from a Student PC. The ICMP request will be actively rejected by the Distribution Switch ACL.

Test Internet (NAT): Trace a packet from a Student PC to the external ISP Cloud to observe the Edge Router performing NAT overload.

Examine Configurations: Enter the CLI of any Distribution switch and run show access-lists or show running-config to view the complex security posture.

👨‍💻 Author

Minhajul Abadin Pius

Role: Network Architect / Security Engineer

Education: Diploma in Engineering (CST), 6th Semester, Rajshahi Polytechnic Institute

Contact/Links: [Insert your LinkedIn profile link here]
