# INT 301 Lab 4: Linux File Permissions and Ownership

## Part 1: Viewing File Permissions
- Created a new directory (PermissionTest) and navigated into it.
- Created a blank file (testfile.txt) using touch.
- Used ls -l to view the default permissions (-rw-r--r--), noting that the owner has read/write, while group and others have read-only.

## Part 2: Modifying Permissions
- Changed permissions to 777 (-rwxrwxrwx) using chmod 777 testfile.txt, granting full read, write, and execute access to everyone.
- Reverted permissions to 644 (-rw-r--r--) using chmod 644 testfile.txt to restore a secure default state.

*Exercise 1: Experiment with Permissions*
- Switched permissions back to 777 and verified using ls -l.

## Part 3: Changing Ownership
- Created a new test user (testuser) using sudo adduser.
- Changed the file owner and group to testuser using sudo chown testuser:testuser testfile.txt.
- Verified the ownership change with ls -l.

*Exercise 2: Group Ownership*
- Changed the group ownership to staff using sudo chgrp staff testfile.txt.
- Verified the change; the file was now owned by testuser:staff.

## Part 4: Practical Exercises
*Exercise 3: Create and Modify Permissions*
- Created three new files: file1.txt, file2.txt, and file3.txt.
- Set permissions:
  - file1.txt to 755 (Full for owner, read/execute for group/others).
  - file2.txt to 644 (Read/write for owner, read for group/others).
  - file3.txt to 777 (Full permissions for everyone).
- Verified all changes using ls -l.

*Exercise 4: Ownership Challenge*
- Created a directory named Project.
- Set the current user as the owner using sudo chown $USER:$USER Project.
- Verified ownership with ls -ld Project.

## Conclusion
This lab demonstrated the critical importance of Linux file permissions and ownership for system security. Mastering commands like chmod, chown, and chgrp is essential for managing access control in multi-user environments and preventing unauthorized access to sensitive data.
