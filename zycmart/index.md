### 1. 图片验证码

#### uri: /web/index/imgcode

#### 请求方法：get

返回数据示例：(无)


### 2. 国家列表

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

### 2-1. 国家列表

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


### 3. 找回密码

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


### 4. 获取zyc实时价格走势

#### uri: /web/index/ticker

#### 请求方法： get/post

#### 请求参数：无

返回示例：

```
{
    "status": 0,
    "data": [
        {
            "id": "25",
            "price": "0.1505",
            "created": "1567947360"
        },
        {
            "id": "24",
            "price": "0.1505",
            "created": "1567947300"
        },
        ...
    ]
}
```

### 5. 获取提币额度

#### uri: /web/index/outlimit

#### method: post

返回示例：

```
{
    "status":0,
    "data":[
        {
            "id":"1",
            "coin":"zyc",
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
            "coin":"zyc",
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
            "coin":"zyc",
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
            "coin":"zyc",
            "level":"3",
            "vip":"0",
            "single":"50000.00",
            "day":"200000.00",
            "week":"1000000.00",
            "month":"3000000.00",
            "nation":"0",
            "status":"0",
            "updated":"0"
        }
    ]
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

```

{
    "status": 0,
    "msg": "success",
    "data": {
        "key": "zyc",
        "name": "ZYC",
        "enname": "zyc",
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

