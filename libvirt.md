# libvirtd

Linux install:
TODO

MacOS install:
```sh-session
brew install libvirt qemu
```

## Configuration

MacOS:

aspect | path
--- | ---
config folder | `/usr/local/etc/libvirt`
main daemon config file | `/usr/local/etc/libvirt/libvirtd.conf`
runtime directory | `/usr/local/var/run/libvirt`
domains directory | TODO

in `/usr/local/etc/libvirt/libvirtd.conf`:
```ini
# disable listening for secure TLS connections on the public TCP/IP port
listen_tls = 0
# Allow users of group "admin" to connect to libvirtd via socket:
unix_sock_group = "admin"
unix_sock_rw_perms = "0770"
```

# virt-admin
host management
# virsh
client management

## basic

### connection

Get a connection URI
```sh-session
uri
```

Connect to `qemu:///system`
```sh-session
sudo virsh
```

To always connect to `qemu:///system` by default (provided socket is configured):
```sh-session
export LIBVIRT_DEFAULT_URI="qemu:///system"
virsh
```

### hypervisor info

```sh-session
virsh capabilities
virsh # capabilities
```
