# MIP开发教程(三)  使用MIP-CLI工具调试组件  
* [一. 在mip-extensions仓库中创建新的组件](#no1)
* [二.预览调试组件](#no2) 
* [三. 在MIP页中引用自己编写的MIP组件](#no3) 
* [四.组件提交到github仓库时需要进行校验](#no4) 
<div id="no1">   </div>

## 一. 在mip-extensions仓库中创建新的组件 

#### 1. 在`mip-extensions`目录中创建组件：  

```
$ mip addelement mip-alert    
```
![addelement](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalert.jpg)    

此时在`mip-extensions`文件夹中创建了`mip-alert`组件，  

![mip-alert](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalertlist.jpg)    

#### 2. 开发组件
  
- `mip-alert.js`用于定义组件，可参考下方示例。    
- `mip-alert.less`用于定义组件样式，可参考 [mip-fixed/mip-fixed](https://github.com/mipengine/mip-extensions/blob/master/mip-fixed/mip-fixed.less)。   
- `README.md`用于说明组件用法，可参考 [mip-fixed/README.md](https://github.com/mipengine/mip-extensions/blob/master/mip-fixed/README.md)。   
- `package.json`用于记录组件版本及开发者信息，可参考 [mip-fixed/package.json](https://github.com/mipengine/mip-extensions/blob/master/mip-fixed/package.json)。    

```
/**
 * @file mip-kkk 组件
 * @author Grace
 */
define(function (require) {
    var customElement = require('customElement').create();
    // 构造元素，只会运行一次
    customElement.prototype.build = function () {
        // TODO
        var btn = document.createElement('button');
        btn.innerHTML = '点我';
        btn.setAttribute('id', 'btn');
        btn.onclick = function () {
            alert('这是一个组件');
        };
        document.body.appendChild(btn);
    };
    return customElement;
});
```    
<div id="no2">   </div>

## 二. 预览调试组件
#### 1. 在`mip-extensions`目录下启动`mip server`来预览组件，预览页面访问的是`README.md`文件中的示例。  

```
$ mip server
```

![mip-extensions](https://github.com/mipengine/mip-blog/blob/master/img/13_mipserver.jpg)   

#### 2. 打开调试网页`http://127.0.0.1:8000/`会列出当前仓库中的组件，点击进入`mip-alert`组件预览。 

访问`http://127.0.01:8000`进入调试页面。   

![extension-list](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-server-list-alert.jpg)       

进入`mip-alert`组件中进行调试组件

![13_mipalertover](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalertover.jpg)  

代码保存后，`mip server`会自动刷新预览页面。  

<div id="no3">   </div>

## 三. 在MIP页中引用自己编写的MIP组件  
#### 1. 进入`mip-project/html`文件夹下，如果没有`mip.config`文件则执行`mip init`命令创建此文件。如果已经存在，
修改`mip.config`文件的字段`extensionsDir`为`../extensions`。    

![mipconfig](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-config.jpg) 

#### 2. 在`html`目录下启动`mip server`    

![13_mip-server-last](https://github.com/mipengine/mip-blog/blob/master/img/13_mip-server-last.jpg)       

访问`http://127.0.01:8000`进入调试页面。进入`mip-alert.html`页面，   
即能看到

![13_mipalertover](https://github.com/mipengine/mip-blog/blob/master/img/13_mipalertover.jpg)   


<div id="no4">   </div>

## 四.组件提交到github仓库时需要进行校验

使用如下命令校验： 
```
$ mip validateelement mip-demo
```

![mip-etensions-validate](https://github.com/mipengine/mip-blog/blob/master/img/13_mipvalidate.jpg)

组件通过校验之后，提交到仓库.












