### 1. 图片验证码

#### uri: /web/index/imgcode

#### 请求方法：get

返回数据示例：(无)

### 2. 币种列表

#### uri: /web/index/coins

#### 请求方法：post

返回数据示例：
```
{
    status: 0,
    msg: "success",
    data: [
        "eth",
        "btc",
        "usdt",
        "mco"
    ]
}

```


### 3. 交易区列表

#### uri: /web/index/boards

#### 请求方法：post

返回数据示例：
```
{
    status: 0,
    msg: "success",
    data: {
        btc: [
            "eth"
        ],
        usdt: [
            "eth",
            "btc"
        ],
        eth: [
            "btc"
        ]
    }
}
```

### 3-1. 交易区列表

#### uri: /web/index/keyboards

#### 请求方法：post

返回数据示例：
```
{
    status: 0,
    msg: "success",
    data: [
        {
            name: btc,
            coins: [
                eth,
                zyc
            ]
        },
        {
            name: eth,
            coins: [
                btc,
                zyc
            ]
        }
    ]
}
```

### 4. 交易对配置信息

#### uri: /web/index/coinconf/board/{board}/coin/{coin}

参数说明：
- board: 交易区
- coin: 交易币种

返回数据示例：

```

{
    status: 0,
    msg: "success",
    data: {
        key: "btc",
        board: "usdt",
        decprice: "2",
        decnumber: "4",
        minamount: "10.000000",
        minmarketask: "0.0001000000",
        minprice: "0.000100000000",
        maxprice: "99999999.000000",
        minnumber: "0.0000010000",
        maxnumber: "999999.000000",
        pstep: "5.0000000000",
        apitrust: "1",
    }
}

```

返回数据说明：

|  参数  |  说明  |
| ---- | ---- |
| key | coin |
| board | 交易区 |
| decprice | 价格精度（小数位数） |
| decnumber | 数量精度（小数位数） |
| minamount | 最小挂单额 |
| minmarketask | 市价单最小卖出量 |
| minprice | 最小允许挂单价格 |
| maxprice | 最大允许挂单价格 |
| minnumber | 最小允许挂单数量 |
| maxnumber | 最大允许挂单 |
| pstep | 挂单价格步长 |
| apitrust | 是否开启api挂单 |


### 5. 实时牌价

#### uri: /web/index/ticker/board/{market}

#### 请求方法：post

参数说明：
- market 表示交易区，如果不传，将返回全部数据。

返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":{
        "usdt_uptime":1561880556.986,
        "usdt":
        {
            "btc":[
                11727.07,
                990,
                1000,
                12230,
                11605,
                2636,
                31539809,
                "11820.51000000",
                "11820.51000000",
                "82089.4900"
            ],
            "eth":[
                310.44,
                123,
                111111,
                324.62,
                297.96,
                70265,
                21963190,
                "301.37000000",
                "301.37000000",
                "2137.0800"
            ]
        }
    }
}

// 当传了 board 参数时

{
    "status":0,
    "msg":"success",
    "data":{
        "btc":[
            11727.07,
            990,
            1000,
            12230,
            11605,
            2636,
            31539809,
            "11820.51000000",
            "11820.51000000",
            "82089.4900"
        ],
        "eth":[
            310.44,
            123,
            111111,
            324.62,
            297.96,
            70265,
            21963190,
            "301.37000000",
            "301.37000000",
            "2137.0800"
        ]
    }
}

