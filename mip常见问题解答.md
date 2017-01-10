# VIP站长大会(北京站)常见问题解答

## 功能支持问题
### 1、react能否和MIP结合使用，如果暂时不能以后是否有考虑？是否会和其他 js 框架(比如angular )结合?
  目前暂无计划支持。

### 2.MIP页是否支持自定义cookie?实现 登录、统计、广告等功能?

`<mip-cookie>`组件正在开发，登录功能已经在规划中，会在`<mip-access>`组件中实现。
### 3. MIP的统计功能如何实现的?
目前我们提供[百度统计](https://www.mipengine.org/doc/3-widget/3-customize-widget/stats-baidu-widget.html)，[天润统计](https://www.mipengine.org/doc/3-widget/3-customize-widget/stats-tianrun-widget.html),第三方站长开发的 [cnzz 统计](https://github.com/mipengine/mip-extensions/tree/master/mip-stats-cnzz),，还有 [mip-pix 自定义统计](https://www.mipengine.org/doc/3-widget/2-inner-widget/pix-widget.html)。在页面中引入相应的组件就可以实现统计功能。
### 4. 与服务端异步交互请求如何发出，如AJAX，官方提供了什么组件？
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
[github issue](https://github.com/mipengine/mip-extensions/issues/297)。
### 5. MIP是否支持GA(谷歌统计)?
MIP暂不支持GA，后续会有计划支持。
### 6. MIP是否支持外链的 css样式表，如果外链 css，更新时间是多久?
MIP推荐使用内联的 css，但是并不禁止外链。使用外链样式表，会多一次网络请求，阻塞渲染，拖慢页面速度。外链css样式表也可使用mip-cache，文件更新的频率是10天，如果需要实时更新，可以采用在文件名后增加文件版本号的方法。
### 7. 第三方自定义组件的时候是否限制个数和规范?
暂无个数限制，规范需要通过[FECS](http://fecs.baidu.com/demo)的规范检查，请保证新提交的组件不重复实现已有功能。未来我们会开放MIP组件平台，方便大家提交组件。
### 8. 样式冲突问题如何解决?
MIP不限制页面中的CSS(position:fixed除外)，可自定义样式覆盖mip.css。
### 9. 如何分享域名?地址栏的域名以什么形式呈现?
分享的域名可以通过 [mip-share](https://www.mipengine.org/doc/3-widget/3-customize-widget/share-widget.html)组件自行定义，地址栏的域名最终会以 https://m.baidu.com/mip/yoururl 的形式呈现，目前正在开发中。
### 10. MIP对于自身广告支持， 第三方广告支持情况和进展?
MIP广告组件目前能支持[百度网盟广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-baidu-widget.html)、[全网推荐广告](https://www.mipengine.org/doc/3-widget/5-ad-widget/ad-qwang-widget.html)，自定义的广告也可以通过开发扩展组件的形式支持。如果有其他通用性广告的相关需求，提议在 github 上提交[issue](https://github.com/mipengine/mip-extensions/issues) 与mip 项目组交流。
### 11. 组件开发后多久可以上线?
组件开发按照 [github 的标准](https://github.com/mipengine/mip-extensions/blob/master/docs/develop.md)，开发自测完成后，通过github提pull request的方式提交到主干,每周二周四下午上线，未来可以通过组件平台上线，只要通过组件平台规范校验的都可以自动上线，上线时间小于1个小时。
### 12. 组件之间是否可以交互?
 为了组件间的抽象分离，mip不建议做组件间的交互。但是可以通过dom加`on`属性的形式控制。如[mip-lightbox 弹层组件](https://www.mipengine.org/doc/3-widget/3-customize-widget/lightbox-widget.html)与[mip-sidebar 侧边栏组件](https://www.mipengine.org/doc/3-widget/3-customize-widget/sidebar-widget.html)，点击button按钮可以触发展开收起。


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


### 13. APP 调起功能
目前此功能在计划开发中，请关注[github issue #282](https://github.com/mipengine/mip-extensions/issues/282)。

## 工具和工程化问题
### 1. gbk转utf8官方是否提供了工具或者方案？
GBK编码如何生成UTF-8网站（基于dedecms）
首先mip站的dede程序和m站的dede程序都公用一个数据库，然后

1. 找到 /include/dedetag.class.php 这个文件
2. 在文件里搜索找到 ”function SaveTo“
3. 把` fwrite($fp,$this->GetResult()); `改成 `fwrite($fp,iconv('gbk','utf-8//ignore',$this->GetResult()));`
4. 注意模板的头部写上是`<meta charset="utf-8">`
5. 然后，重刷mip全站就ok
P.S. 需要注意的是，程序、模板和数据库都是gbk格式的。

### 2. MIP-CLI工具支持多组件调试
参照 wiki：https://github.com/mipengine/mip-cli/wiki/%E8%B0%83%E8%AF%95mip%E7%BB%84%E4%BB%B6
##Cache相关问题
### 1. MIP-cache缓存页面在页面改动后多久生效？
MIP-Cache的内容会在52分钟-5天内生效，访问频率较高的页面，52分钟就会触发 cache 更新，如果一直没有访问的页面，5天自动更新。
### 2. 、一天8000条修改cache的限制能不能放宽？
这个接口仅用于紧急更新或删除url，不建议经常使用。如有特殊情况需要删除大量url，可以通过站长平台反馈。
### 3. mipcache 更新异常会不会对用户访问产生影响?
我们会尽量保证MIP-cache服务的稳定性。如果 cache 没有更新成功，不会影响用户访问。如果 cache 抓取导致站长MIP页不可访问，按照容灾策略会跳转到相应的h5页面。
### 4.如果提交的网址错了，怎么删除错误的网址，另外把页面都改成404对站点排名有没有影响？
可以使用站长平台 mip-cache 的更新接口，删除错误网址。如果还有对应的h5网页的话，对排名没有影响。
### 5. 使用MIP-cache是否增加页面抓取的压力？
会。MIP-cache为了保证页面的时效性，会在cache过期(52分钟-5天)后重新抓取所有页面,网站服务器会受到较高的qps压力。
### 6. 虽然mipcache对站长开放了紧急更新接口，但是一分钟限制了3个页面，当需要紧急更新的页面数量很多的时候，效率很低，这个能改进吗？
目前限制10s能更新一条，如果有特殊需求请从站长平台反馈。
### 7. mipcache的更新时间是固定的吗，以后还会改变吗？
会改变，根据积累的数据的经验值进行变化。

## 产品规范
### 1. `mip-fixed`悬浮组件为什么要限制最大高度?未来是否会修改限高的标准?
限高是为了避免悬浮元素遮挡页面过多影响用户浏览体验，未来暂时不会修改标准。

## 收录问题
### 1.时效性H5已经被百度收录，如何快速提交MIP页?
未来可以在站长平台提交MIP页和原页面的映射关系(pattern)。提交后我们会校验MIP页和H5页的内容相似度，通过即可立即生效。

## 其他问题
### 1.由于域名变了，对于其他搜索引擎来说，会不会影响我们网站的权重?
在原页面MIP化，不会影响其它搜索引擎的抓取收录，也不会影响页面权重。新增MIP页可通过robots.txt文件禁用其它搜索引擎的抓取，从而保证原页面的权重。

MIP相关的内容可以这么写(假设您的目录是/mip/):

```
User-agent: Baiduspider
（这里不用写关于mip的内容）

User-agent: Googlebot
Disallow: /mip/
```

### 2.页面的调整改动需要将代码提交到github上并上线，没有直接在页面上引入script脚本方便?
在封装组件时，MIP建议考虑组件的可扩展性，如宽高和图片可以作为参数传入。这样能够减少组件修改的次数。后期我们会开放组件开发平台，加快组件审核和上线的效率。
### 3.以后上边的广告位是否会控制？
 百度网盟和MIP下线悬浮广告，是出于用户体验的角度考虑。内嵌的广告不会遮挡页面，目前不会控制。