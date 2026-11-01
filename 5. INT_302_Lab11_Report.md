# INT302 Lab 11: Anonymity Testing (Tor & Proxychains)

## Overview
This report documents using Tor and Proxychains to mask IP addresses during network requests.

## Configuration & Verification
*   Installed Tor and Proxychains. Verified the Tor service was running.
*   Configured /etc/proxychains4.conf with strict_chain and proxy_dns.
*   *Baseline IP:* Recorded real IP using curl https://httpbin.org/ip.
*   *Anonymity Test:* Ran proxychains curl https://httpbin.org/ip. The IP returned was a Tor exit node IP, completely different from the real IP, confirming successful masking.
*   *Browser Test:* Launched Firefox via Proxychains and verified the IP was masked on whatismyip.com.

## Limitations & Risks
*   *Speed:* Tor is very slow for active scanning (e.g., nmap).
*   *Exit Nodes:* Malicious exit nodes can intercept unencrypted HTTP traffic.
*   *DNS Leaks:* Misconfiguration can leak real DNS queries.
