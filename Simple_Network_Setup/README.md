Simple Network Setup - Cisco Packet Tracer

This project demonstrates how to build and configure a simple home network using Cisco Packet Tracer.  
It covers both wired and wireless connectivity, DHCP configuration, and basic network testing through ping and web access.

---

• Objectives

- Build a basic network topology in the Logical Workspace  
- Configure end devices (PC and Laptop)  
- Verify connectivity using IP configuration and ping tests  

---

Part 1: Build a Simple Network

In this part, a PC, Laptop, Cable Modem, and a Wireless Router were deployed in the Logical Workspace.

• Steps Completed

1. Added devices to the workspace
   - PC, Laptop, and Cable Modem were added using the Device-Type Selection Box.
   - The Cable Modem connects to an ISP through a coaxial cable and converts it into an Ethernet connection.

2. Renamed devices
   - Each device was renamed for clarity (PC, Laptop, Cable Modem).

3. Connected devices
   - PC connected to the Wireless Router via copper straight-through cable.
   - Wireless Router connected to the Cable Modem via copper straight-through cable.
   - Cable Modem connected to the Internet using a coaxial cable.

---

Part 2: Configure End Devices and Verify Connectivity

• PC Configuration
  - Verified DHCP was enabled under Desktop > IP Configuration.
  - Confirmed the PC received an IPv4 address in the '192.168.0.x' range.
  - Used the command 'ipconfig /all' to review assigned IP details.
  - Tested network connectivity with 'ping cisco.srv' all replies received successfully.

• Laptop Configuration
  - Replaced the wired Ethernet module with a Wireless WPC300N module.
  - Connected to the wireless network HomeNetwork via Desktop > PC Wireless.
  - Verified connection by accessing 'cisco.srv' through the web browser.

---

• Skills Demonstrated
  - Network topology design  
  - Device naming and configuration  
  - DHCP configuration and testing  
  - Wireless connectivity setup  
  - Network troubleshooting using ping commands  

---

• Tools Used
  - Cisco Packet Tracer  
  - Logical Workspace  
  - DHCP and IP configuration tools  

---

• Notes:
  This lab was completed as part of my Cisco Networking Academy studies to reinforce practical networking concepts such as device connectivity, DHCP, and end-device configuration.
