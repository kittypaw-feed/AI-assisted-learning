# Fedora vs Ubuntu: Essential Terminal Commands

## Package Management

| Task | Fedora (DNF) | Ubuntu (APT) |
|------|--------------|--------------|
| Update package list | `sudo dnf check-update` | `sudo apt update` |
| Upgrade all packages | `sudo dnf upgrade` | `sudo apt upgrade` |
| Full system upgrade | `sudo dnf distro-sync` | `sudo apt full-upgrade` |
| Install a package | `sudo dnf install package_name` | `sudo apt install package_name` |
| Remove a package | `sudo dnf remove package_name` | `sudo apt remove package_name` |
| Remove package + config | `sudo dnf remove package_name` | `sudo apt purge package_name` |
| Search for a package | `dnf search package_name` | `apt search package_name` |
| Show package info | `dnf info package_name` | `apt show package_name` |
| List installed packages | `dnf list installed` | `apt list --installed` |
| Clean package cache | `sudo dnf clean all` | `sudo apt clean` |
| Remove unused dependencies | `sudo dnf autoremove` | `sudo apt autoremove` |

## System Services

| Task | Fedora | Ubuntu |
|------|--------|--------|
| Start a service | `sudo systemctl start service_name` | `sudo systemctl start service_name` |
| Stop a service | `sudo systemctl stop service_name` | `sudo systemctl stop service_name` |
| Enable service at boot | `sudo systemctl enable service_name` | `sudo systemctl enable service_name` |
| Disable service at boot | `sudo systemctl disable service_name` | `sudo systemctl disable service_name` |
| Check service status | `sudo systemctl status service_name` | `sudo systemctl status service_name` |
| Restart a service | `sudo systemctl restart service_name` | `sudo systemctl restart service_name` |

*Note: Both use systemd, so service management commands are identical.*

## Firewall Management

| Task | Fedora (firewalld) | Ubuntu (ufw) |
|------|-------------------|--------------|
| Enable firewall | `sudo systemctl start firewalld` | `sudo ufw enable` |
| Disable firewall | `sudo systemctl stop firewalld` | `sudo ufw disable` |
| Check firewall status | `sudo firewall-cmd --state` | `sudo ufw status` |
| Allow a port | `sudo firewall-cmd --add-port=80/tcp --permanent` | `sudo ufw allow 80/tcp` |
| Remove a port | `sudo firewall-cmd --remove-port=80/tcp --permanent` | `sudo ufw delete allow 80/tcp` |
| Allow a service | `sudo firewall-cmd --add-service=http --permanent` | `sudo ufw allow http` |
| Reload firewall | `sudo firewall-cmd --reload` | `sudo ufw reload` |
| List all rules | `sudo firewall-cmd --list-all` | `sudo ufw status verbose` |

## SELinux vs AppArmor

| Task | Fedora (SELinux) | Ubuntu (AppArmor) |
|------|------------------|-------------------|
| Check status | `sestatus` | `sudo aa-status` |
| Set to permissive mode | `sudo setenforce 0` | `sudo aa-complain /path/to/profile` |
| Set to enforcing mode | `sudo setenforce 1` | `sudo aa-enforce /path/to/profile` |
| Disable temporarily | `sudo setenforce 0` | `sudo systemctl stop apparmor` |
| View denials/logs | `sudo ausearch -m avc -ts recent` | `sudo dmesg \| grep apparmor` |

## Software Repositories

| Task | Fedora | Ubuntu |
|------|--------|--------|
| Add repository | Edit `/etc/yum.repos.d/` or use `dnf config-manager` | `sudo add-apt-repository ppa:name` |
| Enable third-party repos | `sudo dnf install fedora-workstation-repositories` | Built into Software & Updates GUI |
| Popular third-party repo | RPM Fusion: `sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm` | Various PPAs |
| List repositories | `dnf repolist` | `apt policy` or check `/etc/apt/sources.list` |

## System Information

| Task | Fedora | Ubuntu |
|------|--------|--------|
| Check OS version | `cat /etc/fedora-release` | `cat /etc/lsb-release` or `lsb_release -a` |
| Kernel version | `uname -r` | `uname -r` |
| System info | `hostnamectl` | `hostnamectl` |

## Quick Tips

### Fedora-specific
- DNF is slower than APT but provides better dependency resolution
- Use `dnf history` to view and undo previous transactions
- `dnf provides */command_name` helps find which package provides a command

### Ubuntu-specific
- APT is generally faster for most operations
- `apt` is newer and more user-friendly than `apt-get`
- PPAs provide easy access to third-party software

### Common Ground
Both distributions use systemd for init and service management, making many system administration tasks identical between them.