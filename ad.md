### 1. 获取首页广告
#### uri：/web/apiad/index 

#### 请求方式：post

参数说明：
- cur: 1

返回示例：
```
{
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
}

```

### 2. 获取公告列表
#### 请求地址：/web/apiad/getOfficeList 

#### 请求方式：post

请求参数说明：
- cur: 页码, 默认 1
- pagesize: 页内数量，默认 10

返回示例：
```
{
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
}
```


### 3. 获取新闻列表
#### 请求地址：/web/apiad/getnewslist 

#### 请求方式：post

参数说明：
- cur: 1， 页码
- pagesize: 页内数量，默认10

返回示例：
```
{
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
}
``` 

### 4. 获取常见问题列表
#### 请求地址：/web/apiad/getproblemlist

#### 请求方式：post

参数说明：
- cur: 1

返回示例：
```
{
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
}
```
### 5. 获取用户协议

#### uri: /web/apiad/getAgree

#### **请求方式：**post

返回示例：（无）



### 6. 获取文章内容

#### uri: /web/apiad/view

#### **请求方式：**post

请求参数
- id 从前面的新闻、公告列表等里拿到的文章id

返回示例：

```
{
    "status":0,
    "msg":"success",
    "data":{
        "id":"1",
        "uid":"100",
        "category":"0",
        "lang":"",
        "title":"Proxychains4 的使用",
        "author":"某某某",
        "origin":"csdn",
        "abstract":"一小段摘要",
        "labels":"proxychains4",
        "weight":"0",
        "status":"1",
        "destroy":"0",
        "content":"一大段内容",
        "created":"0",
        "createip":"0.0.0.0",
        "updated":"0",
        "updateip":"0.0.0.0"
    }
}
```

返回说明：
- uid 创建者uid
- category 分类. 0 公告，1 新闻，2 常见问题，3 注册协议
- title 标题
- author 作者
- origin 来源
- abstract 摘要
- labels 标签
- weight 权重，可以用来排序
- content 带html标签的正文内容
- created 创建时间
