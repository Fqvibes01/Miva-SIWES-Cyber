# INT302 Lab 7: Network Forensic Investigation

## Overview
This report details the forensic investigation of the BookWorld breach PCAP file using Wireshark.

## Key Findings
*   *Initial Access:* Identified a SQL Injection vulnerability in the web application login portal (/login.php).
*   *Exploitation:* The attacker used malicious HTTP POST requests to bypass authentication and interact with the backend database.
*   *Data Exfiltration:* Utilized Wireshark's Conversations statistics to identify a massive outbound data transfer to an external IP, indicating data theft.

## Attack Timeline
1.  *Reconnaissance:* Scanned the web application for vulnerabilities.
2.  *Exploitation:* Injected SQL payloads into the login form.
3.  *Exfiltration:* Downloaded sensitive customer data.

## Recommendations
*   Implement a Web Application Firewall (WAF).
*   Use parameterized queries to prevent SQL Injection.
*   Monitor outbound traffic for abnormal data spikes.
