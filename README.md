# Layer 2 Switch Security Lab 
This lab focuses on securing Layer 2 switching operations in a campus network. You’ll configure VLANs, VTP, DHCP, port security, and DHCP snooping to protect against common network threats while maintaining host connectivity.

**Devices Used**
- Router (RA)
- Multi Layer Switch (MLS)
- Layer 2 Switch (ALS)
- PCs and VMs simulating hosts

--- 
**NOTE**
This lab was done at Algonquin College, offered in the Routing and Switching course (CST8315) in the Computer Systems Technician - Networking course. I just found this lab really fun and intresting!

---
## Networking Topology

![Topology](Topology.jpg)


---

# Part 1 - Initial Setup
- [ ] Power on devices
- [ ] Verify no previous configs are on devices before continuing with the lab
- [ ] Do basic config (refer to Basic Confg)
- [ ] Verify neighboring connectiongs via: *show cdp neighbors* in privilege exec
Goal: Confirm all physical links and base configurations are working before moving forward.

--- 

# Part 2 - VLANS and VTP
- [ ] Set the VTP mode to transparent on ALL switches
- [ ] Create and name all VLANs on the topology
- [ ] On ALS, configure the access ports:
- VLAN 100 → Gi0/5–15 (PCs)
- VLAN 200 → Gi0/16–24 (VMs)
- [ ] Configure trunking between MLS and ALS and verify connectivity.
Goal: Ensure proper VLAN segmentation and inter-switch connectivity.

--- 

# Part 3 - Addressing and Routing 
- [ ] Enable routing on MLS
- [ ] Configure addressing for RA, MLS, and ALS interfaces
- [ ] Verify directly connected networks via ping and traceroute
- [ ] On RA:
- Add a default route via RemoteSw
- Add static routes for PC and VM networks
- [ ] On MLS:
- Add default route via RemoteSw
- [ ] Confirm all devices can reach the FTP server
Goal: Establish network layer connectivity between all segments.

--- 

# Part 4 - DHCP Server Configurations

On MLS (for VLAN 100 – PCs)
- [ ] Create DHCP pool VLAN-100
- [ ] Exclude used addresses
- [ ] Set gateway, DNS, domain name, and 6-hour lease
- [ ] Configure DHCP relay if broadcasts can’t reach the server

On RA (for VLAN 200 – VMs)
- [ ] Create DHCP pool VLAN-200
- [ ] Exclude used addresses
- [ ] Set gateway, DNS, domain name, and 1.5-day lease
- [ ] Configure DHCP relay if needed

Verify with:
- [ ] PCs and VMs get valid IPs and can reach www.8315.ca
- [ ] Use show ip dhcp binding to confirm leases
Goal: Provide automatic IP assignment for both VLANs.

--- 

# Part 5 - Port Security on ALS
- [ ] Disable CDP on edge ports to prevent information leakage
- [ ] Disable all unused ports
- [ ] Configure port security with the follow requirements:
- VLAN 100 ports (Gi0/5–15): max 2 MACs, restrict violations
- VLAN 200 ports (Gi0/16–24): max 3 MACs, shutdown on violation
- [ ] Enable sticky MAC learning
- [ ] Verify with show port-security
Goal: Prevent MAC flooding and unauthorized device access.

---
# Part 6 - DHCP Snooping
- [ ] Enable DHCP snooping globally and for VLANs 100 and 200
- [ ] Configure trusted ports toward DHCP servers (Po1 interface)
- [ ] Limit DHCP discover frames to 20 per second on edge ports
- [ ] Disable Option 82 insertion
- [ ] Verify bindings with show ip dhcp snooping binding
Goal: Protect against rogue DHCP servers and DHCP starvation attacks.

--- 
# Part 7 - Cleanup
- [ ] Erase startup configs and VLAN data from all devices
- [ ] Verify with:
- show startup-config
- show flash: | inc vlan.dat
- [ ] Neatly disconnect and store all cables before powering down equipment
Goal: Leave all lab gear in a default, ready state for the next class.
