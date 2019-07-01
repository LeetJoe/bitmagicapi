
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
        "eth":
        {
            "uid":"10004",
            "balance":"10000.0000",
            "lock":"0.0000",
            "c2clock":"0.0000",
            "otherlock":"0.0000000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"ETH",
            "total":"10000.0000"
        },
        "btc":
        {
            "uid":"10004",
            "balance":"9999.9999",
            "lock":"0.0000",
            "c2clock":"0.0000",
            "otherlock":"0.000000000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"BTC",
            "total":"9999.9999"
        },
        "usdt":
        {
            "uid":"10004",
            "balance":"99990000.8000",
            "lock":"0.0000",
            "c2clock":"0.0000",
            "otherlock":"0.000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"USDT",
            "total":"99990000.8000"
        }
    }
}

```

### 2. 我的提币地址

#### uri: /web/apiwallet/getaddr

#### method: post

参数说明：
- coin 币种


返回数据示例：

```

{
    "status":0,
    "msg":""
    "data":"USER_ADDRESS"
}

```

### 3. 充提币记录

#### uri: /web/apiwallet/history

#### method: post

参数说明：
- type 类型；空表示全部，0 表示转入，1 表示转出
- coin 币种
- p 页码
- size 单页条数


返回数据示例：

```

{
    "status":0,
    "data":
    {
        "page":
        [
            {
                "id":"1",
                "tid":"0",
                "uid":"10005",
                "admin":"0",
                "wallet":"123******124",
                "walletid":"1",
                "txid":"asdfaasdfasdfasdfasdfasdf",
                "txindex":"0",
                "confirm":"6",
                "amount":"0.12300000",
                "transfee":"0.00012300",
                "pay":"0.12300000",
                "type":"0",
                "status":"1",
                "msg":"",
                "remark":"",
                "created":"2019-05-17 23:22:18",
                "createip":"0.0.0.0",
                "updated":"2019-05-17 23:22:18",
                "updateip":"0.0.0.0",
                "status_desc":"\u7b49\u5f85\u4e2d"
            }
        ],
        "next":1,
        "before":1,
        "last":1,
        "current":1,
        "totalItems":"1",
        "totalPages":1
    }
}

```

返回数据说明：
- page 数据列表
- next 下一页页码
- before 前一页页码
- last 最后一页页码
- current 当前页页码
- totalItems 总数据量
- totalPages 总页数
- uid 用户id
- wallet 收/发币钱包地址
- walletid 发币情况下，用户发币地址的id
- txid 交易的transaction id
- confirm 入账成功时确认数
- amount 总数量
- transfee 手续费，转出时会扣除
- pay 实际数量；入账时，amount = pay, 出账时，amount = pay + transfee
- type 类型 0 转入 1 转出
- status 状态
- status_desc 状态描述 
- created 创建时间
- updated 更新时间

### 4. 提币地址列表

#### uri: /web/apiwallet/addrlist

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 5. 添加新提币地址

#### uri: /web/apiwallet/addaddress

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 6. 删除提币地址

#### uri: /web/apiwallet/deladdress

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 7. 提交提币申请

#### uri: /web/apiwallet/transout

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 8. 撤销提币申请

#### uri: /web/apiwallet/cancel

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 9. 绑定银行卡信息

#### uri: /web/apiaccount/bindBankInfo

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 10. 绑定支付宝信息

#### uri: /web/apiaccount/bindAlipayInfo

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 11. 绑定微信支付信息

#### uri: /web/apiaccount/bindWechatInfo

#### method: post

参数说明：
- 


返回数据示例：

```


```

### 12. 获取c2c用户绑定支付信息

#### uri: /web/apiaccount/getC2cBindInfo

#### method: post

参数说明：
- 


返回数据示例：

```


```
