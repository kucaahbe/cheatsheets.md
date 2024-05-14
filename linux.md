[[systemd]]

file last access time:
stat
ls -lu - show last access time
ls -lc - show last modification time

delete files not accessed last 30 days:
find dir -atime +30 -delete

files, accessed less than 13 minutes ago:
find . -atime -13m