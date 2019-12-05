**http接口1 登陆**
###### 接口功能
> 登陆返回cookie会话

###### URL
> [http://localhost/admin/login](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> post

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|name    |是    |string   |用户名 |
|passwd    |是    |string   |密码 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/admin/login -d '{"name":"myname", "passwd":"mypasswd"}'
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```

**http接口2 登出**
###### 接口功能
> cookie会话无效

###### URL
> [http://localhost/admin/logout](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> post

###### 请求参数
空

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/admin/logout -d ''
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```
