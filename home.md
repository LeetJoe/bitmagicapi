### 1. 获取首页广告（webApiGetAds）
#### **请求地址：**http://code.local.com/web/apiad/index 

#### **请求方式：**post

#### **返回参数：**
    "status": 0,
    "msg": "success",
    "data": [
        {
            "id": "4",
            "uid": "100",
            "title": "注册送币活动开始啦！！！！",
            "url": "http://www.baidu.com",
            "img": "3",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0"
        },
        {
            "id": "3",
            "uid": "100",
            "title": "注册送币活动开始啦！！！",
            "url": "http://www.baidu.com",
            "img": "2",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0"
        },
        {
            "id": "2",
            "uid": "100",
            "title": "注册送币活动开始啦！！",
            "url": "http://www.baidu.com",
            "img": "1",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0"
        }
    ]

### 2. 获取新闻列表（webApiGetNews）
#### **请求地址：**http://code.local.com/web/apiad/getnewslist 

#### **请求方式：**post

#### **返回参数：**
    "status": 0,
    "msg": "success",
    "data": {
        "item": [
            {
                "id": "2",
                "uid": "100",
                "category": "1",
                "lang": "",
                "title": "Proxychains4 使用记录",
                "author": "小王",
                "origin": "csdn",
                "abstract": "ProxyChains4 是linux平台的一个代理切换软件。最近在ubuntu 上使用ss 进行上网，每次代理的切换都是非常麻烦。\n\nProxyChains4 能很好的解决socks代理的系统设置问题。",
                "labels": "proxychains4",
                "weight": "0",
                "status": "1",
                "destroy": "0",
                "content": "三 配置\nsudo vi /etc/proxychains.conf\n\n[ProxyList]\n# add proxy here ...\n# meanwile\n# defaults set to \"tor\"\nsocks5 \t127.0.0.1 1080\n四 用法\nproxychains4 firefox\nproxychains4 ping www.google.com\nproxychains4 telnet somehot.com\n\n\n这样 我们打开ss连接服务器后 然后proxychains4 命令打开g..gle 等 都是没问题的.\n\n\n吐槽，中国的网络环境太差\r\n--------------------- \r\n作者：mingjie1212 \r\n来源：CSDN \r\n原文：https://blog.csdn.net/mingjie1212/article/details/51814421 \r\n版权声明：本文为博主原创文章，转载请附上博文链接！",
                "created": "0",
                "createip": "0.0.0.0",
                "updated": "0",
                "updateip": "0.0.0.0"
            }
        ],
        "current": 1,
        "next": 1,
        "before": 1,
        "last": 1,
        "totalPages": 1,
        "totalItems": "1",
        "pageSize": 10,
        "link": "/web/apiad/getnewslist&p="
    }


### 3. 获取公告列表（webApiGetNotice）
#### **请求地址：**http://code.local.com/web/apiad/getnewslist 

#### **请求方式：**post

#### **返回参数：**
    "status": 0,
    "msg": "success",
    "data": {
        "item": [
            {
                "id": "1",
                "uid": "100",
                "category": "0",
                "lang": "",
                "title": "Proxychains4 使用记录",
                "author": "小王",
                "origin": "csdn",
                "abstract": "ProxyChains4 是linux平台的一个代理切换软件。最近在ubuntu 上使用ss 进行上网，每次代理的切换都是非常麻烦。\n\nProxyChains4 能很好的解决socks代理的系统设置问题。",
                "labels": "proxychains4",
                "weight": "0",
                "status": "1",
                "destroy": "0",
                "content": "三 配置\nsudo vi /etc/proxychains.conf\n\n[ProxyList]\n# add proxy here ...\n# meanwile\n# defaults set to \"tor\"\nsocks5 \t127.0.0.1 1080\n四 用法\nproxychains4 firefox\nproxychains4 ping www.google.com\nproxychains4 telnet somehot.com\n\n\n这样 我们打开ss连接服务器后 然后proxychains4 命令打开g..gle 等 都是没问题的.\n\n\n吐槽，中国的网络环境太差\r\n--------------------- \r\n作者：mingjie1212 \r\n来源：CSDN \r\n原文：https://blog.csdn.net/mingjie1212/article/details/51814421 \r\n版权声明：本文为博主原创文章，转载请附上博文链接！",
                "created": "0",
                "createip": "0.0.0.0",
                "updated": "0",
                "updateip": "0.0.0.0"
            }
        ],
        "current": 1,
        "next": 1,
        "before": 1,
        "last": 1,
        "totalPages": 1,
        "totalItems": "1",
        "pageSize": 10,
        "link": "/web/apiad/getofficelist&p="
    }