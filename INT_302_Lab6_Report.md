# INT302 Lab 6: Advanced Packet Analysis

## 1. TCP Analysis
*   *SYN/ACK Flags:* SYN initiates a connection; ACK acknowledges it. The 3-way handshake (SYN, SYN-ACK, ACK) establishes a reliable connection.

## 2. HTTP & DNS Analysis
*   *HTTP:* Captured a GET request with a 200 OK response. The User-Agent header revealed the browser type. This showed a successful web transaction.
*   *DNS:* The query asks for a domain; the response provides the mapped IP address in the Answer section.

## 3. Custom Filters & Port Filtering
*   *Custom Filter:* Used tcp and ip.src == <My_IP> and ip.dst == <Target_IP> to isolate traffic to a specific host.
*   *Port Filter:* Used tcp.port == 80 to view only unencrypted HTTP traffic.

## 4. Vulnerability & SSL Analysis
*   *Vulnerability:* Found unencrypted HTTP traffic transmitting data in plain text. *Remediation:* Enforce HTTPS.
*   *SSL/TLS:* The handshake exchanges certificates and cipher suites to encrypt data, making the payload unreadable to attackers.

## 5. Final Security Assessment
*   *Findings:* Most traffic was securely encrypted (HTTPS), but some unencrypted HTTP traffic was present.
*   *Recommendations:* Enforce HTTPS network-wide, implement HSTS headers, and monitor for unusual traffic patterns (like SYN floods).
