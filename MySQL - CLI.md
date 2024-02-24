# CLI - [mycli](https://www.mycli.net/docs)

output to file once:
`\o -o /tmp/f.csv`

CSV format of data:
`\T csv`
example
```sh-session
\T csv
\o /tmp/data.csv
SELECT first_name, last_name, email FROM employees;
```

plain output
`\T plain` with header
`\T minimal` just list of stuff without header

List of output formats:
`\T`

# CLI - default

## CSV
```sh-session
emp_db> \copy (SELECT first_name, last_name, email FROM employees) TO '/tmp/data.csv'
```

## Credentials management

list all available credentials:

```sh-session
mysql_config_editor print —all
```

add new credentials:

```sh-session
mysql_config_editor set --login-path=LOGIN_PATH --host=HOST --user=USER --password
```

remove credentials:

```sh-session
mysql_config_editor remove -—login-path=LOGIN_PATH
```

`mysql_config_editor` creates and maintains encrypted `~/.mylogin.cnf`

use credentials:

```sh-session
mysql --login-path=os-prod-orig dbname
```