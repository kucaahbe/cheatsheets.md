# WSL

list installed distros:
```sh
wsl --list
wsl --list --online # all available distros
```

install new distro
```sh
wsl --install [Distro] --location <path> --name <Name>
```

set as defalt
```sh
wsl -s <Distro>
```
run specific distro
```sh
wsl ~ -d <Distro>
```
remove distro
```sh
wsl --unregister <Distro>
```
NOTE: will remove vhdx disk!

move WSL to some specific place

```sh
wsl --manage Ubuntu --move D:\WSL\Ubuntu
```
how to restore (from windows re-install)

```sh
# install WSL if not yet
wsl --import-in-place <Distribution Name> <FileName>
```
if `Error code: Wsl/Service/RegisterDistro/MountDisk/HCS/E_ACCESSDENIED`:
open "security" tab of file properties and align access rights:
Authenticated users: full access
SYSTEM: full access
Administrators: full access
Users: read & execute
# files management
remove directory which can't be removed (doesn't really work when some files inside has incorrect permissions, eg, no user exists or so):
To fix permissions issue, add current user (full access) to that folder - Permissions -> security -> additional -> add your user
(in sudo powershell)
```sh
Remove-Item -Path <path> -Force -Recurse
```