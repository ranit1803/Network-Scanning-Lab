# ARP Analysis (Netdiscover Scan)

## Objective
To discover all the active hosts in the local network using ARP scanning and analyze ARP traffic using Wireshark

---

## Why ARP Scan?
-> Address Resolution Protocol works at **Layer 2 (Data Link Layer)**.
-> It maps IP Addresses to MAC Addressess inside a Local Network
-> ARP Scan is useful because:
    - Works even if the ICMP ping is blocked
    - Finds all the machine in the local network
    - It's faster
    - Used for basic network reconnaissance

---

## Netdiscover Result Explanation

### Host 1 -> <gateway-ip>
-> This is the VirtualBox Host-Only Gateway
-> Vendor showing "Unknown" is normal

### Host 2 -> <target-ip>
-> This is "Metasploitable2 VM"
-> MAC vendor: PCS Systemtechnik GmbH, this is the vendor of VirtualBox virtual NIC

### Host 3 -> <kali-ip>
-> This is "Kali Linux VM"
-> Same Vendor

---

## Wireshark ARP Packet Analysis

### ARP Request (Broadcast)
This is sent to: ff:ff:ff:ff:ff:ff (broadcast MAC)

### ARP Reply (Unicast)
<target-ip> is at <target-mac>

This shows that:
    - Kali Broadcasted an ARP request
    - Metasploitable replied with its MAC
    - Devices are communicating at Layer 2
    - Both hosts exist inside the same LAN

---

## Conclusion
* All hosts in the LAN responded to ARP requests.
* Both VMs are confirmed to be active in the same domain
* ARP scan successfully identified the gateway as well as both the machines.