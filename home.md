### 1. 获取首页广告（webApiGetAds）
#### **请求地址：**/web/apiad/index 

#### **请求方式：**post

#### **请求参数：**
    cur: 1

#### **返回参数：**
    "status": 0,
    "msg": "success",
    "data": [
        {
            "id": "4",
            "uid": "100",
            "title": "注册送币活动开始啦！！！！",
            "url": "http://www.xxxxx.com",
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
            "url": "http://www.xxxxxx.com",
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
            "url": "http://www.xxxxx.com",
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
#### **请求地址：**/web/apiad/getnewslist 

#### **请求方式：**post

#### **请求参数：**
    cur: 1

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
                "title": "aaaaaaaaa",
                "author": "小王",
                "origin": "csdn",
                "abstract": "xxxxxxxxxxxxxx",
                "labels": "proxychains4",
                "weight": "0",
                "status": "1",
                "destroy": "0",
                "content": "xxxxxxxxxxxxxxxxxx",
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
#### **请求地址：**/web/apiad/getnewslist 

#### **请求方式：**post

#### **请求参数：**
    cur: 1

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
                "title": "aaaaaa",
                "author": "小王",
                "origin": "csdn",
                "abstract": "xxxxxxxxxxxxxx",
                "labels": "proxychains4",
                "weight": "0",
                "status": "1",
                "destroy": "0",
                "content": "xxxxxxxxxxxxxxx",
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
    


### 4. 获取常见问题列表（webApiGetProblemList）
#### **请求地址：**/web/apiad/getproblemlist

#### **请求方式：**post

#### **请求参数：**
    cur: 1

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
                "title": "aaaaaaa",
                "author": "小王",
                "origin": "csdn",
                "abstract": "xxxxxxxxxxxxxx",
                "labels": "proxychains4",
                "weight": "0",
                "status": "1",
                "destroy": "0",
                "content": "xxxxxxxxxxxxxxx",
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

### 5. 获取用户协议

#### uri: /web/apiad/getuseragree

#### **请求方式：**post

返回示例：（无）