```

返回数据说明：
- [status, msg, data] 是标准api返回，status 为 0 表示返回成功，msg 为提示消息，data 为返回数据内容。
- xxxx_uptime 是指交易区数据更新时间；
- usdt 表示的是交易区；当通过参数指定了交易区时，返回格式里将没有这一层数据；
- usdt 下层的数据表示交易区内各币种的信息；当通过参数指定了交易区时，返回数据里将没有这一层数据；
- 详细数据含义为： [最新价, 买一价, 卖一价, 最高价, 最低价, 成交量, 成交额, 昨日(24h前)收盘价, 今日(24h前)开盘价, 实时cny折合价]. 


### 5-1. 实时牌价

#### uri: /web/index/keyticker/board/{market}

#### 请求方法：post

参数说明：
- market 表示交易区，如果不传，将返回全部数据。

返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":[
        {
            board: "usdt",
            coins: [
                {
                    coin: btc,
                    data: {
                        p: 11727.07,
                        b: 990,
                        a: 1000,
                        h: 12230,
                        l: 11605,
                        n: 2636,
                        v: 31539809,
                        e: "11820.51000000",
                        s: "11820.51000000",
                        c: "82089.4900"
                    }
                },
                {
                    coin: eth,
                    data: {
                        p: 310.44,
                        b: 123,
                        a: 111111,
                        h: 324.62,
                        l: 297.96,
                        n: 70265,
                        v: 21963190,
                        e: "301.37000000",
                        s: "301.37000000",
                        c: "2137.0800"
                    }
                }
                ...
            ]
        },
        ...
    ]
}

// 当传了 board 参数时

{
    "status":0,
    "msg":"success",
    "data":[
        {
            coin: btc,
            data: {
                p: 11727.07,
                b: 990,
                a: 1000,
                h: 12230,
                l: 11605,
                n: 2636,
                v: 31539809,
                e: "11820.51000000",
                s: "11820.51000000",
                c: "82089.4900"
            }
        },
        {
            coin: eth,
            data: {
                p: 310.44,
                b: 123,
                a: 111111,
                h: 324.62,
                l: 297.96,
                n: 70265,
                v: 21963190,
                e: "301.37000000",
                s: "301.37000000",
                c: "2137.0800"
            }
        }
        ...
    ]
}

```

返回参数说明：同上
- p price，最新价
- b bid one，买1价
- a ask one, 卖1价
- h high，最高价
- l low，最低价
- n number, 成交量
- v volumn，成交额
- e end, 昨日收盘价
- s start, 今日开盘价
- c cny price, 人民实时价


### 6. c2c实时牌价

#### uri: /web/index/c2cticker/board/{market}

#### 请求方法：post

参数说明：
board 交易区，可选。目前只有cny交易区。

返回数据示例：

```
{
    status: 0,
    msg: "success",
    data: {
        cny_uptime: 1561883418.3795,
        cny: {
            usdt: {
                yprice: "6.8900",
                latest: "6.8900",
                max: 0,
                min: 0,
                bidone: "7.0000",
                askone: "6.8900"
            }
        }
    }
}

// 当传了board参数时
{
    status: 0,
    msg: "success",
    data: {
        usdt: {
            yprice: "6.8900",
            latest: "6.8900",
            max: 0,
            min: 0,
            bidone: "7.0000",
            askone: "6.8900"
        }
    }
}


```


返回参数说明：
- status, msg, data 是标准返回，可参考上文中关于实时牌价的说明；
- cny_update 表示交易区数据更新时间；
- cny 表示交易区；
- usdt 表示交易区内币种；
- yprice 昨日收盘价 (UTC+8)；
- latest 最新成交价；
- max 24h最高价；
- min 24h最低价；
- bidone 买一价；
- askone 卖一价；


### 6-1. c2c实时牌价

#### uri: /web/index/keyc2cticker/board/{market}

#### 请求方法：post

参数说明：
board 交易区，可选。目前只有cny交易区。

返回数据示例：

```
{
    status: 0,
    msg: "success",
    data: [
        {
            board: "cny",
            coins: [
                {
                    coin: "usdt",
                    data:[
                        yprice: "6.8900",
                        latest: "6.8900",
                        max: 0,
                        min: 0,
                        bidone: "7.0000",
                        askone: "6.8900"
                    ]
                }
                ...
            ]
        },
        ...
    ]
}

// 当传了board参数时
{
    status: 0,
    msg: "success",
    data: [
        {
            coin: "usdt",
            data:[
                yprice: "6.8900",
                latest: "6.8900",
                max: 0,
                min: 0,
                bidone: "7.0000",
                askone: "6.8900"
            ]
        }
        ...
    ]
}


```


返回参数说明：同上


### 7. 银行列表

#### uri: /web/index/banklist

#### 请求方法：post

返回数据示例：
```

{
    status: 0,
    msg: "success",
    data: {
        "中国银行",
        "中国农业银行",
        "中国建设银行",
        "中国工商银行",
        "招商银行",
        "交通银行",
        "中信银行",
        "光大银行",
        "华夏银行",
        "民生银行",
        "兴业银行",
        "广发银行",
        "平安银行",
        "浦发银行"
    }
}

```


### 8. 找回密码

#### uri: /web/index/findpw

#### 请求方法： post

