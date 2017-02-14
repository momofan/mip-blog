# 16\_百度推出 MIP Shell 链接

在站长将站点 MIP 化时，需要关注 URL 的一共有三个：MIP URL, MIP-Cache URL 以及 MIP-Shell URL。

## 从 URL 说起

在互联网中，URL 定义页面的地址，每个 URL 对应一个页面。而 MIP URL 则是 MIP 页的原始地址，指向托管在站长服务器上的 MIP 页。

MIP URL 是一个 MIP 页面的源头，其域名、服务器、内容都由站长自行管理。它是一张符合 MIP 标准的网页，被托管在互联网的各个角落。站长将 MIP URL 通过站长平台提交给百度，用于百度搜索引擎抓取，将 MIP 页面索引起来。

## MIP-Cache URL 是什么

由于 MIP 项目对 MIP 页面提供了缓存，但 MIP URL 并不指向缓存服务，故 MIP 项目组为每个 MIP 页面提供了 MIP-Cache URL。

MIP-Cache URL 是经过 CDN 缓存的 MIP 页面地址，指向 MIP Cache 服务器；而其内容则是由 MIP URL 抓取并缓存而来。其通过 https 协议提供的，增强站点的安全性的同时，亦可以在百度的搜索结果页中安全打开。

## 为什么要有 MIP-Shell

为了使通过百度的搜索结果打开的 MIP 页面加载更加快速、体验更优秀，这些页面将使用 MIP-Shell 打开。在过去，我们在搜索链接后拼接了 MIP-Cache URL 用来标记 MIP 页面。但通过搜索链接 + MIP-Cache 生成的 URL 过于冗长，其中包含大量冗余信息，不利于品牌露出和直接复制分享。为了解决这个问题，MIP 项目组创建了新的 URL 规则，生效于所有从百度搜索结果打开的 MIP 页，MIP-Shell URL 由此诞生。

新的 URL 规则为 RESTful 风格，链接简短清晰、方便传播，在简化 URL 的同时也增加了站长自有品牌的露出。一个电信的例子如下：

> 过去：
> https://www.baidu.com/sf?word=mipengine&mod=0&tn=normal&pd=mms_mip&actname=act_sf_mip&title=www.mipengine.org&top=%7B%22sfhs%22%3A4%7D&ext=%7B%22url%22%3A%22%252F%252Fmipcache.bdstatic.com%252Fc%252Fwww.mipengine.org%252F%22%2C%22lid%22%3A%222179864842002628151%22%7D&lid=2179864842002628151&ms=1&frsrcid=1599&frorder=1
>
> **现在**：
> https://m.baidu.com/mip/c/www.mipengine.org/index.html

## MIP URL 转换工具

为了方便站长的使用，我们提供了 MIP URL 转换工具。该工具中提供了MIP URL, MIP-Cache URL 及 MIP-Shell URL 的相互转换，可以到 https://www.mipengine.org/mippath.html 使用。
