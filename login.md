### 1.用户注册

#### 请求uri: /web/apilogin/register

#### 请求方式: post

参数说明：
- mobile: 手机号,
- email: 邮箱,
- password: 密码,
- repassword: 重复密码,
- vcode: 手机/邮箱验证码，如果email和手机号同时存在，优先使用email。
- icode: 邀请码，非必须，用于确认邀请关系。


返回示例：

```
{
    "status":0,
    "msg":"success"
}

```


### 2. 手机/邮箱验证码直接登录

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


### 特别说明

如果用户携带token执行登录操作，则会直接验证token，如果token有效，则直接返回此token，返回格式与正常登录的结果一样，不会重新执行登录操作，传入的参数也不会验证。


### 3.用户登录

#### uri：/web/apilogin/login

#### post

参数说明：
- ga: 谷歌验证码, 如果绑定则需要
- password: 密码,
- captcha: 图片验证码,
- email: 邮箱，email和mobile只需要传一个参数
- mobile: 手机号，email和mobile只需要传一个，都传的时候email优先。

返回数据示例：

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

### 特别说明

如果用户携带token执行登录操作，则会直接验证token，如果token有效，则直接返回此token，返回格式与正常登录的结果一样，不会重新执行登录操作，传入的参数也不会验证。


### 4. 发送手机验证码

#### uri: /web/apilogin/sendsmscode

#### method: post

参数说明：
- type 类型，必须；根据场景取值：register:注册, bindphone:绑定手机号, bindmail:绑定邮箱, assettoken:设置交易密码, findpw:找回密码, resetpass:修改登录密码, ressetassettoken:修改交易密码, vcode:其它通用验证场景
- mobile 手机号，非必须；当非登录状态时，需要此参数；登录状态时，会自动获取用户的手机号；

返回数据示例：

```
{
    status: 0,
    msg: 'success'
}

```

### 5. 发送邮箱验证码

#### uri: /web/apilogin/sendmailcode

#### method: post

参数说明：
- type 类型，必须；根据场景取值：registercode:注册, registerlink:注册激活链接, withdraw:提币, resetpass:修改密码, ressetassettoken:修改交易密码, findpw:重置密码, bindmail:绑定邮箱, bindphone:绑定手机号, assettoken:设置交易密码, vcode:其它通用验证场景
- email 邮箱地址，非必须；当非登录状态时，需要此参数；登录状态时，会自动获取用户的邮箱；


返回数据示例：

```
{
    status: 0,
    msg: 'success'
}

```


### 6. 用户登出

#### uri: /web/apilogin/loginout

#### method: post

返回数据示例：

```
{
    status: 0,
    msg: '退出成功'
}

```
