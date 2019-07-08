### 1.用户登录(webApiloginLogin)
#### **请求url：**/web/apilogin/login
#### **请求方式：**post
#### **参数：**
    ga: 谷歌验证码, 如果绑定则需要
    password: 密码,
    captcha: 图片验证码,
    email: 邮箱，email和mobile只需要传一个参数
    mobile: 手机号，email和mobile只需要传一个，都传的时候email优先。
#### **返回参数：**

```
{
    msg: "登录成功"
    status: 0
    data: {
        token: "rk98pki16rbrmf1995hfveetkfkokjvv"
        uid: "10001"
        username: "130******531"
    }
}
```

### 2.获取认证与绑定信息(webApisecurityGetuserinfo)
#### **请求url：**/web/apisecurity/getuserinfo
#### **请求方式：**post
#### **参数：**
    type: "all" // 不能为空
#### **返回参数：**

```
{
    msg: "success"
    status: 0
    data: {
        assettoken: 1
        bound: "1"
        email: 1
        emailname: "a***c@a***1.com"
        ga: {bind: 0, open: 0}
        bind: 0
        open: 0
        level: 1
        mobile: 1
        mobilename: "130******531"
        password: 1
        regtype: "1"
        uid: "10001"
        username: "130******531"
        usertype: "0"
        verify: ""
    }
}
```

参数说明：
- ga 表示ga绑定状态，bind 0 表示未绑定，bind 1 表示已绑定； open 0 表示未开启，open 1 表示已开启
- bound 表示目前设置的收款方式，1 表示银行卡， 2 表示支付宝， 4 表示微信。 5 = 1 + 4 表示同时设置了银行卡和微信
- email与mobile、password、assettoken的1仅表示用户设置了邮箱和手机或密码，如果是0表示没有设置
- regtype 表示初始注册方式，0表示邮箱，1表示手机
- usertype 表示用户在c2c交易中的身份，如果1表示用户获得了商户身份
- verify 表示实名认证状态，如果为空表示没有处理中的实名认证；如果为1表示认证审核中，为2表示认证被驳回，与level结合使用


### 3. 找回密码

#### uri: /web/index/findpw`

#### 请求方法： post

#### 请求参数：
- email 邮箱地址，与ecode配合使用；
- ecode 邮箱验证码；
- mobile 手机号，与mcode配合使用；
- mcode 手机验证码；
- capcha 图片验证码，必须；
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


### 4. 手机/邮箱验证码直接登录

#### uri: /web/apilogin/codelogin

#### 请求方法： post

#### 请求参数
- email: 邮箱，email和mobile只需要传一个参数
- mobile: 手机号，email和mobile只需要传一个，都传的时候email优先。
- code: 手机/邮箱验证码
- ga: 当要求ga时，输入ga码

返回示例：

```
{
    msg: "登录成功"
    status: 0
    data: {
        token: "rk98pki16rbrmf1995hfveetkfkokjvv"
        uid: "10001"
        username: "130******531"
    }
}

```
