百度MIP的规范要求必须添加强制性标签canonical，不然[MIP校验工具](https://www.mipengine.org/validator/validate)会报错：
```
强制性标签<link rel="/^(canonical)$/"> 缺失或错误
```
这个标签怎么写？又是干什么用的呢？

**简单来说，canonical标签用于关联原页面和MIP页，保证MIP页继承原页面权重，在移动搜索时优先展现MIP页。**Canonical标签是MIP页连接外界的重要桥梁，不写或写错会导致MIP页不能和原页面产生联系，导致权重丢失，MIP页不展现。

## 0. “原页面”是哪个页面
**原页面**是相对于**MIP页**来讲的，如果在`m.a.com/1.html`的基础上，mip改造后得到`mip.a.com/1.html`，那么`m.a.com/1.html`就是`mip.a.com/1.html`的原页面。

## 1. 标签正确写法
Canonical标签添加在**MIP页**的`<head>`标签中，href指向**原页面**地址。
如：`mip.a.com/1.html`页面（MIP页）的正确写法为：
```
<!-- TODO: 使用请修改href-->
<link rel="canonical" href="http://m.a.com/1.html">
```

#### href指向原则：href指向百度移动搜索导流最多的页面。

不同情况下的href指向：

2. 如果同样的内容既存在对应的pc页，也存在移动页，那么href指向百度移动搜索流量大的页面。
3. 如果是动态页面，**原页面** 已经存在canonical标签，则href指向与原页面指向一致。
4. 如果 **原页面** 有多个版式，href指向流量最大的页面。
1. 如果没有对应的原页面url（如新建独立MIP站），则href指向MIP页本身。
2. 如果直接在当前url进行MIP改造并直接生效，则href指向MIP页本身。

## 2. 用处：关联原页面 继承页面权重 优先显示MIP页
在爬虫抓取MIP页后，会根据其中的canonical标签得到当前MIP页和原页面的关系，在移动端需要展现原页面时，优先展现体验更好、速度更快的MIP页。

一个类似的例子是在站长平台上提交移动端适配。在提交适配规则“`m.a.com/1.html`对应`www.a.com/1.html`”后，在移动端`m.a.com/1.html`会继承`www.a.com/1.html`的权重，优先展现`m.a.com/1.html`。


## 3. 补充说明：
1. **MIP页面和原始页面的主体内容应该大致相同。**如果内容相差较大，被如果搜索引擎判定主体内容不一致的话，会认为canonical标签无效。
2. **原网页与MIP页的url的对应关系尽量简单、直接**（[文档说明](https://www.mipengine.org/doc/2-tech/5-show-your-page.html)）。简明直接的对应关系有利于搜索引擎分析mip页与原网页的关系，加快MIP页被收录和展现的速度。
3. 历史上，MIP曾使用“standardhtml”来链接MIP页和原页面，这个标签已经被“canonical”代替，新提交的mip页不再需要写“standardhtml”了。