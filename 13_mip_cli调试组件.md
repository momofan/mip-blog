# 开发教程(三)  使用MIP-CLI工具调试组件  
#### 使用mip-cli工具可以进行mip组件调试，包括2种方式：

- [调试mip-extensions仓库中的组件](#no1)
- [调试本地编写的mip组件](#no2)
-  [mip组件编译](#no3)

<div id="no1">   </div>

## 调试mip-extensions仓库中的组件 

#### 1.在`mip-extensions`目录下启动`mip server`  

```
$ mip server
```

![mip-extensions](https://github.com/mipengine/mip-blog/blob/master/img/13_mipserver.jpg)   

#### 2.创建MIP组件

在`mip-extensions`目录中创建组件：

```
$ mip addelement mip-demo  
```
![addelement](https://github.com/mipengine/mip-blog/blob/master/img/13_addelement.jpg)  

 
可以开始编写mip-demo组件代码以及`README.md`文件。

#### 3. 开发MIP组件


#### 3.打开调试网页`http://127.0.0.1:8000/`会列出当前仓库中的组件，点击进入`mip-demo`组件预览。 

访问`http://127.0.01:8000`进入调试页面。   

![extension-list](https://github.com/mipengine/mip-blog/blob/master/img/13_extension-list.jpg)       

进入`mip-demo`组件中进行开发，代码保存后，`mip server`会自动刷新预览页面。  


#### 4.组件提交到github仓库时需要进行校验，使用如下命令校验：

```
$ mip validateelement mip-demo
```

![mip-etensions-validate](https://github.com/mipengine/mip-blog/blob/master/img/13_mipvalidate.jpg)

组件通过校验之后，提交到仓库.

#### 5.需要在mip页面中查看组件效果，或同时预览多个组件的修改，参考[调试项目中的mip组件](#no2)

<div id="no2">   </div>
## 调试项目中的mip组件

有时候在项目中创建了mip组件，想要和mip页面一起调试，可以设置`mip.config`来实现。

例如：项目结构如下`mip-demo`为mip组件，`mip-demo.html`为使用了`mip-demo`组件的页面。

![ll](https://github.com/mipengine/mip-blog/blob/master/img/13_ll.jpg)  


mip-demo.html代码如下:

```html
<!DOCTYPE html>
<html mip>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
    <title><!-- 标题 --></title>
    <link rel="stylesheet" type="text/css" href="https://mipcache.bdstatic.com/static/v1/mip.css">
    <link rel="canonical" href="对应的原页面地址">
    <style mip-custom>
    /* 自定义样式 */
    </style>
</head>
<body>
<!-- 正文 -->
<mip-demo></mip-demo>
<script src="https://mipcache.bdstatic.com/static/v1/mip.js"></script>
<script src="https://mipcache.bdstatic.com/static/v1/mip-demo/mip-demo.js"></script>

</body>
</html>
```

**注意**

所有组件调试时引入方式都按照线上地址就可以，`mip server`会自动进行页面注入。


1.修改`mip.config`的字段`extensionsDir`为`./`，注意，是`./`不是`.`。

```javascript
    /**
     * 本地mip组件调试目录，主要用于开发组件时进行本地调试，会自动将本地mip组件注入到当前访问的页面中去
     *
     * @type {string}
     */
    extensionsDir: './',
```

2.启动mip server调试器，访问`mip-demo.html`页面可以看到，已经把项目中的`mip-demo`引入到页面了

![mipdemojs](https://github.com/mipengine/mip-blog/blob/master/img/13_mipdemojs.jpg)


## 下面是一个示例   
  
### 开发一个自动弹出窗口的组件 `mip-alert` 

 
#### 1. 在`mip-extensions`目录中创建组件：  

```
$ mip addelement mip-alert    
```
![addelement](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalert.jpg)    

在`mip-extensions`文件夹中创建了`mip-alert`组件，  

![mip-alert](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalertlist.jpg)    

#### 2. 在`mip-alert.js `文件中编写代码

![13_mip-alert-js](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-alert-js.jpg)       


可以开始编写`README.md`文件。  

#### 3. 添加`mip-alert.html `文件并引入我们创建的`mip-alert `组件  

```
mip add mip-alert.html   
```

![13_mipalerthtml](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalerthtml.jpg)    

#### 4. 修改根目录下`mip.config`文件的字段`extensionsDir`为`./`    

     
![mipconfig](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-config.jpg)  

#### 5. 在`mip-extensions`目录下启动`mip server`    

![13_mip-server-last](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-server-last.jpg)       

访问`http://127.0.01:8000`进入调试页面。找到`mip-alert`组件，进入`mip-alert.html`页面，   
即能看到弹出窗口  

![13_mipalertover](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalertover.jpg)   

#### 6. 组件提交到github仓库时需要进行校验，使用如下命令校验：

```
$ mip validateelement mip-demo
```



组件通过校验之后，提交到仓库即可。  



至此通过校验后，我们的`mip-alert`组件已经开发完成。   











