# INT 301 Lab 2: Advanced APT Operations & Package Management

## Part 1: Advanced APT Operations
*Exercise 1.1: Difference between apt upgrade and apt full-upgrade*
- apt upgrade installs the newest versions of packages but will never remove existing packages. If an update requires a package removal, it holds it back.
- apt full-upgrade can remove packages if necessary to complete the upgrade, better handling changing dependencies.

*Exercise 1.2: Dependencies*
- Nmap dependencies include: libc6, libgcc-s1, liblinear4, liblua5.4-0, libpcap0.8t64.
- Packages depending on python3 include hundreds of tools (as shown in apt-cache rdepends python3).

*Exercise 1.3: Password Cracking Tools*
Tools available in Kali repositories: john (John the Ripper), hashcat, and hydra.

## Part 2: Advanced Installation Techniques
*Exercise 2.1: Python3 version and holding packages*
- The available and installed version of python3 is 3.14.7-3.
- Holding a package (apt-mark hold) locks it at its current version, preventing automatic updates.

*Exercise 2.2: Downloading and installing local DEB*
- Downloaded htop using apt download htop.
- Installed using sudo dpkg -i htop*.deb.
- If dependencies are missing, dpkg throws an error. You fix this by running sudo apt install -f (fix-broken), which downloads the missing dependencies.

## Part 3: Dependency Management and Troubleshooting
- Ran apt install -s metasploit-framework to simulate an install.
- Note: apt check returned an invalid operation error. (Fixed by using apt-get check instead).
- Ran sudo apt --fix-broken install to resolve any potential broken packages.

*Exercise 3.1: Difference between remove and purge*
- remove uninstalls the software but leaves configuration files behind.
- purge uninstalls the software and deletes all configuration files.
- You use remove if you plan to reinstall later and keep settings. You use purge to completely wipe the software from the system.

## Part 4: Repository Management
- Created a pinning file at /etc/apt/preferences.d/custom-pinning.
- Set Kali repository priority to 900 and Debian to 100.

*Exercise 4.1: Why pin packages?*
Pinning ensures the system prioritizes updates from a trusted repository (like Kali) over others. It prevents accidentally pulling in unstable versions from lower-priority repositories, maintaining system stability.

## Part 5: Alternative Package Managers
*Snap:*
- Installed snapd using apt.
- Note: On Kali Linux, snapd requires manual activation using sudo systemctl enable --now snapd apparmor before it can communicate with the store.
- Successfully installed hello-world using sudo snap install hello-world.

*Flatpak:*
- Installed flatpak using apt.
- Added the Flathub repository using flatpak remote-add.

*Exercise 5.1: Installation Locations*
- *APT:* Installs system-wide in /usr/bin, /usr/sbin, and configurations in /etc.
- *Snap:* Installs in /snap/ (isolated from the system).
- *Flatpak:* Installs in /var/lib/flatpak/ (system) or ~/.local/share/flatpak/ (user).

## Part 6: Source Compilation and Installation
*Step 1: Compile from Source*
- Cloned the ffuf repository from GitHub.
- Note: Go language was not installed by default. Installed it using sudo apt install golang-go.
- Successfully compiled the tool using go build and copied it to /usr/local/bin/ for global access.

*Step 2: Create DEB Packages*
- Installed packaging tools (dh-make, devscripts).
- Created a test directory and a sample script (myscript.sh).
- Generated the Debian packaging structure using dh_make.
- Successfully built the .deb package using dpkg-buildpackage -us -uc.

*Exercise 6.1: Compiling from Source vs Package Managers*
- *Advantages of Source:* Latest software version, customizable build, ability to audit code.
- *Disadvantages of Source:* Time-consuming, manual dependency management, no automatic updates.
- *Advantages of Package Managers:* Fast, automatic dependency resolution, easy updates/removals, security patches.
- *Disadvantages of Package Managers:* Software versions might be older, reliance on repository maintainers.

## Part 7: Advanced Troubleshooting Scenarios
*Step 1: Dependency Hell Resolution*
- Simulated installing kali-linux-default (required over 10GB of space).
- Used aptitude to see alternative dependency resolutions for the large package.

*Step 2: Package Forensic Analysis*
- Downloaded the Nmap .deb package.
- Used dpkg -c to view package contents without installing.
- Used dpkg -x to extract the package contents to /tmp/nmap-extract/.
- Note: dpkg --verify nmap returned an error because the package was downloaded but not actually installed on the system (expected in this environment).

## Part 8: Automation and Scripting
*Step 1: Bulk Package Operations*
- Created a list of tools in tools.txt.
- Used xargs to read the file and install multiple packages simultaneously.
- Exported the full list of installed system packages to installed_packages.txt using dpkg --get-selections.

*Step 2: System Setup Script*
- Created an automated bash script (setup_tools.sh) to install essential cybersecurity tools.
- Made the script executable using chmod +x.
- Note: While preparing to execute the script, the Kali Linux VM experienced a system crash (soft lockup) due to resource constraints. The script was successfully created and validated.
