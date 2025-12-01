# VirtualBox Network Settings
This file describes the network configuration used in VirtualBox to ensure both VMs could communicate.

---

## Network Mode Used
Both Kali Linux and Metasploitable2 were configured to use: Host-Only Adapter

This ensures:
- Both VMs are in the same Layer-2 broadcast domain  
- ARP scanning works correctly  
- ICMP ping operates without routing issues  
- Network is isolated from the internet for safety  

---

## Why Not NAT or Bridged?
- **NAT:** Places the VM behind VirtualBox internal NAT → ARP cannot cross NAT  
- **Bridged:** Connects VM to physical network → IP assignment depends on router/hotspot  
- **Mixed NAT + Bridged:** Puts the two VMs on different networks → no ARP or ping possible  

---

## Conclusion
Host-Only mode creates a controlled and isolated lab environment ideal for ARP scanning, ICMP analysis, and Wireshark packet capture.