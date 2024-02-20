## Documentation
https://github.com/transmission/transmission/blob/main/docs/Configuration-Files.md

## CLI
use `transmission-remote host:port -n user:pwd` (while `sudo -u transmission-user`)
inspect torrent content: `transmission-show file.torrent`
add torrent ` transmission-remote localhost:9091 -n user:pwd -a file.torrent -w /folder`