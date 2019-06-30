### 1.用户登录(webApiloginLogin)
#### **请求url：**/web/apilogin/login
#### **请求方式：**post
#### **参数：**
    ga: this.gacode,
    password: this[formName].password,
    captcha: this[formName].captcha,
#### **返回参数：**
    msg: "登录成功"
    status: 0
    data: {uid: "10001", username: "130******531", token: "rk98pki16rbrmf1995hfveetkfkokjvv"}
    token: "rk98pki16rbrmf1995hfveetkfkokjvv"
    uid: "10001"
    username: "130******531"

### 2.获取认证与绑定信息(webApisecurityGetuserinfo)
#### **请求url：**/web/apisecurity/getuserinfo
#### **请求方式：**post
#### **参数：**
    type: "all",
    isThis: this
#### **返回参数：**
    msg: "success"
    status: 0
    data: {uid: "10001", regtype: "1", username: "130******531", email: 1, emailname: "a***c@a***1.com",…}
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
   
### 3.请求图片验证码
#### **请求url：**/web/index/imgcode
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
