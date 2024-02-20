### SELECT TO CSV

```sh-session
\copy (SELECT * FROM table) To '/tmp/psql-output.csv' With CSV
```


or [https://www.postgresql.org/docs/current/static/sql-copy.html](https://www.postgresql.org/docs/current/static/sql-copy.html)

### set pager to always

```sh-session
\pset pager always
```