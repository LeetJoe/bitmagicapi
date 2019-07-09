### 1.用户注册(webApiloginRegister)

#### **请求url:**/web/apilogin/register

#### **请求方式:**post

#### **参数：**
- mobile: 手机号,
- email: 邮箱,
- password: 密码,
- repassword: 重复密码,
- vcode: 手机/邮箱验证码，如果email和手机号同时存在，优先使用email。

#### **返回参数：**

```
{
    "status":0,
    "msg":"success",
    "data": {newid}
}

```
