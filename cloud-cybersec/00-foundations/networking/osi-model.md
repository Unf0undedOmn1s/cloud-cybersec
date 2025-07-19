### OSI Model (Open Systems Interconnection)
## Layer 1: Pysical Layer
- Function: Transmite raw bits (0,1) over cables, WiFi, Fiber.
- Devices: Hubs, Repeaters, Cables (Ethernet, etc.)
- Security Risks: 
    - Cable tapping (Physical Interception)
    - Electromagnetic Interference (EMI)

## Layer 2: Data Link Layer
- Function: 
    - MAC Addressing
    - Switching (Forwarding frames within a LAN) 
    - VLAN (Logical Network Segmentation)
- Protocols: Ethernet (IEEE 802.3), WiFi (IEEE 802.11)
- Security Risks:
    - MAC Spoofing (Attacker impersonating another device)
    - ARP Poisoning (Redirects traffic to attacker)

## Layer 3: Network Layer
- Function:
    - IP Addressing (192.168.1.1)
    - Routing (Moves packets between networks by finding the best route)
- Protocols: IP, ICMP (Ping), BGP (Routing)
- Security Risks:
    - IP Spoofing (Fake source IP in DDoS Attacks)
    - Route hijacking (BGP Manipulation)*

## Layer 4: Transport Layer
- Function:
    - TCP (Reliable, connection-oriented)
    - UDP (Fast, connectionless)
    - Port Numbers (HTTP=80, HTTPS=443)

## Layer 5: Session Layer
- Function: Manages connections (setup, maintanance, teardown)
- Examples:
    - RPC (remote Procedure Call)*
    - NetBIOS (Windows file sharing)*
- Security Risks:
    - Session hijacking (Stealing active sessions)

## Layer 6: Presentation Layer
- Function:
    - Encryption (SSL/TLS)
    - Compression (gzip)
    - Data Formatting (JSON,XML)
- Security Risks:
    - SSL Stripping (Downgrade HTTPS-> HTTP)*

## Layer 7: Application Layer
- Function: User-Interface protocols (HTTP, FTP, SFTP, DNS, SMTP)
- Security Risks:
    - SQL Injection (Layer 7 web attack)
    - Phishing (Fake login pages)
