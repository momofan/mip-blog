##MIP部分问题解答

## 功能支持问题
### 1、react能否和MIP结合使用，如果暂时不能以后是否有考虑？是否会和其他 js 框架(比如angular )结合?
  目前暂无计划支持

### 2. 是否支持cookie?实现 登录、统计、广告等功能?
cookie正在开发，登录功能已经在规划中，请关注[官网进展](https://www.mipengine.org/timeline.html#all)。
### 3. 统计功能如何实现的?
目前我们提供[百度统计](https://www.mipengine.org/doc/3-widget/3-customize-widget/stats-baidu-widget.html)，[天润统计](https://www.mipengine.org/doc/3-widget/3-customize-widget/stats-tianrun-widget.html),第三方站长开发的 [cnzz 统计](https://github.com/mipengine/mip-extensions/tree/master/mip-stats-cnzz),，还有 [mip-pix 自定义统计](https://www.mipengine.org/doc/3-widget/2-inner-widget/pix-widget.html)。在页面中引入相应的组件就可以实现统计功能。
###4. 请求如何发出，如AJAX，官方提供了什么组件？
可以用 fetch 自行实现
示例： 

```
fetch(location.href).then(function (res) {
    return res.text();
}).then(function (text) {
    fetchElement.innerHTML = 'fetch: ' + (text.search('mip-test') !== -1);
});
```

 如果需要 ajax 取数据渲染页面，可以使用 mip-list组件，目前正在开发中，请关注
[官网进展](https://www.mipengine.org/timeline.html#all)。
### 5. 是否支持GA(谷歌统计)?
MIP暂不支持GA，后续会有计划支持。
### 6. 样式外链 css，若外链 css 的更新问题
mip 推荐使用内联的 css；多一次网络请求，阻塞渲染，速度会慢。外链也可使用，不过文件更新的频率是10天。如果目前机制上有问题，可以通过 github 的 issue 反馈给 mip 项目组。
### 7. 我们自定义组件的时候是否限制个数和规范?
暂无个数限制，规范需要通过组件平台的规范检查，我们还将对组件的功能场景进行 review，避免多个组件实现重复功能。未来我们会开放MIP组件平台，方便大家提交组件。
### 8. 样式冲突问题如何解决?
css完全可以自己定义，这个 mip 不做强制要求。
### 9. 如何分享域名?地址栏的域名以什么形式呈现?
分享的域名可以通过 mip-share组件自行定义，地址栏的域名最终会以 https://m.baidu.com/mip/yoururl 的形式呈现，目前正在开发中。
### 10. MIP对于自身广告支持， 第三方广告支持情况和进展?
自身广告可以通过开发扩展组件的形式支持，第三方广告目前能支持[百度网盟广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-baidu-widget.html)、[全网推荐广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-qwang-widget.html)，阿里妈妈广告的部分功能，如果有广告相关需求，提议在 github 上提交[issue](https://github.com/mipengine/mip-extensions/issues) 的方式和 mip 项目组交流。
###11. 组件开发周期
组件开发按照 [github 的标准](https://github.com/mipengine/mip-extensions/blob/master/docs/develop.md)，通过github提pull request,开发自测完成，可以通过组件平台上线，只要通过组件平台规范校验的都可以自动上线，上线时间小于1个小时。未来我们会开放MIP组件平台，方便大家提交组件。
###12. 组件之间交互 
 为了组件间的抽象分离，mip不建议做组件间的交互。但是可以通过dom加`on`属性的形式控制。如mip-lightbox 弹层组件与mip-sidebar 侧边栏组件，点击button按钮可以展开侧边栏。
示例:
mip-lightbox 默认是隐藏的，作为打开开关的 dom 节点 需设置 on 属性，且 on 属性的属性值为 "tap:组件ID.open"。

```
<button on="tap:my-lightbox.open" id="btn-open" role="button" tabindex="0">
    Open lightbox
</button>

<mip-lightbox
    id="my-lightbox"
    layout="nodisplay"
    class="mip-hidden">
    <div class="lightbox">
        <h1>Hello, World!</h1>
        <p> this is the lightbox</p>
    </div>
</mip-lightbox>
```


###13. APP 调起功能
目前此功能在计划开发中。

##工具和工程化问题
###1. gbk转utf8官方是否提供了工具或者方案？
GBK编码如何生成UTF-8网站（基于dedecms）
首先mip站的dede程序和m站的dede程序都公用一个数据库，然后

1. 找到 /include/dedetag.class.php 这个文件
2. 在文件里搜索找到 ”function SaveTo“
3. 把` fwrite($fp,$this->GetResult()); `改成 `fwrite($fp,iconv('gbk','utf-8//ignore',$this->GetResult()));`
4. 注意模板的头部写上是`<meta charset="utf-8">`
5. 然后，重刷mip全站就ok
P.S. 需要注意的是，程序、模板和数据库都是gbk格式的。

###2. 工具支持多组件调试
参照 wiki：https://github.com/mipengine/mip-cli/wiki/%E8%B0%83%E8%AF%95mip%E7%BB%84%E4%BB%B6
##Cache相关问题
###1. MIP构造的页面在页面改动后多久生效？
MIP-Cache的内容会在52分钟-5天内生效，访问频率较高的页面，52分钟就回触发 cache 更新，如果一直没有访问的页面，5天自动更新。
###2. 、一天8000条修改cache的限制能不能放宽？
这个接口仅用于紧急更新或删除url，不建议经常使用。如有特殊情况需要删除大量url，可以通过站长平台反馈。
###3. mipcache 充挂了会不会对站长带来什么影响?
mipcache稳定性目标4个9，如果是 cache 没有充成功，这个不影响站长，如果是指 cache 抓取导致站长服务不可用，这个会直接容灾到落地页。
###4.如果提交的网址错了，怎么删除错误的网址，另外把页面都改成404对站点排名有没有影响？
可以使用 cache 的更新接口，如果还有对应的 h5网页的话，对排名没有影响。
###5. 是否增加页面抓取的压力？（todo）

###6. 虽然mipcache对站长开放了紧急更新接口，但是一分钟限制了3个页面，当需要紧急更新的页面数量很多的时候，效率很低，这个能改进吗？
目前10s能更新一条，暂无计划放开，有特殊需求请从站长平台反馈。
###7. mipcache 的缓存时间是52min，但有的时候更新了页面，cache中的页面要一两天才更新？
MIP-Cache的内容会在52分钟-5天内生效，访问频率较高的页面，52分钟就回触发 cache 更新，如果一直没有访问的页面，5天自动更新。
###8. mipcache的更新时间是固定了吗，以后还会改变吗？
会改变，根据积累的数据的经验值进行变化。

##产品规范
###1. 悬浮限高目的，是否会修改标准
去掉悬浮，我们去掉的只是广告，不会影响页面中的其他内容，像悬浮组件还是存在于页面中的。
###2. mip不允许加广告问题？（todo）



##收录问题
###1.时效性新闻：不走站长平台提交（todo）
考虑一下时效性的方案：新闻源

##其他问题
###1.由于域名变了，对于其他搜索引擎来说，会不会影响我们网站的权重?（todo）
在原页面MIP化，不会影响其它搜索引擎的抓取收录，也不会影响页面权重。新增MIP页可通过robots.txt文件禁用其它搜索引擎的抓取，从而保证原页面的权重。
###2.页面的调整改动，没有我们自己页面上的方便？(todo)
在封装组件时，MIP建议考虑组件的可扩展性，如宽高和图片可以作为参数传入。这样能够减少组件修改的次数。后期我们会开放组件开发平台，加快组件审核和上线的效率
###3.以后上边的广告位是否会控制？(todo)
 百度网盟和MIP下线悬浮广告，是出于用户体验的角度考虑。内嵌的广告不会遮挡页面，目前不会控制。