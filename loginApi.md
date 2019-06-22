### 1.用户登录(webApiloginLogin)
#### **请求url：**http://code.local.com/web/apilogin/login
#### **请求方式：**post
#### **参数：**
    ga: this.gacode,
    password: this[formName].password,
    captcha: this[formName].captcha,
#### **返回参数：**
    "status": 1,
    "msg": "用户名或密码错误"

### 2.获取认证与绑定信息(webApisecurityGetuserinfo)
#### **请求url：**http://code.local.com/web/apisecurity/getuserinfo
#### **请求方式：**post
#### **参数：**
    type: "all",
    isThis: this
#### **返回参数：**
    "status": 100,
    "msg": "您还没有登录"


### 3.请求图片验证码
#### **请求url：**http://code.local.com/web/index/imgcode
#### **请求方式：**post