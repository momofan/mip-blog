## 老版本 MIP 文件问题剖析

本文写作的缘起：
1、在追查部分开发者问题的时候，发现问题是由于页面引入一些老版本的文件导致；
2、MIP 项目组技术方案的实现，在新版本的环境下是能正常运行的，但是在一些既引入了老版本的文件，也引入了新版本的文件，新老交杂的页面上，技术方案运行出现 bug。

基于如上的一些原因，本文先介绍 MIP 的老版本文件，然后列出老版本文件可能存在的一些问题，最后介绍 MIP 团队对于老版本的后续处理方法。

### 什么是老版本

老版本是什么？一时说不清楚，但是什么是最新的版本，这个有清楚的定义，可见[文章](http://www.cnblogs.com/mipengine/p/6077510.html)。从文章可以看出，非 v1 版本的 css 和 js 文件地址，均为老版本。
举例说明：
``` html
	<!-- 老版本css -->
	<link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/mipmain-v1.1.1.css">
	<!-- 老版本js -->
	<script src="https://mipcache.bdstatic.com/static/mipmain-v0.0.1.js" ></script>
	<script src="https://mipcache.bdstatic.com/static/v1.1/mip-stats-cnzz.js"></script>
```
从上可以看出，其中包含了`mipmain-v1.1.1.css`，`mipmain-v0.0.1.js`，`v1.1/mip-stats-cnzz.js`老版本的文件地址，其他的可以类推。

正如前文所述，新版本的都是 v1 版本，上面的对应的新版本如下所示：

``` html
	<!-- 老版本css -->
	<link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/v1/mip.css">
	<!-- 老版本js -->
	<script src="https://mipcache.bdstatic.com/static/v1/mip.js" ></script>
	<script src="https://mipcache.bdstatic.com/extensions/platform/v1/mip-cambrian/mip-cambrian.js"></script>
	<script src="https://mipcache.bdstatic.com/static/v1/mip-stats-cnzz/mip-stats-cnzz.js"></script>
```

### 老版本存在的问题

老版本是 MIP 团队早期的版本迭代的技术方案，由于该方案对应的版本号不定，会产生开发者需求频繁更新的困扰，所以，在16年11月统一版本的 v1 诞生。

#### 1、 版本兼容问题
v1版本不对老版本进行兼容处理，所以这就意味着，如果页面使用 v1 版本的脚本，那该页面上的所有的 MIP 脚本和 css 的版本需要都是 v1 版本的，如果同时存在新老交杂的情况，页面展现没有问题，但页面功能会出现问题，包括组件的功能、组件样式等。
下面举个栗子。
从一个 MIP 页面，看到他们的 MIP 的脚本引入如下图：
![脚本版本混用](img/case2.png)
可以看到控制台 js 报错如下图：
![控制台 js 报错](img/case1.png)

从上面的 case 可以看出，如果要用老版本就全用老版本，如果用 v1 版本就全用 v1 版本。当然，作者在这呼吁，有长期维护稳定的 v1 版本，为什么要用老版本呢？所有的都升级到 v1 版本是最佳的 MIP 实践。

#### 2、 功能使用问题

what？我按照官网组件使用，添加到了页面，为什么这个组件的一些功能缺失？

OK，因为我们的功能迭代只针对 v1 版本，老版本的功能都是16年11月前开发实现的，在这个之后的功能，都是在老版本上缺失的。官网介绍的组件功能，当然也是针对 v1 版本的。可以从官网的所需脚本可以看出，如下图：
![组件所需脚本](img/case3.png)

如果避免上述问题呢？

同理，我们都按照 v1 版本来添加页面的 MIP 文件即可。

### 老版本的处理方式

1、通过本文，呼吁开发者都是用稳定的最新的 v1 版本；

2、17年Q4，我们会升级校验模块，对这部分使用的问题，进行 warning 提示，让开发者便于发现和修改；

3、将老版本的文件添加到 MIP 校验中，通过规则使这部分页面 MIP 校验失败。

第3种处理办法，我们执行的节奏是：

1、老版本的页面流量非常小；

2、提前一个月发文进行预告通知。

OK，在本文最后，再次呼吁所有开发者，使用 MIP 的 [v1 版本](http://www.cnblogs.com/mipengine/p/6077510.html)的文件。


