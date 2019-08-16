
### 1. 挂单

#### uri: /web/apic2cmarket/entrust

前置条件：高级实名认证；需要设置收款方式；
其它约束：如果一天内撤消了5次成交，日内将不再允许挂单；如果有3笔未处理完成的订单（不包括申诉单）,不允许挂单。

#### method: post

参数说明：
- board 交易区
- coin 币种
- targetid 交易目标挂单id，只有定向吃单的时候才有用。
- type 类型，0 买 1 卖
- paytype 支付类型，1 => 银行卡，2 => 支付宝，4 => 微信；5 = 1 + 4 表示支付银行卡与微信
- number 数量, 目前配置是最少50个。
- price 价格，若是普通用户挂单，价格以实时价格成交，未必是显示的价格
- roletype 成交角色。如果用户是商户，商户可以选择以普通用户身份挂单; 1 表示普通用户身份，2 表示商户身份
- password 交易密码，输入正确一次后，半小时内不需要重新输入
- min 商家挂单要求的最小成交量。商家挂单时必须，而且不能大于number。


返回数据示例：

```
{
    "status":0,
    "msg":"success",
    "data": "{挂单id}"
}
```

### 2. 撤单

#### uri: /web/apic2cmarket/cancel

约束：目前只有商户可以撤消挂单

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

### 3. 成交确认。确认支付与确认收款都是这个方法

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

### 4. 成交撤消。只有买方用户在确认付款前可以撤单。

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

### 5. 我的委托列表

#### uri: /web/apic2cmarket/trustlist

#### method: post

参数说明：
- board 交易区，目前只有cny
- coin 交易币种，目前只有usdt
- p 页码
- size 页面大小
- status 列表类型，active表示进行中的，old表示历史的（包括已完成和已撤消的）记录
- type 买/卖。空表示买+卖，0表示买，1表示卖


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
                    "minmatch":1000,
                    "total": 30000,
                    "paytype":3,
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

参数说明：
- paytype 表示下单方接收的收款/支付方式。对买方而言，表示其支持的付款方式；对卖方而言，表示其接受的收款方式。成交时，只有paytype有交集的挂单才可以成交。
- type 0 => 买, 1 => 卖
- minmatch 挂单方要求的最小成交限额
- total 总量
- remain 剩余量

### 6. 我的待处理成交

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
            "bank_code":"4444444444444444",
            "mate_mobile":""
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
- mate_mobile 对方的手机号，只有买方确认付款后，半小时对方仍未确认收款的情况下，才不为空，否则内容为空。客户端可以简单处理为：如果mate_mobile为空则不展示，如果不为空，则展示。

### 7. 我的历史成交列表

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

### 8. 我的成交详情

#### uri: /web/apic2cmarket/dealinfo

#### method: post

参数说明：
- board 交易区，目前cny
- coin 币种，目前都是usdt
- id 成交id


返回示例

```

{
    "status":0,
    "data":
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
        "wechatid":"xxxxx",
        "wechat_img":"http://testapi.bitmagic.pro/payinfo/image/317575fc3e99eba11ef8ccc001dd59d4/wechat.gif",
        "alipay":"xxxxxxx",
        "alipay_img":"http://testapi.bitmagic.pro/payinfo/image/317575fc3e99eba11ef8ccc001dd59d4/alipay.gif",
        "bank":"某某某银行",
        "bank_code":"4444444444444444",
        "mate_mobile":""
    }
}
```

### 9. 获取商户成交统计信息

#### uri: /web/apic2cmarket/merchantInfo

#### **请求方式：**post

请求参数
- board 交易区，通常是cny
- coin 交易币种，目前只有usdt
- uid 用户uid
- wechatid 微信号
- alipay 支付宝账号


返回示例

```

{
    "status": 0,
    "data": {
        "num": 15,
        "time": "11秒",
        "ptime": 580423
    }
}

```

返回说明

- num 历史成交笔数
- time 平均成交用时
- ptime 暂时没用