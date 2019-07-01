
### 1. 交易市场

#### uri: /web/index/c2centrustlist

#### method: post

参数说明：
- board 交易区
- coin 币种


返回数据示例：

```
{
    "status":0,
    "data":[
        {
            "id":"19",
            "uid":"10001",
            "type":"1",
            "paytype":"银行卡",
            "targettid":"0",
            "total":"200000.0000",
            "minmatch":"300.0000",
            "remain":"195000.0000",
            "price":"7.0100",
            "status":"1",
            "created":"2019-06-24 06:38:51",
            "createip":"3232252417",
            "updated":"0",
            "updateip":"0",
            "mate_name":"**(52分钟)",
            "type_desc":"买入",
            "dealcount":1,
            "dealtime":"15分钟",
            "status_desc":"已支付"
        },
        {
            "id":"18",
            "uid":"10001",
            "type":"1",
            "paytype":"支付宝",
            "targettid":"0",
            "total":"200000.0000",
            "minmatch":"300.0000",
            "remain":"192000.0000",
            "price":"6.8900",
            "status":"2",
            "created":"2019-06-24 06:38:24",
            "createip":"3232252417",
            "updated":"0",
            "updateip":"0",
            "mate_name":"**(52分钟)",
            "type_desc":"卖出",
            "dealcount":1,
            "dealtime":"15分钟",
            "status_desc":"已确认"
        }
    ]
}

```

返回数据说明：
- id 记录 id
- uid 用户uid
- type 类型，0 买 1卖
- paytype 支付方式，逗号分隔的支付方式，有三种：银行卡、支付宝、微信
- targettid 目标挂单id，定向吃单的时候传此值
- total 总量
- minmatch 最小匹配量
- remain 剩余量
- price 价格
- status 状态码
- created 创建时间（北京时间）
- createip 创建ip（int类型需要自行转换）
- updated 更新时间（时间戳）
- updateip 更新ip
- mate_name 挂单人姓名（打码）
- type_desc 挂单类型描述（买入/卖出）
- dealcount 已成交数量
- dealtime 平均成交时间
- status_desc 状态描述

### 2. 挂单

#### uri: /web/apic2cmarket/entrust

#### method: post

参数说明：
- board 交易区
- coin 币种
- targetid 交易目标挂单id
- type 类型，0 买 1 卖
- paytype 支付类型，1 => 银行卡，2 => 支付宝，4 => 微信；5 = 1 + 4 表示支付银行卡与微信
- number 数量
- price 价格，若是普通用户挂单，价格以实时价格成交，未必是显示的价格
- roletype 成交角色。如果用户是商户，商户可以选择以普通用户身份挂单; 1 表示普通用户身份，2 表示商户身份
- password 交易密码


返回数据示例：

```
{
    "status":0,
    "msg":"success",
    "data": "{挂单id}"
}
```

### 3. 撤单

#### uri: /web/apic2cmarket/cancel

#### method: post

参数说明：
- id 撤单id
- board 交易区
- coin 交易币种


返回数据示例：

```
{
    "status":0,
    "msg":""
}

```

### 4. 我的待处理成交

#### uri: /web/apic2cmarket/newdeal

#### method: post

参数说明：
- board 交易区
- coin 交易币种


返回数据示例：

```
{
    "status":0,
    "data":[
        {
            "id":"2",
            "amount":"13780.00000000",
            "price":"6.8900",
            "number":"2000.0000",
            "paytype":"1",
            "status":"1",
            "complain":"0",
            "taker":"0",
            "bid_tid":"16",
            "bid_uid":"10001",
            "bid_fee":"0.0000000000",
            "ask_tid":"11",
            "ask_uid":"10002",
            "ask_fee":"0.0000000000",
            "paytime":1561711336000,
            "confirmtime":"0",
            "created":1561374279000,
            "updated":"1561711336",
            "type":0,
            "type_desc":"买入",
            "againstuid":"10002",
            "status_desc":"已支付",
            "mate_name":"李四",
            "wechat_img":"http://testapi.bitmagic.pro/payinfo/image/317575fc3e99eba11ef8ccc001dd59d4/wechat.gif",
            "alipay_img":"http://testapi.bitmagic.pro/payinfo/image/317575fc3e99eba11ef8ccc001dd59d4/alipay.gif",
            "bank":"某某某银行",
            "bank_code":"4444444444444444"
        }
    ]
}

```

