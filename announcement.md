**添加接口，成功返回id**
``` javascript
curl http://107.191.49.150:8080/announcement/add -d '{"title":"公告标题", "content":"公告内容"}'
返回：{"status":0,"msg":"","data":{"id":""}}
```

**根据id删除**
``` javascript
curl http://107.191.49.150:8080/announcement/del?aid=""
返回：{"status":0,"msg":""}
```

**更新接口是全部字段更新**
``` javascript
curl http://107.191.49.150:8080/announcement/set -d '{"aid":"","title":"公告标题set", "content":"公告内容set"}'
返回：{"status":0,"msg":""}
```

**因轮播数据只有几条，拉取时不分页**
``` javascript
curl http://107.191.49.150:8080/announcement/get?
返回：
```
