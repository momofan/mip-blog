# 存储
为提供站点数据存储的功能，并且保证安全性和完整方案，开发一套存储方案来进行统一管理，包括站长管理存储，local storage方式。

### 方案解读
通过初始化决定采用哪种方式，如new customStorage(0)，0为local storage，1为站长管理存储；
- Local Storage存储方案
    - 对于不敏感信息，通过local storage的方式存储在当前域名下，由站长选择；
    - 如果是cache域名，通过mip策略进行管理，如果是站长域名下，通过local storage原始方法进行存储管理；
    - 该方案不保证信息的安全性，所以应该适当选取；
    - 每个站点对应local storage里面的一个key，如果在cache域名下，key为站长站点域名；
    - cache域名下，每个站点信息以json方式存储；
    - cache域名下，每个站点存储信息大小不超过4k；
    - cache域名下，总存储空间为5M，根据浏览器不同而不同；

- 服务端存储方案
    - 较local storage更安全，但是会有延迟，同时不建议设置用户信息等隐私数据；
    - 存储设置/获取完成后通过callback进行回调；
    - MIP只负责发起请求并将数据传给站长，需要站长自己维护存储操作功能（如种cookie或者存储数据库）；

### 使用方式
```
var util = require('util');
var customStorage = new util.customStorage([param]);
```

### API

#### 1. local storage方式API

#### new util.customStorage(type)
- customStorage类，用于初始化存储对象
- 参数列表
```
参数       类型       描述
type      number   type为存储类型，0表示local storage存储，1表示站长管理存储
```
- 示例
```
var customStorage = new util.customStorage(0);
```

#### customStorage.set(name, value, [expire], [callback])
- 设置当前站点下的存储；
- 参数列表
```
参数       类型       描述
name      string   存储名称
value     string   存储值
expire    number   存储的过期时间，指的是当前站点整个存储的过期时间，单位为s
callback  Function 存储出现问题时的回调，分为两种情况，一种是当前站点存储超限（4k），一种是超过local storage最大存储值（一般浏览器为5M），这个错误是针对所有站点的存储空间的
```
- 示例
```
btn.onclick = function() {
    customStorage.set('a', '这是a');
    customStorage.set('b', '这是b');
}
```

#### callback返回的error对象结构
```
参数       类型       描述
errCode   string   错误号，21为当前站点超限，22位整个local storage存储空间不足
errMess   string   错误信息
```
#### customStorage.get(name)
- 获取当前站点下的存储；
- 参数列表
```
参数       类型       描述
name      string   存储名称
```
- 示例
```
var a = customStorage.get('a');
```

#### customStorage.rm(name)
- 删除当前站点下的存储；
- 参数列表
```
参数       类型       描述
name      string   存储名称
```
- 示例
```
customStorage.rm('b');
```

#### customStorage.rmExpires()
- 删除整个local storage存储中过期的站点存储数据；
- 示例
```
customStorage.rmExpires();
```

#### customStorage.clear()
- 清空当前站点下数据存储；
- 示例
```
customStorage.clear();
```

#### 2. 站长管理存储
#### customStorage.request(opt)
- 发起站长请求的函数，将数据通过请求传给站长，由其对数据进行设置或获取；
- 请求通过fetch的方式发出，具体可参考[使用fetch](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch)和[GlobalFetch.fetch()](https://developer.mozilla.org/zh-CN/docs/Web/API/GlobalFetch/fetch)两篇文章；
- 参数列表
```
参数         类型       描述
url         string   必选，发送请求的地址
method      string   可选，默认为get，请求方法 (GET, POST, or other)
mode        string   可选，请求的模式，如 cors, no-cors,  same-origin
headers     Object   可选， 请求的头信息，形式为 Headers 对象或 yteString
body        Object/string   可选，请求的 body 信息,可能是一个 Blob、BufferSource、FormData、URLSearchParams 或者 USVString 对象，注意 GET 或 HEAD 方法的请求不能包含 body 信息
credentials string   可选，请求的 credentials，如omit、same-origin 或者 include
cache       string   可选，请求的 cache 模式: default, no-store, reload, no-cache, force-cache, or only-if-cached
```
- 示例
```
storage1.request({
    url: 'http://example.com/',
    type: 'POST',
    data: JSON.stringify({
      aa: 1,
      bb: 2
    }),
    success: function() {
      console.log('success');
    },
    error: function(e) {
      console.log(e);
    }
});
```

#### 站长管理存储后端需要如何做校验来保证安全性？

请求采用cors(跨域资源共享)的方式，需要站长后端进行配置和安全校验才能使用；同时由于目前百度CDN需要更换域名，所以需要站长配置时暂时兼容两个域名，分别为`mipcache.bdstatic.com`和`c.mipcdn.com`（即下面说到的cache域名），具体配置方式如下步骤：

- http请求头referer校验：解析出referer中所有域名
  - 如果第一个域名是站长的域名，可以访问；如果是百度的cache域名，进入下一步，否则禁止；
  - 如果第二个域名是站长的域名，可以访问，否则禁止；
- response header定义
  - `Access-Control-Allow-origin: origin`，这个设置为允许跨站访问的域名，可以为百度cache域名和站长域名，不建议设置为`*`；
  - `Access-Control-Allow-Methods: 'GET, POST'`，具体运行哪种类型由站长自行定义；

通过以上步骤可以完成校验流程，但是该方案不建议操作隐私信息，如用户信息！