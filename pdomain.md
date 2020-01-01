**接口**
``` javascript
curl http://localhost/domain/add -d '{"partner":"xxxxx","webdomain":"https://xxxx.com"}'
curl http://localhost/domain/del -d '{"webdomain":"https://xxxx.com"}'
curl "http://localhost/domain/get?pagenum=0&pagecount=10"
curl http://localhost/domain/bypartner?partner=xxxxx
curl http://localhost/domain/bywebdomain -d '{"webdomain":"https://xxxxx.com"}'
```
