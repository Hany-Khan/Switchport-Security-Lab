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
- Power on devices
- Verify no previous configs are on devices before continuing with the lab
- Do basic config (refer to Basic Confg)
- Verify neighboring connectiongs via: *show cdp neighbors* in privilege exec
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
- Enable routing on MLS
- Configure addressing for RA, MLS, and ALS interfaces
- Verify directly connected networks via ping and traceroute
- 
