# AWK

mass file rename with git:

```sh-session
git ls-files *es6* | awk -F.es6 '{ system("git mv " $0 " " $1 $2) }'
```

append "rubocop:disable" to the end of the needed line:
```awk
#!/usr/bin/awk -f
# file: fixup.awk
# usage:
#   ./bin/rubocop --only Rails/CreateTableWithTimestamps -f emacs db/migrate | awk -f fixup.awk

# Set the field separator to ":" to extract line number
BEGIN {
    FS = ":"
}

# Process each line
{
    # Extract file name, line number, and the rest of the line
    file = $1
    line_num = $2
    rubocop_issue = substr($5, 2)
    gsub(/\//, "\\/", rubocop_issue)

    sed = "gsed -i '" line_num "s/$/ # rubocop:disable " rubocop_issue "/' " file
    #print sed
    system(sed)
}
```

append to begin and end of each file rubocop disable/enable:
```awk
#!/usr/bin/awk -f
# file: fixup.awk
# usage:
#   ./bin/rubocop --only Rails/ReversibleMigration -f files db/migrate | awk -f fixup.awk

{
    file = $1
    rubocop_issue = "Rails\\/ReversibleMigration"

    #print sed
    system("gsed -i '1 i \\# rubocop:disable " rubocop_issue "\n; $ a \\# rubocop:enable " rubocop_issue ";' " file)
}
```