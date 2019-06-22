### 1.用户注册(webApiloginRegister)
#### **请求url:**http://code.local.com/web/apilogin/register
#### **请求方式:**post
#### **参数：**
     mobile: "",
     password: "",
     repassword: "",
     code: "",
     vcode: ""

#### **返回参数：**
    "status": 1,
    "msg": "参数错误"

### 2.请求图片验证码
#### **请求url：**http://code.local.com/web/index/imgcode
#### **请求方式：**post

### 3.获取短信验证码(webApiloginSendsmscode)
#### **请求url:**http://code.local.com/web/apilogin/register
#### **请求方式:**post
#### **参数：**
     type: "register",
     mobile: this.ruleForm1.mobile

#### **返回参数：**
    "status": 1,
    "msg": "参数错误"