
**http接口1 保存新创建的竞猜**
###### 接口功能
> 管理员在链上新创建了一个竞猜，将其保存

###### URL
> [http://localhost/guess/save](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> post

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gid    |是    |uint64   |竞猜id |
|assetid    |是    |uint64   |资产id |
|minchip    |是    |uint64   |本竞猜每个用户的下注最小筹个数 |
|maxchip    |是    |uint64   |本竞猜每个用户的下注最大筹个数 |
|endguess    |是    |uint64   |下注截止时间，格林威治时间1970年01月01日00时00分00秒起的总秒数 |
|endtime    |是    |uint64   |开奖时间 |
|gclass    |是    |string   |竞猜系列分类 |
|title    |是    |string   |竞猜标题 |
|sketch    |是    |string   |竞猜简述 |
|desc    |是    |string   |竞猜内容 |
|opts    |是    |json  string数组   |竞猜选项 |
|creator    |是    |string   |创建者，直接是公链账户（可能支持多个管理员账户有创建权限） |
|其它    |否    |null   |其它未在此描述的字段由后台服务直接默认处理：如状态、分类后的期数|

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|data  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/guess/save -d '{"gid":1,"assetid":0,"minchip":1,"maxchip":10,"endguess":1576206359,"endtime":1576292759,"gclass":"足球赛","title":"世界杯预先赛竞猜","sketch":"中国 vs 叙利亚","desc":"世界杯预选赛中国vs叙利亚","opts":[{"opt":0,"desc":"赢"},{"opt":1,"desc":"平"},{"opt":2,"desc":"输"}],"creator":"laocai"}'

> curl http://localhost/guess/save -d '{"gid":2,"assetid":0,"minchip":2,"maxchip":10,"endguess":1576206659,"endtime":1576292859,"gclass":"数字币价格","title":"每天BTC预测","sketch":"BTC价格之神","desc":"每天BTC价格涨跌预测","opts":[{"opt":0,"desc":"涨"},{"opt":1,"desc":"跌"},{"opt":2,"desc":"不波动"}],"creator":"laoluo"}'
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```

**http接口2 删除竞猜**
###### 接口功能
> 管理员更新竞猜的状态信息

###### URL
> [http://localhost/guess/del](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> get

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gid    |是    |uint64   |竞猜id |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/guess/del?gid=3
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```

**http接口3 更新竞猜的状态信息**
###### 接口功能
> 管理员更新竞猜的状态信息

###### URL
> [http://localhost/guess/setstatus](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> get

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gid    |是    |uint64   |竞猜id |
|status    |是    |uint   |竞猜状态：1：待发布；2：竞猜进行中；3：等待开奖 ；4：已结束； |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/guess/setstatus?gid=12&status=2
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```

**http接口4 开奖**
###### 接口功能
> 管理员开奖

###### URL
> [http://localhost/guess/endguess](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> get

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gid    |是    |uint64   |竞猜id |
|opt    |是    |uint   |第几个选项，选项序号从0开始 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 正确为空                      |

###### 接口示例
> curl http://localhost/guess/endguess?gid=12&winopt=2
返回：
``` javascript
{
  "status":0,
  "msg":""
}
```

**http接口5 根据时间获取竞猜列表**
###### 接口功能
> 按下注截止时间或结束时间倒序获取状态未结束的列表

###### URL
> [http://localhost/guess/getlist/bytime](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gettype    |是    |int   |根据条件获取。1：按截止时间；2：按结束时间 |
|pagenum    |是    |int   |第几页，从0开始 |
|pagecount    |是    |int   |每页数量 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容数据                      |
|data  |json数组 | 竞猜内容数据                      |

###### 接口示例
> curl http://localhost/guess/getlist/bytime?gettype=1&pagenum=0&pagecount=10
返回：
``` javascript
{
  "status":0,
   "msg":"",
   "data":[{"gid":2,"assetid":0,"minchip":2,"maxchip":10,"endguess":1576206659,"endtime":1576292859,"gclass":"数字币价格","title":"每天BTC预测","sketch":"BTC价格之神","desc":"每天BTC价格涨跌预测","opts":[{"opt":0,"desc":"涨"},{"opt":1,"desc":"跌"},{"opt":2,"desc":"不波动"}],"winopt":999,"status":1,"chipsum":0,"participants":0,"creator":"laoluo","createtime":1575343818},{"gid":1,"assetid":0,"minchip":1,"maxchip":10,"endguess":1576206359,"endtime":1576292759,"gclass":"足球赛","title":"世界杯预先赛竞猜","sketch":"中国 vs 叙利亚","desc":"世界杯预选赛中国vs叙利亚","opts":[{"opt":0,"desc":"赢"},{"opt":1,"desc":"平"},{"opt":2,"desc":"输"}],"winopt":999,"status":1,"chipsum":0,"participants":0,"creator":"laocai","createtime":1575343050}]
}
```

**http接口6 根据热度获取竞猜列表**
###### 接口功能
> 按下注金额或人数获取状态未结束的列表，默认按下注截止时间倒序

###### URL
> [http://localhost/guess/getlist/byhot](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gettype    |是    |int   |根据条件获取。1：按金额大小；2：按人数 |
|pagenum    |是    |int   |第几页，从0开始 |
|pagecount    |是    |int   |每页数量 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容数据                      |
|data  |json数组 | 竞猜内容数据                      |

###### 接口示例
> curl http://localhost/guess/getlist/byhot?gettype=1&pagenum=0&pagecount=10
返回：
``` javascript
{
    "status": 0,
    "msg":"",
    "data": [...]
}
```
**http接口7 根据状态获取竞猜列表**
###### 接口功能
> 按下注金额或人数获取状态未结束的列表，默认按结束时间倒序

###### URL
> [http://localhost/guess/getlist/bystatus](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|status    |是    |int   |根据状态获取。1：待发布；2：竞猜进行中；3：等待开奖 ；4：已结束；|
|pagenum    |是    |int   |第几页，从0开始 |
|pagecount    |是    |int   |每页数量 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容数据                      |
|data  |json数组 | 竞猜内容数据                      |

###### 接口示例
> curl http://localhost/guess/getlist/bystatus?status=1&pagenum=0&pagecount=10
返回：
``` javascript
{
    "status": 0,
    "msg":"",
    "data": [...]
}
```

**http接口8 获取竞猜详情**
###### 接口功能
> 根据竞猜id获取详细此竞猜的信息

###### URL
> [http://localhost/guess/desc](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gid    |是    |uint64   |竞猜id |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|data  |string | 竞猜内容详细信息                      |

###### 接口示例
> curl http://localhost/guess/desc?gid=12
返回：
``` javascript
{
    "status": 0,
    "data": {...}
}
```

**http接口9 添加竞猜类别**
###### 接口功能
> 根据竞猜id获取详细此竞猜的信息

###### URL
> [http://localhost/guess/guessclass/add](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gclass    |是    |string   |类别名称 |
|weight    |是    |int   |权重 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容详细信息                      |

###### 接口示例
> curl http://localhost/guess/guessclass/add?gclass=足球赛&weight=1
返回：
``` javascript
{
    "status": 0,
    "msg": ""
}
```

**http接口10 删除竞猜类别**
###### 接口功能
> 根据竞猜id获取详细此竞猜的信息

###### URL
> [http://localhost/guess/guessclass/del](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gclass    |是    |string   |类别名称 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容详细信息                      |

###### 接口示例
> curl http://localhost/guess/guessclass/del?gclass=足球赛
返回：
``` javascript
{
    "status": 0,
    "msg": ""
}
```

**http接口11 修改竞猜权重**
###### 接口功能
> 根据竞猜id获取详细此竞猜的信息

###### URL
> [http://localhost/guess/guessclass/set](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|gclass    |是    |string   |类别名称 |
|weight    |是    |int   |权重 |

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容详细信息                      |

###### 接口示例
> curl http://localhost/guess/guessclass/set?gclass=足球赛&weight=3
返回：
``` javascript
{
    "status": 0,
    "msg": ""
}
```

**http接口12 拉取竞猜类别**
###### 接口功能
> 根据竞猜id获取详细此竞猜的信息

###### URL
> [http://localhost/guess/guessclass/get](http://)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
无

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。0：正常；1：错误。   |
|msg  |string | 竞猜内容详细信息                      |

###### 接口示例
> curl http://localhost/guess/guessclass/get
返回：
``` javascript
{
  "status":0,
  "msg":"",
  "data":[{"gclass":"数字币价格","weight":1},{"gclass":"足球赛","weight":3}]
}
```
