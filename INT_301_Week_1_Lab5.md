# INT 301 Lab 5: Advanced Research Topics

## Part 1: Advanced Research Topics (Chosen Topics)

### Topic 1: Security-Focused Linux Distributions
*Comparison of Kali Linux, Parrot OS, BlackArch, and BackBox:*
*   *Kali Linux:* Debian-based, the industry standard for penetration testing. Includes over 600 pre-installed tools with a rolling update mechanism.
*   *Parrot OS:* Debian-based, lightweight. Focuses on both security testing and daily use. Uses rolling releases.
*   *BlackArch:* Arch Linux-based. Contains the largest repository of security tools (over 2800). Highly customizable but has a steep learning curve.
*   *BackBox:* Ubuntu-based. Designed for performance and minimalism, focusing on network and system security assessments.

*Use Cases:*
*   *Kali:* General penetration testing and red teaming.
*   *Parrot:* Red teaming, OSINT, and daily development.
*   *BlackArch:* Advanced users who need extreme customization.
*   *BackBox:* Lightweight security audits.

### Topic 2: Linux Kernel Security Mechanisms
*SELinux vs. AppArmor:*
*   *SELinux:* Developed by the NSA. Uses Mandatory Access Control (MAC) based on labels. Highly granular and secure but complex to configure.
*   *AppArmor:* Developed by Canonical. Uses path-based access control. Easier to configure than SELinux and is the default on Ubuntu, Debian, and Kali Linux.

*Kernel Hardening Features:*
*   *ASLR (Address Space Layout Randomization):* Randomizes memory locations to prevent buffer overflow attacks.
*   *Stack Protection:* Prevents stack smashing by placing a "canary" value on the stack.

---

## Part 2: Comprehensive Research Methodology

### Step 1: Multi-Source Research
- Checked current kernel security features on Kali: cat /proc/sys/kernel/randomize_va_space (returned 2, meaning full ASLR is enabled).
- aa-status confirmed AppArmor is active and enforcing.
- getenforce returned command not found, confirming SELinux is not installed.
- Used dpkg -l | grep -E "(security|scan|audit)" to analyze installed security tools.

### Step 2: Hands-On Investigation
- Counted installed packages: apt list --installed | wc -l returned over 1000 packages, confirming a heavy tool load.
- Checked update mechanisms using cat /etc/apt/sources.list and systemctl status apt-daily-upgrade.timer.
- Created a 10MB test file using dd if=/dev/zero of=test.img bs=1M count=10.
- Analyzed the file using strings test.img | head -20 and file test.img (forensic analysis).

---

## Part 3: Advanced Research Table

### Research Table 1: Technical Comparison

| Feature | Kali Linux | Parrot OS | BlackArch | Analysis |
| :--- | :--- | :--- | :--- | :--- |
| *Update Frequency* | Rolling Release | Rolling Release | Rolling Release | All provide the latest tools quickly. |
| *Default Hardening* | Moderate | High (AppArmor) | Moderate | Parrot is designed for privacy. |
| *Tool Collection Size* | ~600+ tools | ~600+ tools | 2800+ tools | BlackArch has the largest collection. |
| *Community Support* | Excellent | Very Good | Good | Kali has the largest community. |
| *Use Case Specificity* | Pentesting/Red Team | Pentesting/Dev | Advanced Pentesting | Kali is standard for industry. |
| *Performance Impact* | Heavy (VM) | Lightweight | Heavy | Parrot runs well on older hardware. |
| *Learning Curve* | Moderate | Moderate | Steep | BlackArch requires deep Linux knowledge. |

### Research Table 2: Security Implementation Analysis

| Security Mechanism | Implementation | Configuration Complexity | Effectiveness | Real-World Usage |
| :--- | :--- | :--- | :--- | :--- |
| *SELinux* | Mandatory Access Control (MAC) labels | High (Complex) | Very High | Default in RHEL/CentOS |
| *AppArmor* | Path-based access control | Low (Simple) | High | Default in Ubuntu/Kali |
| *ASLR* | Randomizes memory space | N/A (Kernel default) | High (Anti-exploit) | Enabled on all modern Linux |
| *Stack Protection* | Canary values in memory | N/A (Compiled) | High | Standard in GCC/Clang |

---

## Part 4: Practical Research Exercises

### Exercise 1: Security Tool Analysis (Nmap)
- *Primary use case:* Network discovery, port scanning, and service version detection.
- *Key features:* Host discovery, OS detection, stealth scanning, and vulnerability scripting.
- *Command syntax:* nmap -sS <target>
- *Output interpretation:* Shows open ports (e.g., 22/tcp open ssh) and the state of the ports (open, closed, filtered).
- *Common use:* Used by pentesters to map a target's attack surface before exploitation.

### Exercise 2: Kernel Security Research
- Ran sysctl -a | grep kernel to list active kernel parameters.
- Ran sudo dmesg | grep -i security to inspect the kernel log for security events.
- Note: These commands verified that security features (like ASLR) are active and logging critical system events.

---

## Part 5: Vulnerability Research Case Study

### Vulnerability Analysis: CVE-2021-4034 (PwnKit)

