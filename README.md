# Switchport-Security-Lab
This lab focuses on securing Layer 2 switching operations in a campus network. You’ll configure VLANs, VTP, DHCP, port security, and DHCP snooping to protect against common network threats while maintaining host connectivity.

**Devices Used:**
- Router (RA)
- Multi Layer Switch (MLS)
- Access Layer Switch (ALS)
- PC and VM Hosts

---
# Part 1 - Initial Setup & Verification
- Power on all nodes
- Verify no previous configurations are leftover on said nodes
- Configure hostnames for RA, MLS, and ALS using the format username-W12-DeviceName
- Complete basic configurations (console/vty timeouts, interface shutdowns), you can refer to basic config file
- Confirm conenctions between devices with *show cdp neighbors* in privilege exec mode
