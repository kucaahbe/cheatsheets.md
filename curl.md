display out: -v  (or more compact and for regular case -i)
header -H ''
-H 'accept: */*' \
-H "Authorization: $apiKey" \
-H 'Content-Type: application/json' \

request type -X 

request body -d '{"json": "data"}'
