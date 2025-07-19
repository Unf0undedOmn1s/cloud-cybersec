### *Critical Protocol Notes:

#### **BGP (Border Gateway Protocol)**
- **Function**: The "postal service" of the internet that routes traffic between autonomous systems (ASNs)
- **Manipulation Risks**:
  - **Route Hijacking**: Malicious AS announces false IP prefixes (e.g., 2018 Amazon Route 53 hijack)
  - **Prefix Spoofing**: Advertising routes not actually owned (e.g., 2022 Russian ISP hijacked CDN traffic)
  - **Mitigation**: 
    - RPKI (Resource Public Key Infrastructure) for route validation
    - BGPsec (RFC 8205) for cryptographic origin verification

#### **RPC (Remote Procedure Call)**
- **Function**: Allows programs to execute code on remote systems (common in microservices)
- **Security Issues**:
  - **Unauthenticated Calls**: Legacy RPC often lacks encryption (e.g., SunRPC vulnerabilities)
  - **Portmapper Exploits**: Uses random high ports (UDP/111) vulnerable to amplification attacks
  - **Modern Solutions**: gRPC with TLS 1.3 and auth tokens

#### **NetBIOS (Network Basic Input/Output System)**
- **Function**: Legacy Windows naming/service discovery (ports 137-139)
- **Exploits**:
  - **NBNS Spoofing**: Poisoning name resolution to intercept SMB traffic
  - **SMB Relay Attacks**: Using NetBIOS to pass-the-hash in AD environments
  - **Mitigation**: Disable NetBIOS over TCP/IP in modern networks

### Attack Examples:
1. **BGP**: 2021 Facebook outage (AS32934 withdrew routes)  
2. **RPC**: EternalBlue exploited Windows RPC (WannaCry ransomware)  
3. **NetBIOS**: Responder.py tool steals NTLM hashes via NetBIOS  
