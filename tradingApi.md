### 1.用户资产-获取 webApiaccountList
#### **请求url:**http://code.local.com/web/apiaccount/list
#### **请求方式:**post
#### **参数：**

#### **返回参数：**
    msg: "获取用户资产成功"
    status: 0
    data: {eth: {uid: "10001", balance: "10000.0000", lock: "0.0000", c2clock: "0.0000",…},…}
    btc: {coin: "BTC", uid: "10001", balance: "7242.1691", lock: "2752.8797", otherlock: "0.000000000000000000",…}
        balance: "7242.1691"
        c2clock: "2752.8797"
        coin: "BTC"
        lock: "2752.8797"
        otherlock: "0.000000000000000000"
        rate: "0.001"
        ratelevel: "0"
        total: "9995.0489"
        uid: "10001"
    cnha: {uid: "10001", balance: "9960.0000", lock: "0.0000", c2clock: "0.0000", otherlock: "0.000000000000",…}
    eth: {uid: "10001", balance: "10000.0000", lock: "0.0000", c2clock: "0.0000",…}
    usdt: {coin: "USDT", uid: "10001", balance: "4665874.4046", lock: "94841653.4000",…}


### 2.kline数据  webKlineData
#### **请求url:**http://code.local.com/mdata/kline/
#### **请求方式:**get

#### **返回参数：**


### 3.挂单 webApiEntrust
#### **请求url:**http://code.local.com/web/apimarket/entrust
#### **请求方式:**post

#### **返回参数：**


### 4.撤单 webApiCancelTrust
#### **请求url:**http://code.local.com/web/apimarket/cancel
#### **请求方式:**post

#### **返回参数：**


### 5.委托列表 webApiTrustlist
#### **请求url:**http://code.local.com/web/apimarket/trustlist
#### **请求方式:**post
#### **参数：**
    board: this.pair[0],
    coin: this.pair[1]

#### **返回参数：**
    status: 0
    data: {,…}
    active: {page: [,…], next: 2, before: 1, last: 61, current: 1, totalItems: "1201", totalPages: 61,…}
        before: 1
        current: 1
        last: 61
        next: 2
        page: [,…]
        0: {id: "203", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
            amount: "0.000000000000"
            category: "0"
            category_desc: "否"
            created: "2019-05-20 15:00:13"
            createip: "2130706433"
            deal: "0.000000000000"
            from: "0"
            id: "203"
            price: "5785.00000000"
            remain: "1.10750000"
            status: "1"
            status_desc: "交易中"
            total: "1.10750000"
            type: "1"
            type_desc: "卖出"
            uid: "10001"
            updated: "0"
            updateip: "0"
        1: {id: "359", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        2: {id: "400", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        3: {id: "445", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        4: {id: "462", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        5: {id: "478", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        6: {id: "499", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        7: {id: "543", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        8: {id: "568", uid: "10001", from: "0", category: "0", amount: "0.000000000000", deal: "0.000000000000",…}
        totalItems: "1201"
        totalPages: 61
        where: "`uid`=10001 and `status`=1"
    old: {page: [,…], next: 2, before: 1, last: 1240, current: 1, totalItems: "24798", totalPages: 1240,…}


### 6.成交列表 webApiDeallist
#### **请求url:**http://code.local.com/web/apimarket/deallist
#### **请求方式：**post
#### **参数：**
    board: this.pair[0],
    coin: this.pair[1]

#### **返回参数：**
    status: 0
    data: {page: [], next: 1, before: 1, last: 1, current: 1, totalItems: "0", totalPages: 1}
        before: 1
        current: 1
        last: 1
        next: 1
        page: []
        totalItems: "0"
        totalPages: 1

### 7.全局委托数据 webTrustAll
#### **请求url:**http://code.local.com/mdata/trust/
#### **请求方式:**get
#### **参数:**

#### **返回参数:**

### 8.全局成交数据 webDealAll
#### **请求url:**http://code.local.com/mdata/deal/
#### **请求方式:**get
#### **参数：**

#### **返回参数:**





