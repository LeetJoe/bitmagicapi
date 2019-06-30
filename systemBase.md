### 1. 交易区列表

#### uri: /web/index/boards

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

### 2. 币种列表

#### uri: /web/index/coins

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

### 3. 交易对配置信息

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

### 4. 国家列表

#### uri: /web/index/country

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

### 5. 银行列表

#### uri: /web/index/banklist

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

### 6. 图片验证码

#### uri: /web/index/imgcode

返回数据示例：(无)



### 4. 实时牌价

#### uri: /web/index/ticker/{market}

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
                "11820.51000000"
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
                "301.37000000"
            ]
        }
    }
}

```

返回数据说明：
- [status, msg, data] 是标准api返回，status 为 0 表示返回成功，msg 为提示消息，data 为返回数据内容。
- xxxx_uptime 是指交易区数据更新时间；
- usdt 表示的是交易区；当通过参数指定了交易区时，返回格式里将没有这一层数据；
- usdt 下层的数据表示交易区内各币种的信息；当通过参数指定了交易区时，返回数据里将没有这一层数据；
- 详细数据含义为： [最新价, 买一价, 卖一价, 最高价, 最低价, 成交量, 成交额, 昨日(24h前)收盘价, 今日(24h前)开盘价]. 


### 5. c2c实时牌价

#### uri: /web/index/c2cticker

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

