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

### 2.请求图片验证码
#### **请求url：**http://code.local.com/web/index/imgcode
#### **请求方式：**post
#### **返回参数：**
    msg: "success"
    status: 0
    data: {uid: "10001", regtype: "1", username: "130******531", email: 1, emailname: "a***c@a***1.com",…}
    assettoken: 1
    bound: "1"
    email: 1
    emailname: "a***c@a***1.com"
    ga: {bind: 0, open: 0}
    level: 1
    mobile: 1
    mobilename: "130******531"
    password: 1
    regtype: "1"
    uid: "10001"
    username: "130******531"
    usertype: "0"
    verify: ""

### 3.获取短信验证码(webApiloginSendsmscode)
#### **请求url:**http://code.local.com/web/apilogin/register
#### **请求方式:**post
#### **参数：**
     type: "register",
     mobile: this.ruleForm1.mobile

#### **返回参数：**
    