# INT 301 Week 1 Lab 1

## Exercise 1.1
Question: What is the difference between cd ~ and cd /home/kali?

Answer: cd ~ expands to the current user's home directory (/home/farouq). It is portable across usernames. cd /home/kali is a hardcoded absolute path that only works if the username is exactly kali.

## Exercise 1.2
Command used:
mkdir -p Lab1/{recon/{hosts,services},exploits,logs,evidence/{screenshots,packets}}

Verification (from tree Lab1):
Lab1
├── evidence
│   ├── packets
│   └── screenshots
├── exploits
├── logs
└── recon
    ├── hosts
    └── services

9 directories, 0 files.

## Step 3 Verification
cd Lab1/recon/hosts -> pwd: /home/farouq/Lab1/recon/hosts
cd ../../evidence/packets -> pwd: /home/farouq/Lab1/evidence/packets
