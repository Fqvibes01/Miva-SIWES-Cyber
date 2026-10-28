## Part 5: Search and Find Operations
- Used find to locate .txt files and specific names (scan*).
- Used -type f and -type d to distinguish between files and directories.
- Used -size to find files based on their size.
- Used -exec to find all .sh files and automatically make them executable.

## Part 6: Text Processing Challenges
- Created a file (fruits.txt) and used sort to arrange it alphabetically.
- Used sort | uniq to remove duplicate entries.
- Used wc and wc -l to count words and lines in files.

## Part 7: Compression and Archiving
- Used tar -czf to create a compressed backup archive of the Lab1 directory.
- Used tar -tzf to list the contents without extracting.
- Extracted the archive into a new directory using tar -xzf.

## Part 8: System Monitoring
- Used ps aux and ps -ef | grep kali to monitor running processes.
- Used df -h and du -sh to check overall disk space and the size of the Lab1 directory.
- Used uname -a and whoami to check system information.

## Challenge Exercises
*Challenge 1: Directory Structure*
Created the Engagement_2024 folder with subdirectories for reconnaissance, exploitation, reporting, and evidence (with screenshots, logs, and packets inside evidence). Created readme.txt files in each main directory.

*Challenge 2: Permission Scheme*
- Applied 700 to .sh files (executable only by owner).
- Applied 644 to .txt files (readable by everyone, writable only by owner).
- Applied 000 to a secret file (no access to anyone).

*Challenge 3: Command Line Tools*
- Used find to locate all .log files.
- Used grep -c "ERROR" to count error lines in the log file.
- Saved the results to error_report.txt using output redirection (>).
