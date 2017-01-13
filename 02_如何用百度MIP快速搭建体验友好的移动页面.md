在读这篇文章之前，请确定你已经了解MIP定义及加速原理。如果不确定的话，可以到MIP官网了解。
## 改造前期准备和注意事项:

你可以选择直接将原先的移动站点直接改成MIP站，也可以单独再做一套MIP站点与移动站并存。
复杂的页面暂不建议MIP改造，目前对资讯、图文类支持已较好，若功能较为复杂的建议自定义组件或等待MIP项目小组开发。
改造需具备一定的html知识，改造MIP教程请按照教程来，特别注意大小写，建议全局小写。
我们从一个html页面的上下顺序一步步改造，只要按照本文章内的一步步来，即可完成MIP改造。

## 1. Doctype改造

1.1 打开你的模板或代码文件看第一行，将`<! DOCTYPE ***>`改为`<!DOCTYPE html>`

## 2. `<Html>`标签改造

2.1 完成第一步后，继续修改下一行代码，将： `<html xmlns="http://www.w3.org/1999/xhtml">`或：`<html lang="en">` 改成：`<html mip>`注意全部小写

## 3. Head部分改造

3.1 `<head>`标签必须是完全小写。
3.2 页面的编码必须是utf-8，修改声明为：`<meta charset="utf-8">`
3.3 页面中加入`<meta name="viewport" content="width=device-width, minimum-scale=1, initial-scale=1">`
3.4 页面中加入MIP专用样式文件`< link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/v1/mip.css" >`
3.5 这里需要告诉搜索引擎改页面对应的标准html页面地址，如果存在则标识`<link rel="canonical" href="https://www.baidu.com">` 其中href值修改成为与当前mip页面相对应的标准页面（移动页）url地址。如果只有mip页面没有相对应的标准页面则标识为：`<link rel="canonical" href="https://www.baidu.com">` 其中的href值为当前页面地址。[详细说明](http://www.cnblogs.com/mipengine/p/canonical_link.html)

## 4. Body内改造

4.1 首先`<body>`标签必须是小写的；
4.2 替换`<img>`, `<style>`, `<frame>`, `<form>`,`< input>`, `<textarea>`, `<select>`, `<option>`标签为对应MIP组件标签，具体见官网文档。
4.3 引用MIP-JS 运行环境 `<script src= "https://mipcache.bdstatic.com/static/v1/mip.js"></script>`放在页面尾部。

## 5. 使用MIP Cache注意事项

5.1 一般Cache图片、样式、脚本，做完上述4步后，修改资源地址为相对地址或合法绝对地址（以校验工具为准）；
5.2 Cache的内容需要更新需要通过MIP数据提交中的更新数据接口，把更新的url链接推送过去，等待百度更新。

## 6. 其他组件使用

6.1 除了上述这些需求外，一部分站点可能需要用到组件，官网文档包含了目前支持的所有组件，本文简单举例说明一下使用百度统计该如何实现：
6.2 查找原有百度统计工具查看统计JS代码(可全局查找 var _hmt 关键字)获取token（hm.js?之后的编码），在页面底部，所有script前放入代码：`<mip-stats-baidu token="22090d4a309827eb62bc1335b2b28f11（网站统计token值）"></mip-stats-baidu>`
6.3 去除原有百度统计工具查看统计JS代码，删除整段js.

更多教程参考，可查看：
- [MIP新手指南]https://www.mipengine.org/doc/00-mip-101.html
- [MIP 完整demo]https://www.mipengine.org/doc/01-mip-demo.html
- [canonical使用说明]http://www.cnblogs.com/mipengine/p/canonical_link.html