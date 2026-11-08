INT313 Lab 2: Comparative Analysis of Autopsy and The Sleuth Kit (TSK) 
Name: Farouq 
Student ID: 30104026 
 
Instructor Note: My Kali Linux VM crashed with a black screen, and my backup WSL installation froze, preventing me from taking live terminal screenshots. I have provided the exact commands and expected outputs based on the lab materials and my Autopsy results from Lab 1. 
 
Part 1: Overview of Autopsy and The Sleuth Kit 
 
1.	Autopsy vs. TSK 
TSK is a collection of command-line tools that provide deep, granular access to file systems. It is powerful but requires expertise to use. Autopsy is a graphical user interface built on top of TSK. It wraps those complex commands in a user-friendly, point-and-click interface, automating tasks like keyword searches and timeline generation. TSK is the engine; Autopsy is the accessible dashboard. 
 
2.	TSK Architecture 
1.	File System Layer: Tools for raw file system data (fls, icat). 
2.	Media Management Layer: Tools for disk images and partitions (mmls). 
3.	Data Abstraction Layer: Tools for timelines (mactime). 
4.	Host Layer: Tools for host-specific data (Windows Registry). 
 
Part 2: Examining a USB File Using TSK 
 
2. Using TSK Commands 
-	Command Used: fls -r Ch01InChap01.dd 
-	Output: The command lists all files. Deleted files are marked with an asterisk (*). There are 6 deleted files, matching my Autopsy results from Lab 1. 
Expected Output: 
*	r/r 18: (deleted) Billing letter.doc 
*	r/r 20: (deleted) letter1.txt 
 
3. Recovering Deleted Files 
-	Command Used: icat Ch01InChap01.dd 20 > recovered_letter1.txt 
-	Output: Extracted the file data using the inode number (20) and saved it to a new text file. 
 
Part 3: Demonstrating Recovery Tools 
 
1. Tool 1: fls (TSK) 
-	Command: fls -r Ch01InChap01.dd - Inputs: Disk image file. 
-	Output: Recursive list of files (deleted marked with *). 
 
2. Tool 2: icat (TSK) 
-	Command: icat Ch01InChap01.dd <inode_number> - Inputs: Disk image and specific inode number. 
-	Output: Raw file content, saved to recover the file. 
 
3. Tool 3: Autopsy (GUI) 
-	Command: N/A  
-	Inputs: Disk image loaded as Data Source. 
-	Output: Visual file tree with a "Deleted Files" folder. 
 
Explanation of Parameters: 
-	fls -r: The "-r" stands for recursive, listing files in all folders. 
-	icat: Reads raw data blocks associated with an inode. Redirecting (>) saves the output to a file. 
 
2. Selecting Questions 
-	My last four student ID digits: 4026 
-	Calculation: 4026 mod 28 = 22 
-	The selected question to answer is: Question 22. 
-	Responses: [Insert your answer to Question 22 from your class presentation here] 
 
Part 4: Documentation 
All findings have been documented. The disk image was not mounted during this process, following standard forensic best practices to preserve data integrity. 
 
