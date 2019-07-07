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
| 51  | 正在生成钱包地址，需要等待 |
| 100  | 用户未登录 |
| 999  | 系统异常 |
