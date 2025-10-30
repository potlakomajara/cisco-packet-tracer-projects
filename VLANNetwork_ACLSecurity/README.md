# VLAN configuration, Inter-VLAN Routing and ACL Security Policy Lab

• Overview:
  This project demonstrates how to design, segment, and secure a small enterprise network using Cisco Packet Tracer.
  The setup includes VLAN creation, inter-VLAN routing , static IP addressing, and ACL-based security policies.

# Phase 1: Building and Segmenting the Network
  
  Objectives
  
  Create VLANs for different departments
  
  Assign switch ports to VLANs
  
  Configure a trunk link between the switch and router
  
  Configuration Summary
  VLAN ID	VLAN Name	PC Ports	Gateway IP
  10	IT_Support	Fa0/2 – Fa0/3	192.168.10.1
  20	Sales	Fa0/4 – Fa0/5	192.168.20.1
  30	Guest	Fa0/6 – Fa0/7	192.168.30.1
  
  Switch Commands (CoreSwitch)
  enable
  configure terminal
  hostname CoreSwitch
  
  • Create VLANs
  vlan 10
   name IT_Support
  vlan 20
   name Sales
  vlan 30
   name Guest
  
  • Assign ports to VLANs
  interface range Fa0/2 - 3
   switchport mode access
   switchport access vlan 10
  
  interface range Fa0/4 - 5
   switchport mode access
   switchport access vlan 20
  
  interface range Fa0/6 - 7
   switchport mode access
   switchport access vlan 30
  
  • Configure trunk to router
  interface Fa0/1
   switchport mode trunk
  
  end
  copy running-config startup-config

# Phase 2: Router-on-a-Stick Configuration
  
  • Objectives
  
  Configure router sub-interfaces for inter-VLAN routing
  
  Assign IP addresses to each VLAN
  
  Enable connectivity between VLANs
  
  🖧 Router Commands (CoreRouter)
  enable
  configure terminal
  hostname CoreRouter
  
  • Enable main interface
  interface GigabitEthernet0/0
   no shutdown
  exit
  
  • VLAN 10 Gateway
    interface GigabitEthernet0/0.10
     encapsulation dot1Q 10
     ip address 192.168.10.1 255.255.255.0
    
  • VLAN 20 Gateway
    interface GigabitEthernet0/0.20
     encapsulation dot1Q 20
     ip address 192.168.20.1 255.255.255.0
  
  • VLAN 30 Gateway
    interface GigabitEthernet0/0.30
     encapsulation dot1Q 30
     ip address 192.168.30.1 255.255.255.0
  
  end
  copy running-config startup-config

• PC IP Configuration
  VLAN	PCs	Example IPs	Gateway
  10	PC1, PC2	192.168.10.11 / 192.168.10.12	192.168.10.1
  20	PC3, PC4	192.168.20.11 / 192.168.20.12	192.168.20.1
  30	PC5, PC6	192.168.30.11 / 192.168.30.12	192.168.30.1

• Verification:
  Ping across VLANs (to confirm inter-VLAN routing is working.

# Phase 3: Security Policy (ACL Implementation)
  Objective
  
  Block all traffic from the Guest VLAN (30) to the IT Support VLAN (10) while allowing all other communication.
  
  Router ACL Configuration
  configure terminal
  ip access-list standard BLOCK_GUEST_TO_IT
   deny 192.168.30.0 0.0.0.255
   permit any
  
  • Apply inbound on VLAN 10 sub-interface
  interface GigabitEthernet0/0.10
   ip access-group BLOCK_GUEST_TO_IT in
  end
  
  
  • Verification:
  
  Ping from VLAN 30 (Guest) → VLAN 10 (IT Support) should fail.
  
  Pings between VLAN 20 and VLAN 10 should succeed.
  
 # Key Learnings:
  
  VLAN segmentation improves network organization and security.
  
  Access Control Lists (ACLs) can enforce network security policies efficiently.
  
