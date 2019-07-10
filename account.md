
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
	        "toc2c_lock":"0.0000",
	        "fromc2c_lock":"0.0000",
	        "c2c_balance":"0.0000",
            "c2clock":"0.0000",
            "mine_balance":"0.0000",
            "mine_lock":"0.0000",
            "evermined":"0",
            "otherlock":"0.0000000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"ETH",
        },
        "btc":
        {
            "uid":"10004",
            "balance":"9999.9999",
            "lock":"0.0000",
	        "toc2c_lock":"0.0000",
	        "fromc2c_lock":"0.0000",
	        "c2c_balance":"0.0000",
            "c2clock":"0.0000",
            "mine_balance":"0.0000",
            "mine_lock":"0.0000",
            "evermined":"0",
            "otherlock":"0.000000000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"BTC",
        },
        "usdt":
        {
            "uid":"10004",
            "balance":"99990000.8000",
            "lock":"0.0000",
	        "toc2c_lock":"0.0000",
	        "fromc2c_lock":"0.0000",
	        "c2c_balance":"0.0000",
            "c2clock":"0.0000",
            "mine_balance":"0.0000",
            "mine_lock":"0.0000",
            "evermined":"0",
            "otherlock":"0.000000000000",
            "ratelevel":"0",
            "rate":"0.001",
            "coin":"USDT",
        }
    }
}

```

返回数据说明：
- balance: 币币账户余额
- lock: 币币账户锁定
- toc2c_lock： 用户从币币账户划转到c2c账户的锁定数量。因为这类划转是延迟到账。
- fromc2c_lock: 用户从c2c账户转到币币账户的锁定数量。因为目前这类划转是立即到账，所以这个字段实际上没用。
- mine_balance: 挖矿账户余额，可以划转至币币账户，没有锁定期；
- mine_lock: 挖矿账户锁定，目前只有系统赠送的zyc会进入这个数字。
- evermined: 标记用户是否进行过挖矿释放交易，后台做的记号，目前前端不用关心。
- otherlock: 备用字段。
- rate: 费率，如果值不小于0，则以此值计算用户交易手续费；如果小于0，以下方ratelevel定手续费；
- ratelevel: 见关于rate的说明，费率等级，一般0表示0.001，数字越大费率越低；


### 2. 绑定银行卡信息

前置要求：完成初级实名认证，绑定手机号，设置资金密码。

#### uri: /web/apiaccount/bindBankInfo

#### method: post

参数说明：
- assettoken 资金密码
- code 手机验证码
- bank 银行id，见 /web/index/banklist
- branch 支行名称
- card 卡号


返回数据示例：

```

{
    "status":0,
    "msg":"银行卡信息设置成功"
}

```

### 3. 绑定支付宝信息

前置要求：完成初级实名认证，绑定手机号，设置资金密码。

#### uri: /web/apiaccount/bindAlipayInfo

#### method: post

参数说明：
- assettoken 资金密码
- code 手机验证码
- alipay 支付宝账号，邮箱或手机
- 一张通过表单提交的图片


返回数据示例：

```
{
    "status":0,
    "msg":"支付宝设置成功"
}

```

### 4. 绑定微信支付信息

前置要求：完成初级实名认证，绑定手机号，设置资金密码。

#### uri: /web/apiaccount/bindWechatInfo

#### method: post

参数说明：
- assettoken 资金密码
- code 手机验证码
- wechatid 微信号
- 一张通过表单提交的图片

返回数据示例：

```
{
    "status":0,
    "msg":"微信支付设置成功"
}
```

### 5. 获取c2c用户绑定支付信息

#### uri: /web/apiaccount/getC2cBindInfo

#### method: post

参数说明：(无)


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":
    {
        "uid":"10005",
        "alipay":"a***c@a***c.com",
        "askrate":"-1.00000",
        "askratelevel":"0",
        "bank":"某某某银行",
        "bidrate":"-1.00000",
        "bidratelevel":"0",
        "binding":"0",
        "bound":"7",
        "branch":"qwerqwerqw",
        "card":"123******234",
        "ctype":"1",
        "dealcount":"0",
        "wechatid":"wq****23"
    }
}


```


### 6. 币币账户向法币账户转币

#### uri: /web/apiaccount/toc2c

#### method: post

参数说明：
- coin 币种
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


### 7. 法币账户向币币账户转币

#### uri: /web/apiaccount/fromc2c

#### method: post

参数说明：
- coin 币种
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

返回数据说明：（略）


### 8. 挖矿账户向币币账户转币

#### uri: /web/apiaccount/frommine

#### method: post

参数说明：
- coin 币种
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

返回数据说明：（略）


### 9. 法币账户向币币账户转币历史记录

#### uri: /web/apiaccount/fromc2clist

#### method: post

参数说明：
- coin 币种
- cur 页码


返回数据示例：

```
{
    "status":0,
    "msg":{
        "page":[
        {
            "id":"9",
            "uid":"10001",
            "type":"1",
            "status":"1",
            "number":"100.00000000",
            "created":"1562270464",
            "createip":"3232252417",
            "updated":"0",
            "updateip":"0"
        },
        ...
        ],
        "next":1,
        "before":1,
        "last":1,
        "current":1,
        "totalItems":"3",
        "totalPages":1
    }
}

```

返回数据说明：
- uid 用户id
- type 类型 0: 转入至c2c， 1: 从c2c转出
- status 状态 0 划转中，1: 划转完成，2: 已撤销，3: 划转失败
- number 数量
- created 创建时间


### 10. 币币账户向法币账户转币历史记录

#### uri: /web/apiaccount/toc2clist

#### method: post

参数说明：
- coin 币种
- cur 页码


返回数据示例：

```

{
    "status":0,
    "msg":{
        "page":[
        {
            "id":"9",
            "uid":"10001",
            "type":"1",
            "status":"1",
            "number":"100.00000000",
            "created":"1562270464",
            "createip":"3232252417",
            "updated":"0",
            "updateip":"0"
        },
        ...
        ],
        "next":1,
        "before":1,
        "last":1,
        "current":1,
        "totalItems":"3",
        "totalPages":1
    }
}

```

返回数据说明：（同上）




### 11. 挖矿账户向法币账户转币历史记录

#### uri: /web/apiaccount/fromminelist

#### method: post

参数说明：
- coin 币种
- cur 页码


返回数据示例：

```
{
    "status":0,
    "msg":{
        "page":[
        {
            "id":"9",
            "uid":"10001",
            "type":"1",
            "status":"1",
            "number":"100.00000000",
            "created":"1562270464",
            "createip":"3232252417",
            "updated":"0",
            "updateip":"0"
        },
        ...
        ],
        "next":1,
        "before":1,
        "last":1,
        "current":1,
        "totalItems":"3",
        "totalPages":1
    }
}

```

返回数据说明：（基本同上，区别如下）
- type: 0 币币账户转到挖矿账户，1 挖矿账户转到币币账户。



### 12. 挖矿收益记录

#### uri: /web/apiaccount/getProfitList

#### method: post

参数说明：
- coin 币种
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
                "updated":"0"
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
                "updated":"0"
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
- type: 0 交易返佣，1 锁定释放，2 锁定释放-直接邀请人，3 锁定释放-间接邀请人 10 交易返佣-直接邀请人 11 交易返佣-间接邀请人
- status: 
