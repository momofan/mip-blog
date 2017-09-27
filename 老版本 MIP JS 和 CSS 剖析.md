## 为什么使用 MIP v1 稳定版本？
在2016年末，MIP官方发布了[v1新版本](http://www.cnblogs.com/mipengine/p/6077510.html)文件。v1版脚本不存在两位或三位的版本号，mip.js引用地址如下：

https://mipcache.bdstatic.com/static/v1/mip.js

### 1、使用方便
文件地址只需添加一次，不用担心版本更新问题。

### 2、功能最新
使用v1版本可以无感知的获得MIP最新的功能，任何功能的升级都会实时同步到 v1 版本。

### 3、完美兼容
v1版本的所有文件是互相完美兼容的，v1版本不兼容老版本（存在两位或三位的版本号）的文件，如果v1和老版本文件混用，概率出现js报错、样式等问题。

## 附录

### 老版本示例
``` html
    <!-- 老版本css -->
    <link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/mipmain-v1.1.1.css">
    <!-- 老版本js -->
    <script src="https://mipcache.bdstatic.com/static/mipmain-v0.0.1.js" ></script>
    <script src="https://mipcache.bdstatic.com/static/v1.1/mip-stats-cnzz.js"></script>
```

### v1版本文件地址规则

``` html
    <!-- 唯一的v1 css -->
    <link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/v1/mip.css">
    <!-- 唯一的mip主js文件 -->
    <script src="https://mipcache.bdstatic.com/static/v1/mip.js" ></script>
    <!-- 
        通用组件
        https://mipcache.bdstatic.com/static/v1/组件名/组件名.js
    -->
    <script src="https://mipcache.bdstatic.com/static/v1/mip-list/mip-list.js"></script>
    <!-- 
        开发者扩展组件
        https://mipcache.bdstatic.com/extensions/platform/v1/组件名/组件名.js
    -->
    <script src="https://mipcache.bdstatic.com/extensions/platform/v1/mip-cambrian/mip-cambrian.js"></script>
```
