## 校验相关
### 1. MIP 页面的 `<a>`链接校验报错，MIP 是强制 target=“_blank” 吗?  

如果想直接跳转MIP页，可以用[mip-link 组件](https://www.mipengine.org/doc/3-widget/3-customize-widget/link-widget.html)；MIP 页 `<a>` 强制跳出是为了解决 MIP 体验的问题，12月底会升级校验，去掉强制target=“_blank”。

### 2. 静态文件引用，一定要用绝对路径么？

目前是，一定要使用“带有协议头和域名”的绝对路径，比如”https: //m.baidu.com/a.jpg”。未来有计划取消这条规则，请关注[官网进展](https://www.mipengine.org/timeline.html#all)。

### 3. `<a href=“m.a.com”>test</a>`标签`<a>`中的属性’href’的属性值’m.a.com’无效?标签’a’的强制性属性’target’缺失？

标签href属性可以为“//m.a.com”, “http: //m.a.com”, “https: //m.a.com”三种。标签强制target=“_blank”, 因为在iframe嵌套页面跳转有问题。可以加上target=“blank”，如果直接跳转到另一个MIP页，可以直接使用 [mip-link 组件](https://www.mipengine.org/doc/3-widget/3-customize-widget/link-widget.html)解决。

<br>
## 广告相关
### 1. MIP页的网盟广告为什么在uc和qq下不显示？

如果您使用了[网盟广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-baidu-widget.html)`type="ad-baidu"`, 可以尝试使用[网盟扩展广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-baidu-wm-ext-widget.html)`type="ad-baidu-wm-ext"`。

### 2. 从百度结果页打开MIP页，为什么反屏蔽广告不展示？

反屏蔽广告必须是 https 的，如果原页面正常，在[预览环境](https://www.mipengine.org/validator/preview)下却不展示很可能是站点域名未注册https；在[网盟扩展广告文档](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-baidu-wm-ext-widget.html)的注意事项中有说明，或者看网络控制台有没有js获取不到的报错。

### 3. 从百度结果页打开MIP页，为什么悬浮广告不展示？

不只悬浮广告，MIP 页面中所有的悬浮元素（布局为 position: fixed 的元素）联盟广告自带的贴底广告都需要使用 mip-fixed 悬浮组件进行支持，使用细节可参考 [mip-fixed 悬浮组件](https://www.mipengine.org/doc/3-widget/3-customize-widget/fixed-widget.html)。

<br>
## 组件相关
### 1. 为什么mip和组件和AMP不完全一样？
市场环境不同。国内有一些浏览器兼容性不好，MIP组件需要额外增加兼容代码。

### 2. 百度统计组件为什么不生效？
1) mip-stats-baidu.js 依赖 mip.js，所以要把 mip.js 写到前面；
2) 标签名和所使用的脚本应该保持一致；
3) 确认标签使用的是`<mip-stats-baidu>`而不是`<mip-stats-bidu>` 。
4) 确认脚本引用的是`https://mipcache.bdstatic.com/static/v1/mip-stats-baidu/mip-stats-baidu.js`。
```
<!--正确示例-->
<mip-stats-baidu token="4e397f684261b9e4ff9d8ad4714f5b2b"></mip-stats-baidu>
<script src="https://mipcache.bdstatic.com/static/v1/mip.js"></script>
<script src="https://mipcache.bdstatic.com/static/v1/mip-stats-baidu/mip-stats-baidu.js"></script>
```

### 3. 悬浮组件如何关闭？
mip-fixed 悬浮组件支持关闭功能，详见[文档](https://www.mipengine.org/doc/3-widget/3-customize-widget/fixed-widget.html)-关闭悬浮元素的方法。

#### 4. 自己开发扩展组件，使用了`<script type=”application/json”>`标签，在标签内的JSON属性值配置html，MIP 页面会乱码？
示例：
```
 <script type="application/json">
    {
        "key": "<div>value</div>"
    }
</script>
```
解释：MIP 不会对上述情况进行特殊处理，需要扩展组件的开发者在标签`<script>`中使用encodeURIComponent对html进行编码，然后在组件中进行解码

### 5. 自定义组件上线后访问404？
首先，组件pr merge后并能马上使用，需要操作上线，上线后会在 github 的 changelog 中更新；
然后，确认所访问的组件线上地址是正确的：
```
https://mipcache.bdstatic.com/static/v1/{组件名}/{组件名}.js
```

<br>
## 其他问题
### 1. MIP 页面如何使用cookie？
MIP 页面暂时不支持cookie，所有的cookie会被清除，后期MIP项目组会提供cookie的统一解决方案。

### 我的网站使用了302跳转, mip-cache会抓取302跳转后的页面么？
会，但mip-cache只会根踪一次302跳转，抓取重定向后的页面。如果网站使用了多次302跳转，mip-cache会抓取失败，导致触发cache降级逻辑，在用户访问时直接打开mip页，不使用异步极速框架，有损用户体验。如有多次302的需求，请通过[邮件](mailto:mip-support@baidu.com)与MIP项目组联系。
<br>
谢谢阅读。如有补充，欢迎留言