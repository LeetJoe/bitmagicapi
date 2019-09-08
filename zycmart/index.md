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