---
tags: tools
---
# runtime
## hostnamectl
shows info similar to `lsb_release`
## systemctl
conveniently create drop-in files:
```sh-session
# edits /etc/systemd/system/unit.service.d/override.conf
sudo systemctl edit unit
```
## journalctl
https://gist.github.com/sergeyklay/f401dbc8286f732783e05072f03ecb61
```sh-session
# tail logs:
journalctl -f
# view logs for specific unit:
journalctl -xe -u ssh
# kernel messages (-k), scrolled to bottom (-e):
journalctl -k -e
```
## networkctl
manage systemd-networkd network configuration
### Migrate from NetworkManager
1. install packages:
   ```sh-session
   # systemd-networkd is available in the default package "systemd" in Debian
   # systemd-resolved is a separate package:
   sudo apt-get install systemd-resolved
   ```
1. create basic network configuration for networkd:
   ```ini
   # /etc/systemd/network/lan0.network
   [Match]
   Name=eth0
   # or using stable interface name (ID_NET_NAME in udevadm info /sys/class/net/eth0)
   #Name=whatever it writes
   [Network]
   DHCP=yes
   # add search domains
   #Domains=lan
   [DHCPV4]
   UseDomains=yes
   ```
1. disable NetworkManager and enable networkd/resolved
   ```sh-session
   sudo systemctl stop NetworkManager
   sudo systemctl disable NetworkManager
   sudo systemctl enable systemd-networkd
   sudo systemctl enable systemd-resolved
   sudo systemctl start systemd-networkd
   sudo systemctl start systemd-resolved
   ```
1. reboot and hope it works
1. check the systemd units, who need to wait for network to be up and running, with networkd they need following unit config:
   ```ini
   [Unit]
   Requires=network-online.target
   After=network-online.target
   ```
1. if it works, remove NetworkManager:
   ```sh-session
   sudo apt-get purge network-manager
   sudo apt-get autoremove
   ```
## machinectl
manage systemd-nspawn [containers](systemd-container.md)