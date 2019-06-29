### 1. 获取全局挂单列表

#### uri: /mdata/trust/{market}/{coin}

- market 是指交易区，如usdt交易区；
- coin 是指交易币种，如btc；

例：要取得最近的usdt_btc交易对的挂单列表，需要使用uri: /mdata/trust/usdt/btc

数据格式示例：

```

{
    bid: 
        [
            901,
            1,
            1
        ],
        [
            900,
            2,
            3
        ],
        [
            899,
            3,
            6
        ]
    ask:
        [
            902,
            1,
            1
        ],
        [
            903,
            2,
            3
        ],
        [
            904,
            3,
            6
        ]
}
    
```

说明：
- bid表示买单，ask表示卖单；
- 每一组三个数字分别代表:价格，数量，累加量。其中买单价格按倒序排，卖单是正序排；累加量为按照此排序，从第一单到当前单累加的挂单数量。



### 2. 获取全局成交列表

#### uri: /mdata/deal/{market}/{coin}

- market 是指交易区，如usdt交易区；
- coin 是指交易币种，如btc；

例：要取得最近的usdt_btc交易对的成交，需要使用uri: /mdata/deal/usdt/btc

### 3. 获取k线数据

#### uri: /mdata/kline/{market}\_{coin}\_{resolution}

- market是指交易区，比如usdt交易区；
- coin是指交易币种，比如btc；
- resolution是指k线的时间间隔。

例：要取得usdt交易区btc的5分钟k线数据，需要使用 uri: /mdata/kline/usdt_btc_5m

支持的resolution有：
1m, 5m, 15m, 30m, 1h, 8h, 1d

k线数据暂时不支持增量获取。