返回数据说明：
- amount 成交额
- price 成交价
- number 成交量
- paytype 支付方式。1 => 银行卡，2 => 支付宝，4 => 微信；5 = 1 + 4 表示同时支持银行卡和微信 
- status 状态码
- status_desc 状态描述
- complain 是否申诉
- taker taker类型，0 买，1 卖
- bid_tid 买方挂单id
- bid_uid 买方uid
- bid_fee 买手续费
- ask_tid 卖单id
- ask_uid 卖方uid
- ask_fee 卖手续费
- paytime 确认支付时间
- confirmtime 确认收款时间
- created 创建时间
- updated 更新时间
- type 类型 0 买 1 卖
- type_desc 类型描述
- againstuid 对手uid
- mate_name 对手姓名
- wechat_img 微信二维码url，需要带token访问
- alipay_img 支付宝二维码url，需要带token访问
- bank 银行名
- bank_code 银行卡号

### 5. 成交确认。确认支付与确认收款都是这个方法

#### uri: /web/apic2cmarket/confirm

#### method: post

参数说明：
- board 交易区
- coin 交易币种
- id 确认单id
- type 0 表示确认支付， 1 表示确认收款


返回数据示例：

```
{
    "status":0,
    "msg":"success"
}
```

### 6. 成交撤消。只有买方用户可以撤单。

#### uri: /web/apic2cmarket/dealcancel

#### method: post

参数说明：
- board 交易区
- coin 交易币种
- id 撤单id


返回数据示例：

```
{
    "status":0,
    "msg":""
}
```

### 7. 我的委托列表

#### uri: /web/apic2cmarket/trustlist

#### method: post

参数说明：
- 


返回数据示例：

```

{
    "status":0,
    "data":{
        "active":{
            "page":[
                {
                    "id":"51988",
                    "uid":"10001",
                    "from":"0",
                    "category":"0",
                    "amount":"0.000000000000",
                    "deal":"0.000000000000",
                    "type":"0",
                    "total":"2.00000000",
                    "remain":"2.00000000",
                    "price":"970.00000000",
                    "status":"1",
                    "created":"2019-06-25 14:50:48",
                    "createip":"2890171783",
                    "updated":"0",
                    "updateip":"0",
                    "category_desc":"否",
                    "type_desc":"买入",
                    "status_desc":"交易中"
                },
                ...
            ],
            "next":2,
            "before":1,
            "last":60,
            "current":1,
            "totalItems":"1197",
            "totalPages":60
        },
    }
}

```

### 8. 我的历史成交列表

#### uri: /web/apic2cmarket/deallist

#### method: post

参数说明：
- type 类型，0 买 1 卖
- board 交易区
- coin 交易币种
- p 页码
- size 页内数据数量


返回数据示例：

```
{
    "status":0,
    "data":
    {
        "page":[
            {
                "id":"2",
                "amount":"13780.00000000",
                "price":"6.8900",
                "number":"2000.0000",
                "paytype":"1",
                "status":"1",
                "complain":"0",
                "taker":"0",
                "bid_tid":"16",
                "bid_uid":"10001",
                "bid_fee":"0.0000000000",
                "ask_tid":"11",
                "ask_uid":"10002",
                "ask_fee":"0.0000000000",
                "paytime":"1561711336",
                "confirmtime":"0",
                "created":1561374279000,
                "updated":1561711336000,
                "mate_name":"王五",
                "type":0,
                "type_desc":"买入",
                "againstuid":"10002",
                "status_desc":"交易中"
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
