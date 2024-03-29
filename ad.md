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
            "article_id": 0,
            "img": "3",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0",
            "article": {
                  //
            }
        },
        {
            "id": "3",
            "uid": "100",
            "title": "注册送币活动开始啦！！！",
            "url": "http://www.xxxxxx.com",
            "article_id": 0,
            "img": "2",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0",
            "article": {
                  //
            }
        },
        {
            "id": "2",
            "uid": "100",
            "title": "注册送币活动开始啦！！",
            "url": "http://www.xxxxx.com",
            "article_id": 0,
            "img": "1",
            "lang": "",
            "weight": "0",
            "created": "0",
            "createip": "0.0.0.0",
            "updated": "0",
            "updateip": "0.0.0.0",
            "status": "1",
            "destroy": "0",
            "article": {
                  //
            }
        }
    ]
}

```

返回说明：
- article_id 如果这个字段不为0，表示文章是内部文章，前端自行决定如果跳转及展示（调用/web/apiad/view接口获取内容）；
- url 如果article_id为0，表示是外部文章，直接通过webview方式打开即可。
- article 如果使用article_id不方便，可以直接使用article内容，当article_id不为0的时候，article内容为对应的文章的内容。其结构参考下方 **/web/apiad/getOfficeList** 里的item.

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
