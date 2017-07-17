# MIP cache 域名升级

## MIP cache URL 是什么

MIP cache 对符合 MIP 标准的页面提供缓存服务，但 MIP 页面的 URL 并不是指向缓存服务的地址，所以 MIP cache 中的每个 MIP 页面都有一个对应的 MIP cache URL。    
MIP cache URL 是经过 CDN 缓存的 MIP 页面地址，指向 MIP Cache 的服务器；而其内容则是通过 spider 抓取 MIP 页面的网页内容并进行缓存而来。MIP cache URL 通过 https 协议提供的，增强站点的安全性的同时，亦可以在百度的搜索结果页中安全打开。     

## 升级背景 

升级之前，所有站点的 MIP 页面在搜索结果页中打开时的域名都是一样的，即目前的`https://mipcache.bdstatic.com`，这种情况存在如下两个问题：
- 不利于做页面 url 级别的区分和分析，且站点域名隐藏比较深，在 url 最后面
- 页面下的 cookie 会有过大的风险

## 升级方案

正式由于上述存在的问题，针对 MIP cache 域名进行升级，将`mipcache.bdstatic.com`替换为`xxx.mipcdn.com`,其中将 MIP 站点域名处理后与 MIP cache 域名进行拼接，形成新的域名（泛域名），将域名中的 "." 替换为 "-"，将域名中的 "-"替换为 "--",
以下给出一个具体实例：

> 原有 MIP cache 页面的 url：

```
https://mipcache.bdstatic.com/c/s/www.mipengine.org/

```

> 升级之后： 
     
```
https://www-mipengine-org.mipcdn.com/c/s/www.mipengine.org/

```

## 升级之后的好处  

MIP cache 域名进行升级后，主要有以下优点：
1. 升级后站点的域名在 mip cache 中是有区分的，前置到 url 最前面，大大增加了站长自有品牌的露出。
2. cookie 是分站点存放，不会相互影响；分开存放下，cookie 成功瘦身，能够减少请求的带宽。
3. 域名的不同，更加有利于做一些日志数据分析等。
4. 有利于跨域资源共享 cors 方案的配置，更安全。

## 升级带来的问题

经过项目的仔细测试，目前发现的主要问题是： MIP 页面的服务端会对页面上的资源使用防盗链的策略，由于域名的切换，导致有部分资源403，需要针对域名升级方案添加白名单

## 上线计划

7月20日，MIP 项目组将上线灰度实验，在确认没有问题的前提下，慢慢转成全量。


