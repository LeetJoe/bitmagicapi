
### 1. 用户资产-获取

#### uri: /web/apiaccount/list

#### method: post

参数说明：(无)


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":
    {
        "uid":"10004",
        "balance":"10000.0000",
	    "mart_balance":"0.0000",
        "deposit_balance":"0.0000",
        "deposit_lock":"0.0000",
    }
}

```

返回数据说明：
- balance: 账户余额，暂时没用
- mart_balance: 商城账户余额
- deposit_balance: 定存账户余额
- deposit_lock: 定存账户锁定


### 2. 发起定存

#### uri: /web/apiaccount/deposit

#### method: post

参数说明：
- number 数量
- assettoken 资金密码


返回数据示例：

```

{
    "status":0
}

```

返回数据说明：(略)


### 3. 定存账户向商城账户划转

#### uri: /web/apiaccount/transfer

#### method: post

参数说明：
- number 数量
- assettoken 资金密码


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data": {newid}
}

```

返回数据说明：(略)


### 4. 账户划转记录

#### uri: /web/apiaccount/transferlist

#### method: post

参数说明：
- cur 页码

```
// todo

```



### 5. 获取邀请数量

#### uri: /web/apiaccount/getInviteInfo

#### 请求方法：post

参数说明：（无）

返回示例：

```

{
    "status": 0,
    "data": {
        "dir": [
            {
                "uid": "10006",
                "pid": "10001",
                "realname": "李**",
                "level": "C0",
                "created": "2019-06-28 06:58:53"
            }
        ],
        "indir": [
            {
                "uid": "10008",
                "pid": "10001",
                "realname": "王**",
                "level": "C2",
                "created": "2019-06-28 06:58:53"
            }
        ]
    }
}

```

返回说明：
- dir 表示直接邀请人列表
- indir 表示间接邀请人列表



### 6. 定存释放记录

#### uri: /web/apiaccount/getReleaseList

#### method: post

参数说明：
- cur 页码


返回数据示例：

```
{
    "status":0,"msg":
    {
        "page":[
            {
                "id":"2",
                "uid":"10001",
                "type":"0",
                "status":"1",
                "number":"5.000800000000000000",
                "stime":"0",
                "etime":"0",
                "remark":null,
                "created":"1561817696",
                "updated":"0",
                "type_desc": "类型描述",
                "status_desc": "状态描述"
            },
            {
                "id":"1",
                "uid":"10001",
                "type":"0",
                "status":"1",
                "number":"5.000800000000000000",
                "stime":"0",
                "etime":"0",
                "remark":null,
                "created":"1561817620",
                "updated":"0",
                "type_desc": "类型描述",
                "status_desc": "状态描述"
            }
        ],
        "next":1,
        "before":1,
        "last":1,
        "current":1,
        "totalItems":"2",
        "totalPages":1
    }
}


```

返回数据说明：（基本同上，区别如下）
- status: 0 待处理，1 已完成
