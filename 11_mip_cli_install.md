# MIP-CLI 开发工具安装步骤详解

## MIP-CLI 依赖
需要安装**node**环境以及**git**

node的安装方法:

  windows下:
[node安装教程](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85node&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=node%20%E5%AE%89%E8%A3%85&rsv_t=a785CqyQ9RpKKCL78%2BpfCb%2BYbG57Dg9%2BVh8nCkL11e%2Fy4rNwHzfH1OLxqhlqOneaYodNDKwf&rsv_sug1=49&rsv_sug7=101&rsv_pq=8ecb9b0c00007ff4&rsv_sug3=36&rsv_sug2=0&inputT=24514&rsv_sug4=26243)

  mac下:
 [node安装教程](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85node&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=node%20%E5%AE%89%E8%A3%85&rsv_t=a785CqyQ9RpKKCL78%2BpfCb%2BYbG57Dg9%2BVh8nCkL11e%2Fy4rNwHzfH1OLxqhlqOneaYodNDKwf&rsv_sug1=49&rsv_sug7=101&rsv_pq=8ecb9b0c00007ff4&rsv_sug3=36&rsv_sug2=0&inputT=24514&rsv_sug4=26243)


git的安装方法:

  windows下:
[git安装教程](https://www.baidu.com/s?wd=windows%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=mac%E4%B8%8B%E5%AE%89%E8%A3%85nodejs&rsv_t=d110N%2Bj0kMrkYiNWUYjNtW9ux3ILb%2BI2AwypVDVonpP%2B%2Bvbxi01rUp55PQDNPlK0XGIVB83w&rsv_pq=c402cbb000009353&inputT=24514&rsv_sug3=58&rsv_sug1=67&rsv_sug7=100&bs=mac%E4%B8%8B%E5%AE%89%E8%A3%85nodejs)

  mac下:
 [git安装教程](https://www.baidu.com/s?wd=mac%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_spt=1&rsv_iqid=0xd4abf74300005ce5&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=93912046_hao_pg&rsv_enter=1&oq=windows%E4%B8%8B%E5%AE%89%E8%A3%85git&rsv_t=5eb6FU22Qo8IXaLHm6afHBRe%2F3ncNACCRxIOkR6QAP0EFBKXn4UWWypr7vvRhOmPjcdKnhWF&rsv_pq=fde61d5200009578&inputT=69859&rsv_sug3=65&rsv_sug1=72&rsv_sug7=100&bs=windows%E4%B8%8B%E5%AE%89%E8%A3%85git)

## 安装
依赖环境:**Node.js (>=4.x)**  
如果你不知道你安装的node是什么版本请在node中输入以下指令

```
node -v
```

示例:    
![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_node_v.jpg)

将安装好的node打开 输入以下指令:

```
$ [sudo] npm install -g mip-cli
```
如果此处安装出现问题，<a href="#question1">请点击这里

 出现以下界面显示正在安装


 ![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_install.jpg)



想检验我们是否安装成功可以输入以下命令


```
mip -V
```

如果出现了mip的版本号，则表示安装成功

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_mip_V.jpg)

如果无法使用npm进行安装，[请点这里](#question2)  

接下来我们还需要安装optimizer
再输入一个命令


```
npm i -g mip-extension-optimizer
```

安装成功如下图：

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_optimizer.jpg)

至此，我们就成功安装了mip-cli工具。

## 安装过程中可能出现的问题

<span id="question1"></span>
 注意： **nodejs 5.x, 6.x** 安装模块时，可能会报**node-gyp**相关错误，像这样



![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_error.jpg)


需要使用如下命令安装

```
$ [sudo] npm install --unsafe-perm -g mip-cli
```


   **nodejs 5.x** 安装**bufferutil**模块时可能会报编译错误，建议使用**4.4**或者**6.x**以上版本。


<span id="question2"></span>

***
如果npm安装模块出了问题，请尝试淘宝**npm**镜像**-cnpm**进行安装


```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```


安装淘宝镜像完成后再重复上述步骤


```
cnpm install -g mip-cli
```

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_done.jpg)

安装成功界面如图

![Alt text](https://github.com/mipengine/mip-blog/blob/master/img/11_done2.jpg)