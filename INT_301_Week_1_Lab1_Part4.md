## Step 1: Check Current Permissions
Command: cd ~/Lab1
Command: ls -l

Output showed all files with permission strings starting with -rw- (default permissions for newly created files).

## Step 2: Create Permission Test Files
Command: touch secret_file.txt admin_tool.sh public_read.txt
All three files created with default permissions (-rw-r--r--).

## Step 3: Modify Permissions Using Symbolic Method

Command: chmod u+x admin_tool.sh
Effect: Added execute permission for the owner (user).
Before: -rw-r--r--
After:  -rwxr--r--

Command: chmod o-r secret_file.txt
Effect: Removed read permission for others (users who are not owner and not in group).
Before: -rw-r--r--
After:  -rw-r-----

Command: chmod a+w public_read.txt
Effect: Added write permission for all (user, group, others).
Before: -rw-r--r--
After:  -rw-rw-rw-

### Exercise 4.1 Answer
- chmod u+x admin_tool.sh: Added execute bit for the owner. The owner can now run this file as a program.
- chmod o-r secret_file.txt: Removed read permission for others. Users who are neither the owner nor in the group cannot read the file - useful for hiding sensitive data.
- chmod a+w public_read.txt: Added write permission for everyone. Any user can now modify this file - useful for shared scratch files but risky for important data.

## Step 4: Modify Permissions Using Octal Method

Command: chmod 755 admin_tool.sh
Effect: Set permissions to rwxr-xr-x (7=user rwx, 5=group rx, 5=others rx).

Command: chmod 600 secret_file.txt
Effect: Set permissions to rw------- (6=user rw, 0=group none, 0=others none).

### Final Verification (stat -c '%A %n' admin_tool.sh secret_file.txt public_read.txt)
Output:
-rwxrw-r--  admin_tool.sh
-rw-------  secret_file.txt
-rw-rw-rw-  public_read.txt

### Explanation of Octal Method
Each digit represents the sum of permissions for a category:
- 4 = read (r)
- 2 = write (w)
- 1 = execute (x)

Examples:
- 7 = 4+2+1 = rwx (full permissions)
- 6 = 4+2 = rw (read and write)
- 5 = 4+1 = rx (read and execute)
- 0 = no permissions

The octal method is faster when setting multiple bits at once. Common patterns:
- 755 = executables and directories
- 600 = private files (only owner can read/write)
- 644 = standard files (owner write, everyone read)
