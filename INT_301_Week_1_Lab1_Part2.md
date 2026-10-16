# INT 301 Week 1 Lab 1 - Part 2: Comprehensive File Operations

## Step 1: Create multiple practice files
Command: touch scan_results.txt passlist.txt logfile.log config.conf secret.key data.xml

Files created:
config.conf  data.xml  logfile.log  passlist.txt  scan_results.txt  secret.key

## Step 2: Copy with verification
Command 1: cp scan_results.txt scan_results_backup.txt
Command 2: cp passlist.txt ../passlist_backup.txt

### Exercise 2.1 Verification
ls output (in Lab1):
config.conf  data.xml  evidence  exploits  logfile.log  logs  passlist.txt  recon  scan_results_backup.txt  scan_results.txt  secret.key

ls .. output (parent folder):
Lab1  MIVA-SIWES-Cyber  passlist_backup.txt

Both copies confirmed successful.

## Step 3: Move and rename files
Command 1: mv config.conf exploits/
Command 2: mv logfile.log logs/application.log

### Exercise 2.2 Verification
ls exploits/ output:
config.conf

ls logs/ output:
application.log

Final ls of Lab1 (config.conf and logfile.log are gone - they were moved):
data.xml  evidence  exploits  logs  passlist.txt  recon  scan_results_backup.txt  scan_results.txt  secret.key