#### 请求参数：
- email 邮箱地址，与ecode配合使用；
- ecode 邮箱验证码；
- mobile 手机号，与mcode配合使用；
- mcode 手机验证码；
- captcha 图片验证码，必须；
- password 新密码，必须；
- repassword 重新新密码，必须；

说明：其中email + ecode 和 mobile + mcode 两组选择任意一组即可。

返回示例：

```
{
    status: 0,
    msg: 'success',
}
```


### 9. 交易市场

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
- paytype 支付方式，1表示银行卡，2表示支付宝，4表示微信。 5 = 1 + 4 表示同时支持银行卡和支付宝。
- paytype_desc 支付方式，逗号分隔的支付方式，有三种：银行卡、支付宝、微信
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

### 9. 国家列表

#### uri: /web/index/country

#### 请求方法：post

返回数据示例：
```
{
    status: 0,
    msg: 'success',
    data: {
        AC: "阿森松岛",
        AD: "安道尔",
        AE: "阿拉伯联合酋长国",
        AF: "阿富汗",
        AG: "安提瓜和巴布达",
        AI: "安圭拉",
        AL: "阿尔巴尼亚",
    }
}
```

### 9-1. 国家列表

#### uri: /web/index/keycountry

#### 请求方法：post

返回数据示例：
```
{
    status: 0,
    msg: 'success',
    data: [
        {
            ab: "CN",
            name: "中国"
        },
        {
            ab: "AC",
            name: "阿森松岛"
        }
        ...
    ]
}
```


### 10. 获取提币额度

#### uri: /web/index/outlimit

#### method: post

参数说明：
- coin 币种，如果不传，则返回全部配置
- vip 是否vip, 0 否，1 是
- level 用户认证等级
- nation 国家，目前没用，固定传 0 即可


返回示例：

```
// 如果 coin 参数留空
{
    "status":0,
    "data":[
        {
            "id":"1",
            "coin":"usdt",
            "level":"0",
            "vip":"0",
            "single":"0.00",
            "day":"0.00",
            "week":"0.00",
            "month":"0.00",
            "nation":"0",
            "status":"0",
            "updated":"0"
        },
        {
            "id":"2",
            "coin":"usdt",
            "level":"1",
            "vip":"0",
            "single":"10000.00",
            "day":"30000.00",
            "week":"100000.00",
            "month":"300000.00",
            "nation":"0",
            "status":"0",
            "updated":"0"
        },
        {
            "id":"3",
            "coin":"usdt",
            "level":"2",
            "vip":"0",
            "single":"50000.00",
            "day":"150000.00",
            "week":"500000.00",
            "month":"1500000.00",
            "nation":"0",
            "status":"0",
            "updated":"0"
        },
        {
            "id":"4",
            "coin":"usdt",
            "level":"3",
            "vip":"0",
            "single":"50000.00",
            "day":"200000.00",
            "week":"1000000.00",
            "month":"3000000.00",
            "nation":"0",
            "status":"0",
            "updated":"0"
        },
        ...
    ]
}

// 如果 coin 参数不留空


{
    "status":0,
    "data":
    {
        "id":"2",
        "coin":"usdt",
        "level":"1",
        "vip":"0",
        "single":"10000.00",
        "day":"30000.00",
        "week":"100000.00",
        "month":"300000.00",
        "nation":"0",
        "status":"0",
        "updated":"0"
    }
}

```

返回数据说明：
- coin 币种
- level 用户认证等级
- vip 是否vip
- single 单次限额
- day 日限额
- week 周限额
- month 月限额


### 11. 获取币种配置

#### uri: /web/index/coininfo

#### method: post

参数说明：
- coin 币种，可选。

