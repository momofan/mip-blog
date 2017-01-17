# MIP开发教程(二)  使用MIP-CLI工具调试MIP网页

- [初始化mip配置](#no1)    
- [新建一个MIP网页](#no2)    
- [编写mip网页代码](#no3)    
- [校验MIP网页](#no4)    
- [调试MIP网页](#no5)  

<div id="no1">   </div>

## 1.初始化mip配置  

我们在`html`目录下进行初始化mip 配置：  

```
$ mip init
```

![mipinit](https://github.com/mipengine/mip-blog/blob/master/img/12_mipinit.jpg)  

此时会创建`mip.config`文件，  

![mip.config](https://github.com/mipengine/mip-blog/blob/master/img/12_mipconfig.jpg)

<div id="no2">   </div>  

## 2.新建一个MIP网页

在`mip-project/html`文件夹下输入如下命令：
```
$ mip add index.html
```
![addindex](https://github.com/mipengine/mip-blog/blob/master/img/12_addindex.jpg)

成功添加后，本地文件夹中会出现index.html 文件，这就是一个基础的MIP页面 

![index.html](https://github.com/mipengine/mip-blog/blob/master/img/12_indexhtml.jpg)  


![index](https://github.com/mipengine/mip-blog/blob/master/img/12_index.jpg)  

在新建网页的时候可以添加需要载入的mip组件js脚本，例如：

```
$ mip add index.html mip-share
```

![mipshare](https://github.com/mipengine/mip-blog/blob/master/img/12_mipshare.jpg)     

将在`index.html`中载入`mip-share`组件的js脚本 


![sharejs](https://github.com/mipengine/mip-blog/blob/master/img/12_sharejs.jpg)       

<div id="no3">   </div>  

## 3.编写mip网页代码

MIP页面新手指南可参见[官网文档-新手指南](https://www.mipengine.org/doc/00-mip-101.html)。在编写mip代码的时候需要注意符合mip网页规范，否则通不过mip校验程序，mip校验规则地址：

https://www.mipengine.org/doc/2-tech/2-validate-mip.html

<div id="no4">   </div>

## 4.校验MIP网页 

```
$ mip validate index.html
```

出现`ERROR`的条目通不过mip校验，需要进行修改。

例如：

![validate](https://github.com/mipengine/mip-blog/blob/master/img/12_validate.jpg)  


**注意**： 
mip页面应该为`utf-8`编码，其他编码格式通不过校验，如果需要使用其他编码格式，可以使用线上校验器粘贴代码进行校验，  

线上校验器地址：
https://www.mipengine.org/validator/validate  

<div id="no5">   </div>  

## 5.调试MIP网页

进入到html项目目录，启动`mip server`

```
$ mip server
```
![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/12_mipserver.jpg) 

访问`http://127.0.01:8000`进入调试页面:  

![12_mipserverlist](https://github.com/mipengine/mip-blog/blob/master/img/12_mipserverlist.jpg)  

**注意**：  

`mip server`默认监听`8000`和`35730`端口，如果有端口冲突可以在`mip.config`中修改启动端口。  
 
也可以使用`mip server -f`命令强制关闭当前占用端口的node进程(windows下无效)。   
 
<hr>
本系列共有三篇文章：  

- [MIP开发教程(一)  MIP-CLI工具安装与环境部署](https://github.com/mipengine/mip-blog/blob/master/11_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%80)%20%20MIP-CLI%E5%B7%A5%E5%85%B7%E5%AE%89%E8%A3%85%E4%B8%8E%E7%8E%AF%E5%A2%83%E9%83%A8%E7%BD%B2.md)
- MIP开发教程(二)  使用MIP-CLI工具调试MIP网页
- [MIP开发教程(三)  使用MIP-CLI工具调试组件](https://github.com/mipengine/mip-blog/blob/master/13_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%89)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95%E7%BB%84%E4%BB%B6.md)

