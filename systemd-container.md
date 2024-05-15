# Documentation
[official manual](https://www.freedesktop.org/software/systemd/man/latest/systemd-nspawn.html)
[good debian manual](https://wiki.debian.org/nspawn)
[images hub](https://nspawn.org/images/)
# Install on host
(Ubuntu-based)
```sh-session
sudo apt install systemd-container mmdebstrap
sudo sysctl kernel.unprivileged_userns_clone # must be kernel.unprivileged_userns_clone = 1
# default on debian/ubuntu, but just in case change to 1
# to enable simple virtual networking for containers:
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service
```
# Container creation
```bash
#!/bin/bash
set -eu

# https://wiki.debian.org/nspawn

VM_NAME="basic-ubuntu-focal"
MACHINES_FOLDER=/var/lib/machines
UBUNTU_RELEASE=focal

# https://launchpad.net/ubuntu/+archivemirrors
APT_MIRROR=

sudo machinectl stop "$VM_NAME" || :
sudo rm -rf "$MACHINES_FOLDER/$VM_NAME"
sudo mmdebstrap \
	--customize-hook='chroot "$1" useradd --home-dir /home/user --create-home --shell /bin/bash --groups adm,sudo user' \
	--customize-hook='chroot "$1" passwd --delete user' \
	--customize-hook='echo "'$VM_NAME'" %3E "$1/etc/hostname"' \
	--customize-hook='echo "127.0.0.1 localhost '$VM_NAME'" > "$1/etc/hosts"' \
	--include=systemd,dbus --components=main \
	"$UBUNTU_RELEASE" "$MACHINES_FOLDER/$VM_NAME" "$APT_MIRROR">)
```
DNS name of the container:
place "mymachines" before the "resolve" or "dns" entry of the "hosts:" line of /etc/nsswitch.conf
# Container management
Start/stop/kill/reboot:
```sh-session
sudo machinectl start name
sudo machinectl stop name
sudo machinectl kill name
sudo machinectl reboot name
```
List/status:
```sh-session
sudo machinectl
sudo machinectl status name
```
Login:
```sh-session
sudo machinectl login name
```
Files exchange:
```sh-session
# NOTE: only supports single files and full path must be specified for both sides
sudo machinectl copy-to name /local/path.txt /container/path.txt
sudo machinectl copy-from name /container/path.txt /host/path.txt
sudo machinectl bind name PATH [PATH]
```
Enable/disable at boot:
```sh-session
sudo machinectl enable name
sudo machinectl disable name
```