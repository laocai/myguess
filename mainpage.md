添加接口，成功返回id
curl http://107.191.49.150:8080/mainp/hturn/add -d '{"desc":"mydesc", "image":"test.jpg", "url":"http://localhost", "urltext":"url desc"}'
返回：{"status":0,"msg":"","data":{"id":"f821f41d-1352-11ea-807d-5600026eb468"}}

根据id删除
curl http://107.191.49.150:8080/mainp/hturn/del -d '{"hturnid":"edc49258-1341-11ea-bd12-5600026eb468"}'
返回：{"status":0,"msg":""}

更新接口是全部字段更新
curl http://107.191.49.150:8080/mainp/hturn/set -d '{"hturnid":"f821f41d-1352-11ea-807d-5600026eb468", "desc":"mysetdesc", "image":"test.jpg", "url":"http://localhost", "urltext":"set url desc"}'   
返回：{"status":0,"msg":""}

因轮播数据只有几条，拉取时不分页
curl http://107.191.49.150:8080/mainp/hturn/get -d ''
返回：{"status":0,"msg":"","data":[{"hturnid":"fed26dbc-1341-11ea-bd12-5600026eb468","desc":"mysetdesc","image":"http://107.191.49.150:8021/images/b.jpg","url":"http://localhost","urltext":"url desc"},{"hturnid":"f821f41d-1352-11ea-807d-5600026eb468","desc":"mysetdesc","image":"http://107.191.49.150:8021/images/test.jpg","url":"http://localhost","urltext":"set url desc"}]}
