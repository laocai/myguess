**添加接口，成功返回aid--HTTP POST**
``` javascript
curl http://107.191.49.150:8080/announcement/add -d '{"title":"公告标题", "content":"公告内容"}'
返回：{"status":0,"msg":"","data":{"aid":"e3262cd7-1e22-11ea-846a-5600026eb468"}}
```

**根据id删除--HTTP GET**
``` javascript
curl http://107.191.49.150:8080/announcement/del?aid="e3262cd7-1e22-11ea-846a-5600026eb468"
返回：{"status":0,"msg":""}
```

**更新接口是全部字段更新--HTTP POST**
``` javascript
curl http://107.191.49.150:8080/announcement/set -d '{"aid":"e3262cd7-1e22-11ea-846a-5600026eb468","title":"公告标题set", "content":"公告内容set"}'
返回：{"status":0,"msg":""}
```

**拉取分页接口--HTTP GET**
``` javascript
curl "http://107.191.49.150:8080/announcement/get?pagenum=0&pagecount=10"
返回：{"status":0,"msg":"","data":{"sum":1,"infos":[{"aid":"7cdf98bf-1e23-11ea-87e0-5600026eb468","title":"公告标题set","content":"公告内容set","status":0}]}}
```
