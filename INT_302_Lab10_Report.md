# INT302 Lab 10: DNS and SMB Enumeration

## Overview
This report documents DNS querying and SMB enumeration to map a target network.

## DNS Enumeration
*   Used nslookup, host, and dig to query A, MX, and TXT records.
*   dig provided the most detailed technical output, while host was the cleanest.
*   MX records revealed mail servers; TXT records revealed email security policies.

## SMB Enumeration (enum4linux)
*   Ran enum4linux -a against a local target VM.
*   *Shares Found:* tmp, opt, print$.
*   *Users Found:* msfadmin, user, root.

## Analysis
Combining DNS (external view) and SMB (internal view) provides a complete map of the target. The discovered usernames are prime targets for brute-force attacks, and open shares could allow data theft.
