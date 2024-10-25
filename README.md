# Secure Ubuntu 22.04 LTS Script for CyberPatriot

This repository contains a Bash script designed to secure an Ubuntu 22.04 LTS system, primarily aimed at use in CyberPatriot competitions. The script includes steps to disable unnecessary services, configure firewalls, enhance password policies, and more to meet basic security standards.

## Overview
The script performs the following actions to harden an Ubuntu 22.04 LTS machine:

1. **Update and Upgrade the System**: Ensures all packages are up to date.
2. **Disable Guest Account**: Prevents guest access for increased security.
3. **Set Password Policies**: Configures strong password policies, including minimum length and complexity.
4. **Enable UFW (Uncomplicated Firewall)**: Sets up the firewall to allow only necessary services.
5. **Disable Root SSH Login**: Prevents root login over SSH to secure remote access.
6. **Configure Automatic Updates**: Installs and configures automatic updates for ongoing security.
7. **Disable USB Storage**: Disables access to USB storage devices to prevent unauthorized data access.
8. **Remove Unnecessary Packages**: Uninstalls unneeded software to reduce vulnerabilities.
9. **Configure Auditd for System Auditing**: Sets up auditing to log system activities for security monitoring.

## Running the Script
### Prerequisites
- **Administrative Privileges**: The script must be run as root to make the necessary system changes.
- **Ubuntu 22.04 LTS**: The script is designed specifically for Ubuntu 22.04 LTS.

### Installation and Usage
You can either clone this repository using Git or manually download the script.

#### Option 1: Clone the Repository Using Git (Recommended)

1. **Install Git** (if not already installed):
   ```sh
   sudo apt update
   sudo apt install git -y
   ```

2. **Clone the Repository**:
   ```sh
   git clone https://github.com/Ripper1004/CyberPatriot-Security-Script.git
   cd CyberPatriot-Security-Script
   ```

3. **Run the Script**:
   ```sh
   sudo ./secure_ubuntu.sh
   ```

#### Option 2: Manual Download of the Script
1. **Download the Script Manually**:
   - Navigate to the GitHub repository (e.g., `https://github.com/Ripper1004/CyberPatriot-Security-Script`).
   - Click on the **"Code"** button, then click **"Download ZIP"**.
   - Extract the ZIP file to a location on your computer.

2. **Run the Script**:
   ```sh
   cd /path/to/extracted/directory
   sudo ./secure_ubuntu.sh
   ```

### Important Notes
- **Root Privileges**: The script requires root privileges to make system-wide changes. Always run the script with `sudo`.
- **Manual Verification**: While the script automates basic security hardening, manual verification is recommended to ensure all CyberPatriot-specific requirements are met.
- **Firewall Configuration**: The script uses UFW to manage firewall settings. Ensure that any necessary services are allowed through the firewall.

## Script Summary
After running, the script provides a summary of each action performed, indicating whether it was successful or failed. This helps in identifying areas that need manual intervention.

### Example Summary Output
```
Summary of Actions:
System Update and Upgrade: Success
Disable Guest Account: Success
Set Password Policies: Success
Enable UFW: Success
Disable Root SSH Login: Success
Configure Automatic Updates: Success
Disable USB Storage: Success
Remove Unnecessary Packages: Success
Configure Auditd: Success
```

## Contribution
Contributions to enhance the script are welcome! Feel free to submit a pull request if you have any improvements or additional security measures to suggest.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Disclaimer
This script is provided "as is" without warranty of any kind. Use at your own risk, and always test in a non-production environment first.

