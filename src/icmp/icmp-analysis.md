# ICMP Analysis

## Objective
To verify host reachability at Layer 3 using ICMP ping and analyze Echo Request/Reply packets in Wireshark.

---

## Why ICMP?
After discovering hosts with ARP, ICMP is used to check whether a device is actively responding at the network layer.

Ping helps validate:
- Host availability  
- Round-trip time  
- TTL (used to estimate OS type)  
- Packet loss  

---

## Ping Summary
A ping scan was executed from the attacker machine to `<target-ip>`.  
All packets were successfully returned with:

- 0% packet loss  
- TTL value of 64 (typical for Linux-based targets)  
- Matching sequence numbers in each reply  

This confirms the target was reachable and responsive at Layer 3.

---

