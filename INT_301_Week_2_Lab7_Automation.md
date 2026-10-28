# INT 301 Week 2 - Lab 7: Automating Linux Command Shell Navigation & File Management

## Part 1: Intelligent Navigation System (smart_navigator.sh)
- Created a navigation logger that records every directory change with a timestamp into navigation_history.txt.
- Created the smart_cd function, which safely checks if a directory exists before attempting to cd into it.
- Created the show_history function to display the last 10 navigations using tail.
- Tested the system successfully.

## Part 2: Robust File Operations (file_manager.sh)
- Created the create_secure_file function to safely create files, automatically generating directory structures and verifying permissions (644 default).
- Created the safe_move function, which creates a timestamped backup of the destination file before overwriting it.
- Tested the backup functionality successfully.

## Part 3: Interactive Menu System (automation_dashboard.sh)
- Built an interactive menu that ties the previous scripts together.
- Created functions for show_main_menu, handle_menu_selection, and helper sub-menus (smart_navigation_menu, file_creation_menu).
- Added error checking to ensure the sourced scripts are available before running.
- Successfully tested creating files and checking system info through the menu interface.

## Part 4: Advanced Exercises

### Exercise 4.1: Automated Backup System (auto_backup.sh)
- Created a backup function that:
  1. Checks if the source directory exists.
  2. Creates the backup directory if needed.
  3. Creates a timestamped .tar.gz backup.
  4. Verifies the backup file integrity.
  5. Rotates backups, keeping only the newest 5 files.

### Exercise 4.2: System Health Monitor (health_monitor.sh)
- Created a script that checks disk space (alerts if >80%), monitors memory usage, and verifies if the SSH service is running using systemctl.

### Exercise 4.3: Log File Analyzer (log_analyzer.sh)
- Created a script that analyzes /var/log/syslog for ERRORs and WARNINGs, generates a summary report, simulates sending an email, and archives the log file using tar.
