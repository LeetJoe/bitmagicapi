

### 1. 手机号-绑定

#### uri: /web/apisecurity/bindmobile

#### method: post

参数说明：
- mobile 手机号 
- ecode 邮箱号码
- mcode 手机号码
- ga 谷歌验证码（如果开启了ga验证）


返回数据示例：

```

{
    "status":0,
    "msg":"绑定手机成功"
}

// 失败情形示例

{
    "status":1,
    "msg":"该手机号码已经被占用"
}

// 如果开启了谷歌验证却没有提供ga参数，会返回状态码 7 

{
    "status":7,
    "msg":"谷歌验证码不能为空"
}


```
### 2. 手机号-修改

#### uri: /web/apisecurity/resetmobile

#### method: post

参数说明：
- oldcode 旧手机号验证码
- mobile 新手机号码
- code 新手机号验证码

返回数据示例：

```
{
    "status":0,
    "msg":"修改手机号码成功"
}
```


### 3. 邮箱-绑定

#### uri: /web/apisecurity/bindemail

#### method: post

参数说明：
- email 邮箱地址
- mcode 手机验证码
- ecode 邮箱验证码
- ga 谷歌验证码（如果开启了谷哥验证）


返回数据示例：

```

{
    "status":0,
    "msg":"绑定邮箱成功"
}

// 如果开启了谷歌验证却没有提供ga参数，会返回状态码 7 

{
    "status":7,
    "msg":"谷歌验证码不能为空"
}

```


### 4. 谷歌验证码-绑定

#### uri: /web/apisecurity/bindga

#### method: post

参数说明：
- secret 密码
- gcode 谷歌验证码
- code 手机/邮箱验证码,以注册方式为准，判断用户的 regtype,0 表示邮箱，1 表示手机


返回数据示例：

```

{
    "status":0,
    "msg":"绑定谷歌验证码成功"
}

```


### 4. 谷歌验证码-关闭

#### uri: /web/apisecurity/closega

#### method: post

参数说明：
- gcode 谷歌验证码
- code 手机/邮箱验证码,以注册方式为准，判断用户的 regtype,0 表示邮箱，1 表示手机


返回数据示例：

```

{
    "status":0,
    "msg":"关闭谷歌验证码成功"
}

```

### 5. 谷歌验证码-开启

#### uri: /web/apisecurity/openga

#### method: post

参数说明：
- gcode ga验证码
- code 手机/邮箱验证码,以注册方式为准，判断用户的 regtype,0 表示邮箱，1 表示手机


返回数据示例：

```

{
    "status":0,
    "msg":"启用谷歌验证码成功"
}

```

### 6. 谷歌验证码-修改

#### uri: /web/apisecurity/editga

#### method: post

参数说明：
- oldgcode 旧的ga验证码
- gcode 新的ga验证码
- secret 密码
- code 手机/邮箱验证码,以注册方式为准，判断用户的 regtype,0 表示邮箱，1 表示手机


返回数据示例：

```

{
    "status":0,
    "msg":"重置谷歌验证码成功"
}

```

### 7. 生成谷歌验证密钥

#### uri: /web/apisecurity/createga

#### method: post

参数说明：(无)


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":
    {
        "secret":"TST4V66KWDXRUU2Z",
        "qrCodeUrl":"otpauth://totp/testapi.bitmagic.pro?secret=TST4V66KWDXRUU2Z"
    }
}

```

返回参数说明：
- secret 密码
- qrcodeurl qr code url

### 8. 登录密码-修改

约束：如果半小时内密码输入错误最多5次，超过后要半小时后再试。

#### uri: /web/apisecurity/editpw

#### method: post

参数说明：
- oldpw 原登录密码
- newpw 新登录密码
- renewpw 重复新登录密码
- mcode 手机验证码，根据用户信息的regtype判断，如果是0，使用邮箱验证码，如果是1，使用手机验证码。
- ecode 邮箱验证码，见关于mcode的说明。
- ga 谷歌验证码（如果开启了谷哥验证）

返回数据示例：

```
{
    "status":0,
    "msg":"修改密码成功"
}

// 如果开启了谷歌验证却没有提供ga参数，会返回状态码 7 

{
    "status":7,
    "msg":"谷歌验证码不能为空"
}

```

### 9. 资金密码-设置

约束：资金密码不能和登录密码一致

#### uri: /web/apisecurity/setassettoken

#### method: post

参数说明：
- assettoken 交易密码
- reassettoken 重复交易密码
- mcode 手机验证码
- ga 谷歌验证码（如果开启了谷歌验证）


返回数据示例：

```
{
    "status":0,
    "msg":"设置资金密码成功"
}

// 如果开启了谷歌验证却没有提供ga参数，会返回状态码 7 

{
    "status":7,
    "msg":"谷歌验证码不能为空"
}

