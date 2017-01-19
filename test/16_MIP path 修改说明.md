# 16_MIP path 修改说明

## PATH 修改背景
MIP页在百度搜索结果页打开时URL较长，不利于品牌露出和直接复制分享。为了解决这个问题，MIP项目组创建了新的Path规则，生效于所有从百度搜索结果打开的MIP页。

新的path规则为restful风格，能够很好的协调诠释了前台请求与后台动作应有的关系模型，简化url的同时也增加了品牌露出。可以到https://www.mipengine.org/mippath.html 输入URL查看结果。

修改前：
https://www.baidu.com/sf?word=mipengine&mod=0&tn=normal&pd=mms_mip&actname=act_sf_mip&title=www.mipengine.org&top=%7B%22sfhs%22%3A4%7D&ext=%7B%22url%22%3A%22%252F%252Fmipcache.bdstatic.com%252Fc%252Fwww.mipengine.org%252F%22%2C%22lid%22%3A%222179864842002628151%22%7D&lid=2179864842002628151&ms=1&frsrcid=1599&frorder=1

修改后：
https://m.baidu.com/mip/c/www.mipengine.org/index.html

## 规则 & 示例

### 情况一：http链接

规则：直接将MIP页url拼在`https://m.baidu.com/mip/c/`后。

- MIP页： http://www.mipengine.org/a.html
- Cache页： https://mipcache.bdstatic.com/c/www.mipengine.org/a.html
- 结果页： https://m.baidu.com/mip/c/www.mipengine.org/a.html

### 情况二：https链接

规则：直接将MIP页url拼在`https://m.baidu.com/mip/c/s/`后。与http链接相比，多一个`s/`。

- MIP页： https://www.mipengine.org/a.html
- Cache页： https://mipcache.bdstatic.com/c/s/www.mipengine.org/a.html
- 结果页： https://m.baidu.com/mip/c/s/www.mipengine.org/a.html


### 情况三：url中含有query string

规则： 将MIP页url进行encodeUrlComponent, 再将所有单斜线'/'对应的%2F还原。拼在`https://m.baidu.com/mip/c/(s/)` 之后，MIP页协议为https，结果页链接就带有`/s`。

- MIP页：http://www.mipengine.org/a.html?from=https://m.a.com/b.html
- Cache页： https://mipcache.bdstatic.com/c/www.mipengine.org/a.html?from=https://m.a.com/b.html
- 结果页： https://m.baidu.com/mip/c/www.mipengine.org/a.html%3Ffrom%3Dhttps%3A%2F%2Fm.a.com/b.html
