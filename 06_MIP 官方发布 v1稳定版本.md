近期，MIP官方发布了MIP系列文件的全新v1版本，我们建议大家尽快完成升级。

## 一、 我是开发者，如何升级版本？
对于MIP页面开发者来说，**只需替换线上引用的MIP文件为v1版本**，就可以完成升级。所有组件都已经升级到v1版本，可根据通配规则推断出引用地址。下表为常用文件的v1版本地址：

|文件|v1版本地址|
|--|--|
|mip.js (原mipmain.js)|https://mipcache.bdstatic.com/static/v1/mip.js|
|mip.css (原mipmain.css)|https://mipcache.bdstatic.com/static/v1/mip.css|
|百度统计 mip-stats-baidu|https://mipcache.bdstatic.com/static/v1/mip-stats-baidu/mip-stats-baidu.js|
|广告组件 mip-ad|https://mipcache.bdstatic.com/static/v1/mip-ad/mip-ad.js|
|分享组件 mip-share|https://mipcache.bdstatic.com/static/v1/mip-share/mip-share.js|
|应用下载 mip-appdl|https://mipcache.bdstatic.com/static/v1/mip-appdl/mip-appdl.js|
|(通配规则)mip-abc|https://mipcache.bdstatic.com/static/v1/mip-abc/mip-abc.js|
## 二、升级的好处
**减少未来的开发和维护成本：**v1版本的代码内容由服务端统一控制。未来的功能升级，bugfix等代码改动会直接生效到v1文件中，站长无需再次修改版本。

## 三、继续使用当前mipmain版本会有问题吗？
**当前线上的mipmain版本仍然可用，只是功能不再有更新。**为了保证页面的质量和兼容性，我们建议大家升级到v1版本。


如果您有任何建议，可以到我们的[mipjs_github](https://github.com/mipengine/mip)和[mip组件_github](https://github.com/mipengine/mip-extensions)提issue或直接参与开发。