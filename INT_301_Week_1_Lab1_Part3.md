# INT 301 Week 1 Lab 1 - Part 3: File Content Management

## Step 1: Create and View File Content
Commands:
echo "Important findings from network scan" > scan_report.txt
echo "Additional notes on vulnerabilities" >> scan_report.txt
cat scan_report.txt

Output:
Important findings from network scan
Additional notes on vulnerabilities

## Step 2: Compare File Differences
Commands:
echo "Version 1.0" > config_old.txt
echo "Version 2.0" > config_new.txt
diff config_old.txt config_new.txt

Output:
1c1
< Version 1.0
---
> Version 2.0

### Exercise 3.1 Answer
The diff command compares two files line by line. The output 1c1 means line 1 of the first file needs to be changed (the 'c' stands for change) to match line 1 of the second file. The < symbol shows content from the first file (config_old.txt) and > shows content from the second file (config_new.txt). This is useful in cybersecurity for spotting unauthorised configuration changes.

## Step 3: Search Within Files
Commands:
echo "ERROR: Authentication failed" >> logfile.txt
echo "SUCCESS: User logged in" >> logfile.txt
echo "ERROR: Connection timeout" >> logfile.txt
grep "ERROR" logfile.txt

Output:
ERROR: Authentication failed
ERROR: Connection timeout

## Exercise 3.2: Count ERROR Messages
Command: grep -c "ERROR" logfile.txt
Output: 2

There are 2 lines containing the word "ERROR" in logfile.txt.

## Step 4: View Partial File Content
Command: head -3 logfile.txt
Output:
ERROR: Authentication failed
SUCCESS: User logged in
ERROR: Connection timeout

Command: tail -2 logfile.txt
Output:
SUCCESS: User logged in
ERROR: Connection timeout

## Exercise 3.3: Show Only Lines 2-3
Command: head -3 logfile.txt | tail -2
Output:
SUCCESS: User logged in
ERROR: Connection timeout

Explanation: The pipe (|) sends the first 3 lines from head into tail, which then keeps the last 2 of those 3 lines. The result is lines 2 and 3 of the original file.