```


### 10. 资金密码-修改

约束：资金密码不能和登录密码一致

#### uri: /web/apisecurity/editassettoken

#### method: post

参数说明：
- oldassettoken 旧交易密码
- assettoken 新交易密码
- reassettoken 重新新交易密码
- mcode 手机号码
- ga 谷哥验证码，当开启了ga的时候会要求输入


返回数据示例：

```
{
    "status":0,
    "msg":"设置资金密码成功"
}

// 如果开启了谷歌验证却没有提供ga参数，会返回状态码 7 

{
    "status":7,
    "msg":"谷歌验证码不能为空"
}

```



### 11. 实名认证-第一步

约束：不可重复认证；需要绑定并验证手机; 相同证件(idtype + idnumber)不能重复认证；

#### uri: /web/apisecurity/authprimary

#### method: post

参数说明：
- idtype 认证类型 1 => 身份证， 2 => 护照
- idnumber 认证号码 
- country 国家代码，请参考 /web/index/country 接口
- realname 真实姓名
- code 手机验证码


返回数据示例：

```

{
    "status":0,
    "msg":"绑定邮箱成功"
}

// 如果用户尚未绑定手机，会返回状态码 6 

{
    "status":6,
    "msg":"请先绑定手机号"
}

```


### 12. 实名认证-第二步 上传证件照

约束：需要完成初级认证；不可重复认证；认证审核中时，不可再次申请；

#### uri: /web/apisecurity/authadvance

#### method: post

参数说明：
需要同时上传三张图片，顺序为： 身份证正面，身份证反面，手持身份证照片


返回数据示例：

```
{
    "status":0,
    "msg":"上传文件成功"
}

// 失败情形示例

{
    "status":6,
    "msg":"上传文件失败[m]"
}


```


### 13. 登录历史

#### uri: /web/apisecurity/loginlog

#### method: post

参数说明：
- p 页码


返回数据示例：

```

{
    "status":0,
    "msg":"success",
    "data":
    {
        "item":
        [
            {
                "id":"162",
                "uid":"10001",
                "logintime":"1561960565",
                "loginip":"122.233.232.233"
            },
            ...
        ],
        "current":1,
        "next":2,
        "before":1,
        "last":17,
        "totalPages":17,
        "totalItems":"162",
        "pageSize":10,
        "link":"/web/apisecurity/loginlog&p="
    }
}

```

- tiem 记录列表
- uid 用户uid
- logintime 登录时间
- loginip 登录ip
- current 当前页
- next 下一页
- before 前一页
- last 最后一页
- totalPages 总页数
- totalItems 总记录数
- pageSize 页面大小
- link 页面间跳转的链接


### 14. 获取认证与绑定信息

#### uri: /web/apisecurity/getuserinfo

#### method: post

参数说明：
- type 请求的信息内容，必须，取值如下：all(全部), email(邮箱), mobile(手机), ga(谷歌验证码), password(登录密码), assettoken(交易密码), level(实名认证等级), c2c(c2c相关配置)。api会根据传入参数选择返回的内容。


返回数据示例：

```
{
    "status":0,
    "msg":"success",
    "data":{
        "uid":"10004",
        "pid":"0",
        "icode":"zajb",
        "regtype":"1",
        "username":"130******534",
        "email":1,
        "emailname":"a***c@a***4.com",
        "mobile":1,
        "mobilename":"130******534",
        "ga":{
            "bind":0,
            "open":0
        },
        "password":1,
        "assettoken":1,
        "level":3,
        "verify":null,
        "usertype":null,
        "bound":null
    }
}

```

返回参数说明：
- uid 用户user id
- pid 用户的邀请人 user id
- icode 用户的邀请码
- regtype 注册类型，0 表示通过 email 注册，1 表示通过 mobile 注册
- username 用户名 regtype 为 0 时，即邮箱地址；为 1 时，即手机号
- email 是否设置了邮箱
- mobile 是否设置了手机
- ga 谷歌验证码设置，bind 表示是否设置了 ga，0 表示已设置，1 表示未设置；open 只有在 bind 为 1 的时候才有意义，表示是否开启验证
- password 是否设置了登录密码
- assettoken 是否设置了交易密码
- level 实名认证等级
- verify 实名认证状态，表示 level 当前等级下一级的认证进度，null 表示未提交认证，0 表示正在审核中，1 表示认证成功，2 表示认证被驳回
- usertype c2c用户身份，1 表示普通用户，2 表示商家。
- bound 用户已设置的收款方式。1 银行卡， 2 支付宝， 4 微信。 bound = 5 = 1 + 4 表示同时设置了银行卡和微信支付



### 15. 按注册方式发送验证码

#### uri: /web/apisecurity/sendcode

#### method: post

参数说明：
- type 发送类型，见apilogin中sendSmsCode与sendMailCode的说明，这里可以固定使用vcode


返回数据示例
```

{
    "status":0,
    "msg":"success",
    "data": "{regtype}"
}

```

返回数据说明：
- data 其值实际上是用户的注册类型，用于提示用户查收的验证码类型。0表示发送的是邮件验证码，1表示发送的是手机验证码。