# 16_百度推出MIP Path链接

在做MIP化改造时，站长需要关注的一共有三个URL：MIP URL, MIP-Cache URL 及 MIP-Path。

## MIP URL
MIP URL是MIP页的地址，指向在站长的服务器的MIP页。站长将MIP URL通过站长平台提交给百度，用于搜索引擎抓取和建库。

## MIP-Cache URL 是什么
MIP-Cache url是经过CDN缓存的MIP页面地址，指向MIP-Cache服务器。MIP-Cache url是https的，可以直接访问，页是百度搜索结果页异步打开的页面。

## MIP-Path 诞生记
MIP页在百度结果页是异步打开的，为了页面链接的传播，我们将MIP-cache拼接在搜索结果页链接中，这就是MIP-Path的前身。

但搜索链接 + MIP-Cache这种直接拼链接的方式包含过多冗余信息，不利于品牌露出和直接复制分享。为了解决这个问题，MIP项目组创建了新的Path规则，生效于所有从百度搜索结果打开的MIP页，MIP Path由此诞生。

新的path规则为restful风格，能够很好的协调诠释了前台请求与后台动作应有的关系模型，简化url的同时也增加了品牌露出。

```
修改前：
https://www.baidu.com/sf?word=mipengine&mod=0&tn=normal&pd=mms_mip&actname=act_sf_mip&title=www.mipengine.org&top=%7B%22sfhs%22%3A4%7D&ext=%7B%22url%22%3A%22%252F%252Fmipcache.bdstatic.com%252Fc%252Fwww.mipengine.org%252F%22%2C%22lid%22%3A%222179864842002628151%22%7D&lid=2179864842002628151&ms=1&frsrcid=1599&frorder=1

修改后：
https://m.baidu.com/mip/c/www.mipengine.org/index.html
```

## MIP-Path转换工具
转换工具提供了MIP URL, MIP-Cache URL 及 MIP-Path的相互转换，可以到https://www.mipengine.org/mippath.html 使用。

