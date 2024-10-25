#!/bin/bash

# Secure Ubuntu 22.04 LTS Script for CyberPatriot

# Ensure the script is running as root
if [ "$EUID" -ne 0 ]; then
    echo "This script must be run as root. Please re-run using sudo." >&2
    exit 1
fi

# Initialize status tracking
declare -a action_results

# 1. Update and Upgrade the System
try_update() {
    apt update && apt upgrade -y
    if [ $? -eq 0 ]; then
        action_results+=("System Update and Upgrade: Success")
    else
        action_results+=("System Update and Upgrade: Failed")
    fi
}
try_update

# 2. Disable Guest Account
try_disable_guest() {
    if [ -f /etc/lightdm/lightdm.conf ]; then
        echo "allow-guest=false" >> /etc/lightdm/lightdm.conf
        action_results+=("Disable Guest Account: Success")
    else
        action_results+=("Disable Guest Account: Failed - LightDM configuration not found")
    fi
}
try_disable_guest

# 3. Set Password Policies (e.g., Minimum Length, Complexity)
try_set_password_policy() {
    echo "Setting password policies..."
    echo "minlen = 12" >> /etc/security/pwquality.conf
    echo "dcredit = -1" >> /etc/security/pwquality.conf
    echo "ucredit = -1" >> /etc/security/pwquality.conf
    echo "lcredit = -1" >> /etc/security/pwquality.conf
    echo "ocredit = -1" >> /etc/security/pwquality.conf
    if [ $? -eq 0 ]; then
        action_results+=("Set Password Policies: Success")
    else
        action_results+=("Set Password Policies: Failed")
    fi
}
try_set_password_policy

# 4. Enable UFW (Uncomplicated Firewall)
try_enable_ufw() {
    ufw default deny incoming
    ufw default allow outgoing
    ufw allow ssh
    ufw enable
    if [ $? -eq 0 ]; then
        action_results+=("Enable UFW: Success")
    else
        action_results+=("Enable UFW: Failed")
    fi
}
try_enable_ufw

# 5. Disable Root SSH Login
try_disable_root_ssh() {
    sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
    systemctl restart sshd
    if [ $? -eq 0 ]; then
        action_results+=("Disable Root SSH Login: Success")
    else
        action_results+=("Disable Root SSH Login: Failed")
    fi
}
try_disable_root_ssh

# 6. Configure Automatic Updates
try_auto_updates() {
    apt install unattended-upgrades -y
    dpkg-reconfigure -plow unattended-upgrades
    if [ $? -eq 0 ]; then
        action_results+=("Configure Automatic Updates: Success")
    else
        action_results+=("Configure Automatic Updates: Failed")
    fi
}
try_auto_updates

# 7. Disable USB Storage
try_disable_usb() {
    echo "blacklist usb-storage" > /etc/modprobe.d/usb-storage.conf
    if [ $? -eq 0 ]; then
        action_results+=("Disable USB Storage: Success")
    else
        action_results+=("Disable USB Storage: Failed")
    fi
}
try_disable_usb

# 8. Remove Unnecessary Packages (e.g., games, media)
try_remove_unnecessary() {
    apt purge -y thunderbird rhythmbox
    if [ $? -eq 0 ]; then
        action_results+=("Remove Unnecessary Packages: Success")
    else
        action_results+=("Remove Unnecessary Packages: Failed")
    fi
}
try_remove_unnecessary

# 9. Configure Auditd for System Auditing
try_configure_auditd() {
    apt install auditd -y
    systemctl enable auditd
    systemctl start auditd
    if [ $? -eq 0 ]; then
        action_results+=("Configure Auditd: Success")
    else
        action_results+=("Configure Auditd: Failed")
    fi
}
try_configure_auditd

# Display summary of actions
echo "Summary of Actions:"
for result in "${action_results[@]}"; do
    echo "$result"
done

# End of Script
