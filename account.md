
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


### 1-1. 用户资产-获取

#### uri: /web/apiaccount/keylist

#### method: post

参数说明：
- type 账户类型。trade：币币账户，mine: 挖矿账户，c2c/otc：otc账户（c2c与otc是同样的含义）。一般而言，币币账户与挖矿账户包含全币种，otc账户只包含otc币种，目前只有usdt。


返回数据示例：

```
// 当未指定type或者type无法识别时
{
    "status":0,
    "msg":"success",
    "data":
    [
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
            "rate":"0.001",
            "coin":"ETH",
        },
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
            "rate":"0.001",
            "coin":"BTC",
        },
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
            "rate":"0.001",
            "coin":"USDT",
        }
    ],
    "extra": {
        "sumusdt": "82566818.00",
        "sumcny": "591178416.88"
    }
}

// 当指定了type时，只返回type指定的资产信息. type = c2c
{
    "status":0,
    "msg":"success",
    "data":
    [
        {
            "uid":"10004",
            "balance":"10000.0000",
            "lock":"0.0000",
            "to_lock":"0.0000",
            "from_lock":"0.0000",
            "rate":"0.001",
            "coin":"USDT",
        },
    ],
    "extra": {
        "sumusdt": "82566818.00",
        "sumcny": "591178416.88"
    }
}

```

返回数据说明：
基本同上，指定了账户类型时，返回的balance与lock都是指定账户类型的余额与冻结。
to_lock与from_lock同上方接口返回的toc2c_lock与fromc2c_lock.
- extra 表示额外的数据，这里是相应账户里的总资产折合。type未指定时表示全部，type = c2c时表示c2c账户总资产，type=mine表示挖矿账户，trade表示交易账户；
- sumusdt 表示折合usdt
- sumcny 表示折合cny


### 1-2. 用户资产-获取，基本数据同上，返回数据格式有点区别

#### uri: /web/apiaccount/keylistv2

#### method: post

参数说明：
- type 账户类型。trade：币币账户，mine: 挖矿账户，c2c/otc：otc账户（c2c与otc是同样的含义）。一般而言，币币账户与挖矿账户包含全币种，otc账户只包含otc币种，目前只有usdt。


返回数据示例：

```
// 当未指定type或者type无法识别时
{
    "status":0,
    "msg":"success",
    "data":
    {
        "list":
        [
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
                "rate":"0.001",
                "coin":"ETH",
            },
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
                "rate":"0.001",
                "coin":"BTC",
            },
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
                "rate":"0.001",
                "coin":"USDT",
            }
        ],
        "sum": {
            "sumusdt": "82566818.00",
            "sumcny": "591178416.88"
        }
    }
}

// 当指定了type时，只返回type指定的资产信息. type = c2c
{
    "status":0,
    "msg":"success",
    "data":
    {
        "list":
        [
            {
                "uid":"10004",
                "balance":"10000.0000",
                "lock":"0.0000",
                "to_lock":"0.0000",
                "from_lock":"0.0000",
                "rate":"0.001",
                "coin":"USDT",
            },
        ],
        "sum": {
            "sumusdt": "82566818.00",
            "sumcny": "591178416.88"
        }
    }
}

```

返回数据说明：
基本同上，指定了账户类型时，返回的balance与lock都是指定账户类型的余额与冻结。
to_lock与from_lock同上方接口返回的toc2c_lock与fromc2c_lock.
- extra 表示额外的数据，这里是相应账户里的总资产折合。type未指定时表示全部，type = c2c时表示c2c账户总资产，type=mine表示挖矿账户，trade表示交易账户；
- sumusdt 表示折合usdt
- sumcny 表示折合cny


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
        "bankid":2,
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

返回数据说明：
- alipay 支付宝账号
- askrate 卖出费率
- askratelevel 卖出费率等级
- bidrate 买入费率
- bidratelevel 买入费率等级
- binding 启用的支付方式（暂不用）
- bound 已设置的支付方式，1表示银行，2表示支付宝，4表示微信。3 = 1 + 2 表示同时绑定了银行卡和支付宝
- bankid 银行id（内部id）
- bank 银行名称
- branch 支行名称
- card 银行卡号
- ctype 用户类型，1表示普通用户，2表示商户。商户可以定价，普通用户只能以市场价下单
- dealcount 累计成交笔数
- wechatid 绑定的微信账号


### 6-0. 资产账户间互转（以下6，7，8接口的集成接口）

#### uri: /web/apiaccount/transfer

#### method: post

参数说明：
- coin 币种
- type 划转类型。toc2c: 从币币账户转向otc账户，fromc2c: 从otc账户转向币币账户，frommine: 从挖矿账户转到币币账户. c2c相关的划转当前只支持usdt币种。
- number 数量


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data": {newid}
}

```

返回数据说明：(略)


### 6. 币币账户向法币账户转币

#### uri: /web/apiaccount/toc2c

#### method: post

参数说明：
- coin 币种
- number 数量


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
- coin 币种, 可选，如果留空也返回所有
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
            "coin":"btc",
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
- type: 0 交易返佣，1 锁定释放，2 锁定释放-直接邀请人，3 锁定释放-间接邀请人 10 交易返佣-直接邀请人 11 交易返佣-间接邀请人
- status: 0 待处理，1 已完成


### 13. c2c与币币账户间的转币记录

#### uri: /web/apiaccount/c2ctranslist

#### method: post

参数说明：
- coin 币种，现在只支持usdt
- cur 页码，一页10条。目前不支持自定义条数

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
            "type_desc":"转出",
            "status":"1",
            "status_desc":"成功",
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

参数说明：
- type 0 表示转入c2c账户，1 表示转出自c2c账户。前端可以直接使用type_desc来获取类型描述。
- status 0 表示处理中，1表示处理成功，2表示已取消，3表示处理失败。前端直接使用status_desc来获取状态描述。

### 14. 获取邀请数量

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


### 15. 获取活动收益记录

#### uri: /web/apiaccount/getActlogList

#### 请求方法：post

参数说明：

- cur: 页码

返回示例：
```

{
    "status": 0,
    "data": {
        "page": [
            {
                "id": "12",
                "uid": "10002",
                "actid": "1",
                "category": "10",
                "coin": "zyc",
                "status": "1",
                "number": "8000.00000000",
                "remark": "",
                "created": "1563072451",
                "createip": "0",
                "updated": "0",
                "updateip": "0",
                "act_name": "活动名称",
                "category_desc": "注册赠送",
                "status_desc": "已发放"
            }
        ],
        "next": 1,
        "before": 1,
        "last": 1,
        "current": 1,
        "totalItems": "1",
        "totalPages": 1
    }
}

```

返回说明：
- category 类别，见category_desc的内容即可
- status 状态，见status_desc的内容即可
- coin 赠送的币种
- number 赠送的币数量


### 16. 撤消从币币账户向c2c账户的划转申请。

目前只有从币币账户向c2c账户转币才会有等待期和撤消操作，其它划转都是立即生效。

#### uri: /web/apiaccount/cancelToC2c

#### 请求方法：post

参数说明：
- coin， 币种，目前只支持usdt
- id, 要撤消的申请记录的id

返回示例：

```

{
    "status":0,
    "msg":"success"
}


```