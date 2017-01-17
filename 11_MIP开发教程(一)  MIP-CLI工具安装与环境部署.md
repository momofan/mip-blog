<div id="top">    </div> 

# MIP开发教程(一)  MIP-CLI工具安装与环境部署

- [依赖安装](#no1)  
- [安装MIP-CLI](#no2)  
- [安装 mip-extension-optimizer](#no3)  
- [创建开发文件结构](#no4)  

<div id="no1">  </div>
## 1. 依赖安装

MIP-CLI使用npm安装，依赖node环境：  

- [node安装-windows](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85node&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=node%20%E5%AE%89%E8%A3%85&rsv_t=a785CqyQ9RpKKCL78%2BpfCb%2BYbG57Dg9%2BVh8nCkL11e%2Fy4rNwHzfH1OLxqhlqOneaYodNDKwf&rsv_sug1=49&rsv_sug7=101&rsv_pq=8ecb9b0c00007ff4&rsv_sug3=36&rsv_sug2=0&inputT=24514&rsv_sug4=26243)
- [node安装-mac](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85node&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=node%20%E5%AE%89%E8%A3%85&rsv_t=a785CqyQ9RpKKCL78%2BpfCb%2BYbG57Dg9%2BVh8nCkL11e%2Fy4rNwHzfH1OLxqhlqOneaYodNDKwf&rsv_sug1=49&rsv_sug7=101&rsv_pq=8ecb9b0c00007ff4&rsv_sug3=36&rsv_sug2=0&inputT=24514&rsv_sug4=26243)

MIP-CLI开发组件需要git：

- [git安装-windows](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=mac%E4%B8%8B%E5%AE%89%E8%A3%85nodejs&rsv_t=d110N%2Bj0kMrkYiNWUYjNtW9ux3ILb%2BI2AwypVDVonpP%2B%2Bvbxi01rUp55PQDNPlK0XGIVB83w&rsv_pq=c402cbb000009353&inputT=24514&rsv_sug3=58&rsv_sug1=67&rsv_sug7=100&bs=mac%E4%B8%8B%E5%AE%89%E8%A3%85nodejs)
- [git安装-mac](https://www.baidu.com/s?wd=mac%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=windows%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_t=5eb6FU22Qo8IXaLHm6afHBRe%2F3ncNACCRxIOkR6QAP0EFBKXn4UWWypr7vvRhOmPjcdKnhWF&rsv_pq=fde61d5200009578&inputT=69859&rsv_sug3=65&rsv_sug1=72&rsv_sug7=100&bs=windows%E4%B8%8B%E5%AE%89%E8%A3%85git)

<div id="no2">  </div>  
## 2. 安装MIP-CLI

MIP-CLI：mip开发工具，用于MIP页面和组件的开发和校验。  

依赖环境: **Node.js (>=4.x)**  
输入`node -v` 查看node版本，如果版本为5.x，6.x，<a href="#question1">请点击这里</a>。

示例:     
![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_node_v.jpg)

将安装好的node打开 输入以下指令：

```
$ [sudo] npm install -g mip-cli
```

 出现以下界面显示正在安装


 ![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_install.jpg)


如果安装过程中有报错，<a href="#question2">请点击这里查看解决办法</a> 。  

检验是否安装成功可以输入`mip -V`，如果出现mip版本号，则表示安装成功。

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_mip_V.jpg)


<div id="no3">  </div>    

## 3. 安装 mip-extension-optimizer

MIP-extension-optimizer: mip组件编译工具，用于将mip-extension中的特定组件源码编译成js文件。  

```
npm i -g mip-extension-optimizer
```

安装成功如下图：

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_optimizer.jpg)

<div id="no4">  </div>  

## 4. 创建开发文件结构

打开https://github.com/mipengine/mip-extensions, fork一份mip-extensions项目代码，       
![fork](https://github.com/mipengine/mip-blog/blob/master/img/11_fork1.jpg)  

进入自己的mip-extension项目页，复制仓库地址， 
![fork](https://github.com/mipengine/mip-blog/blob/master/img/11_fork.jpg)  

 在本地创建一个开发用的文件夹`mip-project`，git clone mip-extensions仓库到`mip-project`文件夹下
```
git clone (刚才复制的仓库地址，如：https://github.com/xxxxxxx/mip-extensions.git)
```

建议文件目录结构如下图：

![11_tree](https://github.com/mipengine/mip-blog/blob/master/img/11_tree.jpg)  

其中html文件夹用来存放我们后续开发的mip页面

<hr>
本系列共有三篇文章：  

- [MIP开发教程(一)  MIP-CLI工具安装与环境部署](#top)
- [MIP开发教程(二)  使用MIP-CLI工具调试MIP网页](https://github.com/mipengine/mip-blog/blob/master/12_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%BA%8C)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95MIP%E7%BD%91%E9%A1%B5.md)
- [MIP开发教程(三)  使用MIP-CLI工具调试组件](https://github.com/mipengine/mip-blog/blob/master/13_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%89)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95%E7%BB%84%E4%BB%B6.md)

 

## 附：安装过程中可能出现的问题

<div id="question1">   </div>
 
### 1. node版本问题  

 **nodejs 5.x, 6.x** 安装模块时，可能会报**node-gyp**相关错误，像这样



![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_error.jpg)


需要使用如下命令安装

```
$ [sudo] npm install --unsafe-perm -g mip-cli
```


   **nodejs 5.x** 安装**bufferutil**模块时可能会报编译错误，建议使用**4.4**或者**6.x**以上版本。


<div id="question2"> </div>

### 2. 使用cnpm镜像安装  

如果npm安装模块出了问题，请尝试**npm**镜像**-cnpm**进行安装：


```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```


安装淘宝镜像完成后再重复上述步骤：


```
cnpm install -g mip-cli
```

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_done.jpg)

安装成功界面如图

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_done2.jpg)