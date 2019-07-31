### api说明文档

可用的api请求地址：testapi.bitmagic.pro

统一返回格式说明：

```

{
    status: 0, // 状态码，0表示成功，1表示一般失败。其它非1的大于0的值表示一些特殊的失败场景。
    msg: '', // 成功时通常返回 success。失败时返回失败说明。
    data: {} // 通常成功时才会有，携带返回数据（如果有）。
}

```

status已定义值说明

|  status   | 含义  |
|  ----:  | :----  |
| 0  | 一般成功 |
| 1  | 一般错误 |
| 3  | 需要输入交易密码 |
| 4  | 需要先设置交易密码 |
| 5  | 未绑定手机号码 |
| 6  | 需要绑定手机号码 |
| 7  | 需要验证谷歌验证码 |
| 8  | 需要设置收款方式 |
| 9  | 需要开启收款方式 |
| 11  | 需要先完成一级实名认证 |
| 12  | 需要先完成二级实名认证 |
| 13  | 需要先完成三级实名认证 |
| 14  | 需要验证图片验证码 |
| 51  | 正在生成钱包地址，需要等待 |
| 100  | 用户未登录 |
| 999  | 系统异常 |

对需要验证身份的api，需要在header里增加token: {TOKEN}

{TOKEN}是在登录成功时返回的口令。


### 接口一览：
#### account
- /web/apiaccount/list, 用户资产-获取。用于用户的资产页面，展示用户所有资产信息。
- /web/apiaccount/bindBankInfo, 绑定银行卡信息。提交以绑定银行卡信息。
- /web/apiaccount/bindAlipayInfo, 绑定支付宝信息。提交以绑定支付宝信息。
- /web/apiaccount/bindWechatInfo, 绑定微信支付信息。提交以绑定微信支付信息。
- /web/apiaccount/getC2cBindInfo, 获取c2c用户绑定支付信息。获取当前绑定的所有支付信息（银行卡，支付宝，微信）。
- /web/apiaccount/toc2c, 币币账户向法币账户转币。提交从币币账户向法币账户（OTC）转移资产的申请。
- /web/apiaccount/fromc2c, 法币账户向币币账户转币。提交从法币账户（OTC）转移资产的申请。
- /web/apiaccount/frommine, 挖矿账户向币币账户转币。提交从挖矿账户向币币账户转币的申请。
- /web/apiaccount/fromc2clist, 法币账户向币币账户转币历史记录。
- /web/apiaccount/toc2clist, 币币账户向法币账户转币历史记录
- /web/apiaccount/fromminelist, 挖矿账户向法币账户转币历史记录
- /web/apiaccount/getProfitList, 挖矿收益记录


#### ad
- /web/apiad/index, 获取首页广告
- /web/apiad/getOfficeList, 获取公告列表
- /web/apiad/getnewslist, 获取新闻列表
- /web/apiad/getproblemlist, 获取常见问题列表
- /web/apiad/getAgre, 获取用户协议
- /web/apiad/view, 获取文章内容


#### c2cmarket
- /web/apic2cmarket/entrust, 挂单
- /web/apic2cmarket/cancel, 撤单
- /web/apic2cmarket/confirm, 成交确认。确认支付与确认收款都是这个方法
- /web/apic2cmarket/dealcancel, 成交撤消。只有买方用户可以撤单。
- /web/apic2cmarket/trustlist, 我的委托列表
- /web/apic2cmarket/newdeal, 我的待处理成交
- /web/apic2cmarket/deallist, 我的历史成交列表


#### index
- /web/index/imgcode, 图片验证码
- /web/index/coins, 币种列表
- /web/index/boards, 交易区列表
- /web/index/coinconf/board/{board}/coin/{coin}, 交易对配置信息
- /web/index/ticker/{market}, 实时牌价
- /web/index/c2cticker, c2c实时牌价
- /web/index/banklist, 银行列表
- /web/index/findpw, 找回密码
- /web/index/c2centrustlist, 交易市场
- /web/index/country, 国家列表
- /web/index/outlimit, 获取提币限额
- /web/index/coininfo, 获取币种配置/信息
- /web/index/cnyrate, 获取各币种人民币汇率

#### login
- /web/apilogin/register, 用户注册
- /web/apilogin/codelogin, 手机/邮箱验证码直接登录
- /web/apilogin/login, 用户登录
- /web/apilogin/sendsmscode, 发送手机验证码
- /web/apilogin/sendmailcode, 发送邮箱验证码
- /web/apilogin/loginout, 用户登出


#### market
- /web/apimarket/entrust, 交易挂单
- /web/apimarket/cancel, 撤单
- /web/apimarket/trustlist, 委托列表
- /web/apimarket/deallist, 我的成交列表


#### mdata
- /mdata/trust/{market}/{coin}, 获取全局挂单列表
- /mdata/deal/{market}/{coin}, 获取全局成交列表
- /mdata/kline/{market}\_{coin}\_{resolution}, 获取k线数据

#### security
- /web/apisecurity/bindmobile, 手机号-绑定
- /web/apisecurity/resetmobile, 手机号-修改
- /web/apisecurity/bindemail, 邮箱-绑定
- /web/apisecurity/bindga, 谷歌验证码-绑定
- /web/apisecurity/closega, 谷歌验证码-关闭
- /web/apisecurity/openga, 谷歌验证码-开启
- /web/apisecurity/editga, 谷歌验证码-修改
- /web/apisecurity/createga, 生成谷歌验证密钥
- /web/apisecurity/editpw, 登录密码-修改
- /web/apisecurity/setassettoken, 资金密码-设置
- /web/apisecurity/editassettoken, 资金密码-修改
- /web/apisecurity/authprimary, 实名认证-第一步
- /web/apisecurity/authadvance, 实名认证-第二步 上传证件照
- /web/apisecurity/loginlog, 登录历史
- /web/apisecurity/getuserinfo, 获取认证与绑定信息
- /web/apisecurity/sendcode, 根据用户注册方式发送验证码。如果是手机注册，发送手机验证码；如果是邮箱注册，发送邮箱验证码。


#### wallet
- /web/apiwallet/getaddr, 获取充值地址
- /web/apiwallet/addaddress, 添加转出币地址
- /web/apiwallet/deladdress, 删除转出币地址
- /web/apiwallet/addrlist, 获取转出地址列表
- /web/apiwallet/transout, 提币申请
- /web/apiwallet/cancel, 撤消提币申请
- /web/apiwallet/history, 转币历史记录，入账出账共用此api
- 
