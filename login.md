### 1.用户登录(webApiloginLogin)
#### **请求url：**/web/apilogin/login
#### **请求方式：**post
#### **参数：**
    ga: 谷歌验证码,
    password: 密码,
    captcha: 图片验证码,
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
    type: "all" // 默认
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

