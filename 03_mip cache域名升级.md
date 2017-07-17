# MIP cache 域名升级

## MIP cache URL 是什么

由于 MIP 项目对 MIP 页面提供了缓存，但 MIP URL 并不指向缓存服务，故 MIP 项目组为每个 MIP 页面提供了 MIP-Cache URL。    
MIP-Cache URL 是经过 CDN 缓存的 MIP 页面地址，指向 MIP Cache 服务器；而其内容则是通过抓取 MIP URL 网页内容并进行缓存而来。MIP-Cache URL 通过 https 协议提供的，增强站点的安全性的同时，亦可以在百度的搜索结果页中安全打开。     

## 升级背景 

目前所有所有站点的 MIP 页面在搜索结果页中打开时的域名都是一样的，这样存在以下两个问题：
- 不利于做页面 url 分析、站点域名隐藏比较深
- 页面的 cookie 会有过大的风险

MIP cache 域名进行升级后，针对以上问题进行改进，将`mipcache.bdstatic.com`替换为`xxx.mipcdn.com`,会将 mip 站点域名处理后与 mipcache 域名进行拼接，形成新的域名（泛域名），将域名中包含 "." 的，替换为 " - "，将域名中包含 " - " 的，替换为 " -- ",
具体实例：

> 原有cache页：       

```
https://mipcache.bdstatic.com/c/s/www.mipengine.org/

```

> 升级之后： 
     
```
http://www-mipengine-org.mipcdn.com/c/s/www.mipengine.org/

```

## 升级之后的好处  

MIP cache 域名进行升级后，主要有以下优点：
1. 升级后站点的域名在 mip cache 中是有区分的，前置到 url 最前面，大大增加了站长自有品牌的露出。
2. cookie 是分站点存放，不会相互影响；分开存放下，cookie 成功瘦身，能够减少请求的带宽。
3. 域名的不同，更加有利于做一些日志数据分析等。
4. 有利于跨域资源共享 cors 方案的配置，更安全。

