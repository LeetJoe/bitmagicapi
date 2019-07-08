### 2.撤单 webApiCancelTrust
#### **请求url:**/web/apimarket/cancel
#### **请求方式:**post

#### **返回参数：**


### 3.委托列表 webApiTrustlist
#### **请求url:**/web/apimarket/trustlist
####  ** 请求方式: ** post
#### **参数：**
    board: this.pair[0],
    coin: this.pair[1],
    status: null 或 空串：全部；active: 处理中；old: 处理完毕

#### **返回参数：**
    status: 0
    data: {
        before: 1
        current: 1
        last: 61
        next: 2
        page: 
        {
            id: 123
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
        }
        totalItems: "1201"
        totalPages: 61
        where: "`uid`=10001 and `status`=1"
    }
}

### 4.我的成交列表 webApiDeallist
#### ** 请求url: ** /web/apimarket/deallist
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

### 5. 交易挂单

#### uri: /web/apimarket/entrust

#### method: post

参数说明：
- board 交易区
- coin 币种
- category 是否市价单，0 非市价单，1 市价单
- type 类型，0 买，1 卖
- amount 金额，仅市价买单有效
- number 下单数量，市价买单时无意义
- price 价格，市价单时无意义

返回示例：
```
{
    status: 0,
    msg: 'success'
}

```



