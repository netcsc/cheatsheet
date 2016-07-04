# search with IP
```bash
curl -D- -u username:password -X POST -H "Content-Type: application/json" --data '{"jql":"summary ~ 50\\u002e116\\u002e43\\u002e185 AND project = HDM","startAt":0,"maxResults":2,"fields":["id","key"]}' "http://hostname/rest/api/2/search"
```
