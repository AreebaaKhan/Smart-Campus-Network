# Smart-Campus-Network
This project demonstrates the design and implementation of a Smart Campus Network using Cisco Packet Tracer. It simulates a real-world university campus network with multiple departments, secure inter-VLAN communication, internet access using NAT, and firewall rules using ACLs.

🎯 Project Objectives

Design a scalable campus network using VLANs

Implement inter-VLAN routing using Router-on-a-Stick

Simulate internet access via an ISP router

Configure NAT (Static, Dynamic, PAT)

Apply firewall rules using Access Control Lists (ACLs)

Ensure controlled communication between departments

Build a demonstration-ready network topology

🏗 Network Architecture
VLANs Used
VLAN	Department	Network
10	Admin	192.168.10.0/24
20	Faculty	192.168.20.0/24
30	Students	192.168.30.0/24
40	Labs	192.168.40.0/24
50	Library	192.168.50.0/24

Each VLAN contains:

End-user PCs

A departmental web server (internal)

🌐 Internet Simulation

An ISP router is used to simulate the internet.
External services include:

🌍 External Web Server

📧 External Email Server

Campus users access these services through NAT.

🔄 NAT Configuration

The campus router is configured with all three NAT types:

✔ Static NAT

Used for internal servers

Maps private IPs to fixed public IPs

✔ Dynamic NAT

Used for Faculty VLAN

Maps private IPs to a pool of public IPs

✔ PAT (Overload)

Used by all remaining internal users

Multiple private IPs share one public IP using port numbers

🔐 Firewall & Security (ACLs)

Firewall rules are implemented using Extended ACLs applied in the outbound direction.

Communication Rules Summary

✔ Admin → All VLANs (Allowed)

❌ Faculty → Admin (Blocked)

❌ Students → Admin / Faculty / Labs (Blocked)

❌ Labs → Admin / Faculty / Students (Blocked)

✔ Everyone → Library (Allowed)

❌ Library → Internal VLANs (Blocked)

✔ Library → External Internet (Allowed)

✔ Campus Web Server → Accessible to all

This simulates realistic access control policies found in enterprise networks.

🧪 How to Test & Verify
1️⃣ VLAN Connectivity

Ping PCs within the same VLAN

Ping default gateway of each VLAN

2️⃣ Inter-VLAN Routing

Test allowed VLAN-to-VLAN communication

Verify blocked traffic using ping failures

3️⃣ NAT Verification

On Campus Router:

show ip nat translations
show ip nat statistics


From PCs:

ping external server IP

4️⃣ Firewall Verification

Test allowed & blocked pings as per rules

Observe Destination Host Unreachable vs Request Timed Out

🛠 Tools Used

Cisco Packet Tracer

Cisco Routers & Switches

Static & Dynamic IP addressing

VLANs, Trunking, Sub-interfaces

NAT & ACLs
