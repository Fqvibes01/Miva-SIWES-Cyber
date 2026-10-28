# INT 301 Week 2: Bash Scripting & Automation

## Part 1: Absolute Basics - Your First Script
- Created first_script.sh with the #!/bin/bash shebang.
- Used the echo command to output text to the terminal.
- *Exercise 1.1:* Modified the script to print my name and today's date using the $(date) command.

## Part 2: Variables - Storing Information
- Created variables.sh to store text and numbers in variables (e.g., name="John", age=25).
- Used variables in echo commands by prefixing them with a $ (e.g., $greeting, $name).

## Part 3: Making Decisions - If Statements
- Created decisions.sh to check if a user-inputted number is greater than 10.
- Used comparison operators like -gt (greater than) and the if-then-else-fi structure.

## Part 4: Repeating Tasks - Loops
- Created loops.sh to demonstrate a for loop iterating through numbers (1 to 5) and a list of names (Alice, Bob, Charlie).
- Created while_loops.sh to count from 1 to 5 using a while loop.
- *Exercise 4.1:* Created blastoff.sh to count down from 10 to 1 using a while loop with the -ge operator, ending with the message "Blast off!".

## Part 5: Organizing Code - Functions
- Created functions.sh to group code into reusable blocks.
- Created a function greet_user that accepts a name as an argument ($1) and prints a greeting.
- Created a function introduce that accepts multiple arguments ($1, $2, $3) to print Name, Age, and City.

## Part 6: Your First Real Project - Simple Calculator
- Used nano to write a complete calculator script.
- Implemented a while true loop to keep the calculator running until the user chooses to exit.
- Used functions (show_menu and get_numbers) and a case statement to handle addition, subtraction, multiplication, and division.

## Part 7: Intermediate Project - File Organizer
- Wrote a script (organizer.sh) to automatically organize files into specific directories based on their file extensions.
- Created a test environment with dummy files (.docx, .jpg, .mp3, .mp4, .xyz).
- Used a for loop to iterate through all files, an if statement to verify they are files, and a case statement to match extensions.
- The script successfully moved files into Documents, Images, Music, Videos, and Others folders.

## Part 8: Advanced Beginner - System Monitor
- Created sysmon.sh to group system commands into a clean report.
- *Exercise 8.1:* Added a show_connections function that runs ss -tuln to display active network connections.
- The script displays current user, hostname, uptime, disk space (df -h), and memory usage (free -h).

## Part 9: Security Project - Simple Port Scanner
- Created portscanner.sh to scan common ports on a target IP (e.g., 127.0.0.1).
- Used Bash's built-in /dev/tcp/$host/$port feature combined with timeout 1 to check if ports 21, 22, 80, 443, etc., are open or closed.

## Part 10: Advanced Project - Automated Backup System
- Created backup.sh to archive a specific directory into a timestamped .tar.gz file.
- *Exercise 10.1:* Added a cleanup_old_backups function that uses the find command (find ~/backups -type f -mtime +7 -exec rm {} \;) to automatically delete backups older than 7 days.

## Part 11: Final Master Project - Complete Security Scanner
- Built master_scanner.sh, an all-in-one tool that combines everything learned:
  1. Cleans up old backups (cleanup_old_backups).
  2. Performs network discovery by getting the local IP and running a ping sweep across the local subnet (network_discovery).
  3. Scans for open local ports (vulnerability_scan).
  4. Logs all output to a timestamped .log file using tee for real-time logging (log function).
- *Exercise 11.1 (Conceptual):* To add email notifications, we would use a tool like mail or sendmail. We would modify the scan_port function to append open critical ports to a file and trigger an email if the file is not empty.

## Part 12: Practice Exercises
### Easy Exercise 1: Greeting Script
Created greeting.sh. The script asks the user for their name, checks the current time using date +%H, and uses if/elif/else statements to output "Good morning", "Good afternoon", or "Good evening".

### Medium Exercise 1: Password Generator
Created passgen.sh. The script asks for a desired password length, uses /dev/urandom with tr to filter alphanumeric and special characters, and fold to generate a secure random password of the requested length.