*Basic Information*
- *CVE ID*: CVE-2021-4034
- *CVSS Score*: 7.8 (High)
- *Affected Systems*: All major Linux distributions with policykit-1 installed.
- *Discovery Date*: Disclosed publicly on January 25, 2022 (by Qualys).

*Technical Details*
- *Vulnerability Type*: Local Privilege Escalation (Out-of-bounds read/write).
- *Affected Components*: pkexec (a SUID-root program part of the Polkit package).
- *Attack Vector*: Local.
- *Complexity*: Low (public exploits are widely available).

*Impact Analysis*
- *Confidentiality Impact*: High (Attacker gains root access).
- *Integrity Impact*: High (Attacker can modify system files).
- *Availability Impact*: High (Attacker can crash/disable the system).
- *Privilege Escalation*: Yes (gains root/SYSTEM privileges).

*Mitigation Strategies*
1. *Patch Availability*: Fixed in policykit-1 updates (Jan 2022).
2. *Workarounds*: Remove the SUID bit: sudo chmod 0755 /usr/bin/pkexec.
3. *Detection Methods*: Monitor for unusual pkexec executions in audit logs.
4. *Prevention Techniques*: Timely patch management and limiting local user access.

*Proof of Concept*
- *Example Exploit*: The exploit works by passing an empty argument vector and manipulating environment variables (like GCONV_PATH) to force pkexec to load a malicious shared object (.so file) as root.

---

## Part 6: Advanced Research Report

### Section 1: Executive Summary
*Research Objectives and Methodology:* 
The objective of this research was to analyze security-focused Linux distributions (Kali, Parrot, BlackArch) and investigate core Linux kernel security mechanisms (SELinux vs. AppArmor, ASLR). The methodology involved theoretical comparison, hands-on investigation of the local Kali environment using tools like sysctl and aa-status, and a case study of the CVE-2021-4034 (PwnKit) vulnerability.

*Key Findings and Conclusions:*
Kali Linux remains the industry standard due to its vast community support and default toolset. Parrot OS offers a lighter alternative. AppArmor (used in Kali/Ubuntu) provides a more user-friendly security model compared to SELinux (used in RHEL). Even with kernel hardening features Security like ASLR, critical vulnerabilities like PwnKit can still compromise a system if patching is delayed.

### Section 2: Technical Analysis
- *Kali vs. Parrot:* Both are Debian-based, but Kali is heavier while Parrot is optimized for older hardware.
- *SELinux vs. AppArmor:* SELinux provides granular MAC via security labels, making it highly secure**
 but difficult to configure. AppArmor uses- file paths, making it easier to deploy.
- * **Configuration Examples:* Enabling ASLR via /Actionetc/s:**ysctl.conf and enforcing least privilege using ` Enchmod` and chown.

### Section 3: Practicalforce Applications
- *Penetration Testers strong:* Rely on Kali or BlackArch to simulate attacks.
- *System Administrators:* Use AppArmor and strict file permissions to defend servers.
- *Incident Responders:* Use forensic commands (dd, strings) and log analysis to investigate breaches.

### Section 4: Future Research Directions
- Investigating container security (Docker/Kubernetes) and Linux kernel features like cgroups.
- Exploring eBPF (Extended Berkeley Packet Filter) for real-time kernel monitoring.
- Researching the security implications of running Linux on cloud infrastructure.

---

## Part 7: Research Validation Exercises

### Validation 1: Command Proficiency Test
Created and executed a bash script (security_hardening.sh) that implements security best practices based on the research.
- The script checks the ASLR status by reading /proc/sys/kernel/randomize_va_space.
- Output confirmed ASLR is enabled (2), providing kernel-level memory protection.

### Validation 2: Security Configuration Assessment
Assessed the system's security posture using the following commands:
- ss -tuln: Reviewed all open listening ports.
- sudo iptables -L: Checked active firewall rules.
- getenforce: Confirmed SELinux is not installed.
- cat /etc/passwd | grep -v nologin: Audited user accounts with active login shells.

---

## Challenge Research Project: Security Hardening Guide

1. System Updates & Patch Management*
- *Action:* Ensure the OS and all packages are up to date.
- *Validation Command:* sudo apt update && sudo apt upgrade -y

2. Kernel Hardening (ASLR)*
- *Action:* Ensure Address Space Layout Randomization is fully enabled.
- *Validation Command:* cat /proc/sys/kernel/randomize_va_space (Should output 2).

3. Mandatory Access Control (AppArmor)*
- *Action:* Enforce access controls to restrict what programs can do.
- *Validation Command:* sudo aa-status

4. Firewall Configuration*
- *Action:* Block all incoming traffic by default, except for explicitly allowed services.
- *Validation Command:* sudo ufw status verbose

**5. Account and Password password policies and lock unused accounts.
- *Validation Command:* cat /etc/passwd | grep -v nologin

*6. Secure SSH Configuration*
- *Action:* Prevent brute-force attacks by disabling root login and password authentication.
- *Validation Command:* sudo grep -E "^PermitRootLogin|^PasswordAuthentication" /etc/ssh/sshd_config
