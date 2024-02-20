---
tags: tools
---

[good curl online help page](https://curl.haxx.se/docs/httpscripting.html)


display out: -v  (or more compact and for regular case -i)
header -H ''
-H 'accept: */*' \
-H "Authorization: $apiKey" \
-H 'Content-Type: application/json' \

request type -X

request body -d '{"json": "data"}'

handle redirect -L

disable progress output `-s` (`--silent`)

POST

```sh-session
curl --data "{ 'a': 1 }" http://host.co/path
curl -d "{ 'a': 1 }" http://host.co/path
```

Set header

```sh-session
curl --header "X-MyHeader: 123" -H "X-Myheader2: 456" http://host.co
```

HTTP Basic Authentication

```sh-session
curl --user name:password http://host.co
```

## Download files
```bash
curl -O https://server.co/my/file.txt # will download file.txt
curl -o my-file.txt https://server.co/my/file.txt # will download file.txt by name my-file.txt
```