# MIPCache 域名升级

## MIPCache URL 是什么

先举个例子，MIP 官网的 URL 为：`https://www.mipengine.org`，对应的 MIPCache 的 URL 为   `https://mipcache.bdstatic.com/c/s/www.mipengine.org`。   
所谓 MIPCache URL 是经过 MIPCache CDN 缓存后的 MIP 页面地址，指向 MIPCache 的服务器。   
MIPCache URL 对应的内容则是通过 spider 抓取 MIP 页面的网页内容并进行缓存而来。   
MIPCache URL 通过 https 提供服务，增强内容的安全性的同时，亦可以在百度的搜索结果页中安全打开。       
## 升级背景 

升级之前，所有站点的 MIP 页面在搜索结果页中打开时的域名都是一样的，官网的 MIPCache URL 为例`https://mipcache.bdstatic.com`，这种 URL 存在如下弊端：   

- 站点域名隐藏比较深，在 URL 中后部
- 页面下的 Cookie 会有过大的风险
- 不方便以 Host 为粒度，区分相关特征

## 升级方案

`mipcache.bdstatic.com` 将被替换为 `{host_prefix}.mipcdn.com`
其中，`{host_prefix}` 遵循的替换规则如下：

1. 域名中的 `.` 被替换为 `-`  
2. 域名中的 `-` 被替换为 `--` 

还是以 MIP 官网的 URL 为例子：

> 原有 MIPCache 页面的 url：

```
https://mipcache.bdstatic.com/c/s/www.mipengine.org/
```

> 升级之后： 
     
```
https://www-mipengine-org.mipcdn.com/c/s/www.mipengine.org/
```

## 升级之后的好处 

MIPCache 域名进行升级后，主要有以下优点：
1. 升级后站点的域名在 MIPCache 中是有区分的，前置到 Host 里边，增加了站长自有品牌的露出。
2. Cookie 是分站点存放，不会相互影响。分站点存放也可以使 Cookie 大幅瘦身，减少请求的带宽。
3. 域名的不同，更加有利于做一些日志数据分析。
4. 有利于跨域资源共享 cors 方案的配置，更安全。

## 升级带来的问题

经过项目的仔细测试，目前发现的如下问题： 

     1：MIP 页面的服务端会针对页面上的资源（如图片）使用防盗链的策略，由于域名的切换，导致有部分资源403。需要针对域名升级方案中的新域名添加白名单。
     2：可能存在广告计费问题，需要针对新域名进行相应升级。注：MIP 官网上的广告均已升级支持

## 上线计划

7月20日，MIP 项目组将上线灰度实验，在确认没有问题的前提下，慢慢转成全量。


