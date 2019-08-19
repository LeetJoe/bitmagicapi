
### 1. 获取充值地址

#### uri: /web/apiwallet/getaddr

#### method: post

参数说明：
- coin 币种

返回示例：
```
{
    "status":0,
    "msg":"",
    "data": {地址}
}

```

特别说明：

有的币种地址生成比较慢，在生成过程中，会返回status = 51，表示地址正在生成中，需要稍等片刻。


### 2. 添加转出币地址

#### uri: /web/apiwallet/addaddress

#### method: post

参数说明：
- coin 币种
- address 地址。示例地址：btc(usdt) => 3NoyBq6WGZZCf1vWpppE9JyNhmupMH4i1M [区分大小写], eth(zyc) => 0xd33577609F71Eeb9e72B8B077590f50F9cbbCe0A [不区分大小写]
- remark 地址备注，不要超过10个字
- assettoken 资金密码
- ga 如果绑定了ga需要输入

返回示例：
```
{
    "status":0,
    "msg":"",
    "data": {新地址id}
}

```

注意：同一个币种，同时只允许存在10个有效的地址，超过数量会被拒绝。地址可以删除。

### 3. 删除转出币地址

#### uri: /web/apiwallet/deladdress

#### method: post

参数说明：
- id 要删除的地址id

返回示例：
```
{
    "status":0,
    "msg":""
}

```


### 4. 获取转出地址列表

#### uri: /web/apiwallet/addrlist

#### method: post

参数说明：
- coin 币种

返回示例：
```
{
    "status":0,
    "data":[
        {
            "id":"1",
            "uid":"10001",
            "coin":"btc",
            "address":"xxxxxxxxxxxxxx",
            "remark":"aaaaa",
            "status":"0",
            "created":"2019-05-19 22:12:13",
            "createip":"xxx.xxx.xxx.xxx",
            "updated":"0",
            "updateip":"0.0.0.0"
        }
    ]
}

```


### 5. 提币申请

#### uri: /web/apiwallet/transout

#### method: post

参数说明：
- coin 币种
- addressid 转出币地址的id，见上方地址列表
- number 转出数量
- assettoken 资金密码
- code 手机验证码，如果没有绑定手机会提示绑定
- ga 如果开启了ga验证，需要此内容

返回示例：

```
{
    "status":0,
    "msg":"",
    "data": {转币记录的id}
}

```


### 6. 撤消提币申请

#### uri: /web/apiwallet/cancel

#### method: post

参数说明：
- id 转币记录id
- coin 转币币种

返回示例：

```
{
    "status":0,
    "msg":"",
    "data": {
        "number": 123,
        "time": 1562666276
    }
}

```

返回说明：
- number 撤消的转出数量
- time 转出申请时间戳


注意：只有状态在 等待中，即 status = 0 的记录才可以由用户撤消

### 7. 转币历史记录，入账出账共用此api

#### uri: /web/apiwallet/history

#### method: post

参数说明：
- type 空：全部，0：转入，1：转出
- coin 币种
- p 页码，每页20条

返回示例：

```

{
    "status":0,
    "data":
    {
        "page":
        [
            {
                "id":"12",
                "tid":"0",
                "uid":"10001",
                "admin":"0",
                "wallet":"1M1******vaa",
                "walletid":"1",
                "txid":"nonce_2019-07-09_22:24:17_67043",
                "txindex":"0",
                "confirm":"0",
                "amount":"1.00000000",
                "transfee":"0.00004000",
                "pay":"1.00000000",
                "type":"1",
                "status":"5",
                "msg":"",
                "remark":"",
                "created":"2019-07-09 22:24:17",
                "createip":"0.0.0.0",
                "updated":"2019-07-09 10:24:17",
                "updateip":"0.0.0.0",
                "status_desc":"已取消"
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
- txid 交易id，如果是以 nonce 开头的内容，表示尚未被处理，展示为空即可
- admin 审核管理员uid
- walletid 仅转出有效，表示地址本中的id
- txindex 交易在区块中的位置
- confirm 确认数量
- amount 数量
- wallet 地址
- msg 失败原因(暂不需要显示)
- remark 备注(内部使用不显示)
- transfee 手续费
- pay 扣除手续费后实际的转出数量，对转入而言与amount相等。
- type 0 转入，1 转出
- status 1: 待处理 2:确认中 3:待入账 4:已入账 5:已取消(仅转出) 6:处理失败 7:待人工处理
- status_desc 状态描述