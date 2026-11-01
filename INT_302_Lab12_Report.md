# INT302 Lab 12: Password Cracking with John the Ripper

## Overview
This report documents cracking password hashes using John the Ripper (JtR).

## Cracking Techniques
*   *Dictionary Attack:* Used rockyou.txt to instantly crack weak passwords (e.g., password).
*   *Custom Wordlist:* Created a list with admin123 and successfully cracked the hash.
*   *Brute Force:* Used --incremental to crack a short password.
*   *Windows (NTLM):* Used --format=nt to crack a Windows hash.
*   *Rules:* Used --rules to crack Password123 by mutating the base word "password" from the wordlist.

## Analysis
Dictionary and rule-based attacks are extremely effective because users often use common words with predictable modifications (like adding "123" at the end). 

## Recommendations
*   Enforce long passphrases (12+ characters).
*   Use strong hashing algorithms (bcrypt, Argon2) and salting.
*   Implement Multi-Factor Authentication (MFA).