```

// 如果未指定coin参数：
{
    "status": 0,
    "msg": "success",
    "data": {
        "zyc": {
            "key": "zyc",
            "name": "ZYC",
            "enname": "",
            "tokenof": "eth",
            "sort": "0",
            "status": "0",
            "outstep": "0.0000000000",
            "minout": "10.0000000000",
            "outfee": "10.0000000000",
            "confirmnum": "12",
            "abstract": "",
            "form": "0",
            "explorer": "",
            "walleturl": "",
            "mainpage": "",
            "sourcecode": "",
            "consensus": "",
            "whitepaper": "",
            "feature": "",
            "shortage": "",
            "releasedate": "",
            "planindate": "",
            "planoutdate": "",
            "releaseamount": "",
            "blocktime": ""
        },
        "eth": {
            "key": "eth",
            "name": "以太坊",
            "enname": "",
            "tokenof": "",
            "sort": "0",
            "status": "0",
            "outstep": "0.0000000000",
            "minout": "0.1000000000",
            "outfee": "0.0300000000",
            "confirmnum": "12",
            "abstract": "",
            "form": "0",
            "explorer": "",
            "walleturl": "",
            "mainpage": "",
            "sourcecode": "",
            "consensus": "",
            "whitepaper": "",
            "feature": "",
            "shortage": "",
            "releasedate": "",
            "planindate": "",
            "planoutdate": "",
            "releaseamount": "",
            "blocktime": ""
        },
        "btc": {
            "key": "btc",
            "name": "比特币",
            "enname": "",
            "tokenof": "",
            "sort": "0",
            "status": "0",
            "outstep": "0.0000000000",
            "minout": "0.0001000000",
            "outfee": "0.0000400000",
            "confirmnum": "2",
            "abstract": "",
            "form": "0",
            "explorer": "",
            "walleturl": "",
            "mainpage": "",
            "sourcecode": "",
            "consensus": "",
            "whitepaper": "",
            "feature": "",
            "shortage": "",
            "releasedate": "",
            "planindate": "",
            "planoutdate": "",
            "releaseamount": "",
            "blocktime": ""
        },
        "usdt": {
            "key": "usdt",
            "name": "USDT",
            "enname": "usd tether",
            "tokenof": "",
            "sort": "1",
            "status": "0",
            "outstep": "0.0000000000",
            "minout": "100.0000000000",
            "outfee": "10.0000000000",
            "confirmnum": "36",
            "abstract": "",
            "form": "0",
            "explorer": "",
            "walleturl": "",
            "mainpage": "",
            "sourcecode": "",
            "consensus": "",
            "whitepaper": "",
            "feature": "",
            "shortage": "",
            "releasedate": "",
            "planindate": "",
            "planoutdate": "",
            "releaseamount": "",
            "blocktime": ""
        }
    }
}


// 如果指定了coin参数：

{
    "status": 0,
    "msg": "success",
    "data": {
        "key": "usdt",
        "name": "USDT",
        "enname": "usd tether",
        "tokenof": "",
        "sort": "1",
        "status": "0",
        "outstep": "0.0000000000",
        "minout": "100.0000000000",
        "outfee": "10.0000000000",
        "confirmnum": "36",
        "abstract": "",
        "form": "0",
        "explorer": "",
        "walleturl": "",
        "mainpage": "",
        "sourcecode": "",
        "consensus": "",
        "whitepaper": "",
        "feature": "",
        "shortage": "",
        "releasedate": "",
        "planindate": "",
        "planoutdate": "",
        "releaseamount": "",
        "blocktime": ""
    }
}

```

返回参数说明：
- key 币种名称，小写
- name 币种名称，大写
- enanme 英文名称
- tokenof 代币种类，如果不是代币，此字段为空
- sort 排序权重，数字越小越靠前
- status 状态，0表示有效，1表示无效。通常能得到数据的都是有效数据
- outstep 转出步长，转出金额的粒度，转出数量只能是这个数字的倍数，为0的话表示不限制
- minout 最小转出数量
- outfee 转出手续费
- confirmnum 入账确认数量，在转入币时，区块确认数量达到此数值之后才会进入用户可用余额
- abstract 币种简介
- form 存在形式，代币或者主链
- explorer 区块浏览器地址
- walleturl 钱包下载地址
- mainpage 项目主页
- sourcecode 项目源代码
- consensus 共识类型
- whitepaper 白皮书地址
- feature 主要特性
- shortage 不足之处
- releasedate 发行日期
- planindate 计划在平台中开启转入的时间
- planoutdate 计划在平台中开启转出的时间
- releaseamount 发行总量
- blocktime 区块时间


### 12. 获取人民币汇率

#### uri: /web/index/cnyrate

#### method: post/get

参数说明：无

返回示例：
```
{
    "status": 0,
    "data": [
        {
            "coin": "usdt",
            "price": "6.8900"
        },
        {
            "coin": "eth",
            "price": "1435.60"
        },
        {
            "coin": "btc",
            "price": "65523.41"
        },
        {
            "coin": "zyc",
            "price": "11.71"
        }
    ]
}

```