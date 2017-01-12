# 调试MIP网页

### 1.准备工作
先创建一个本地开发组件用的文件夹，存储位置自选，建议存储空间足够大，这时我们已经安装好了git，右键点击此文件夹弹出菜单 我们选择
![Alt text](./img/12_gitbash.jpg)，若右键菜单无此命令可以使用cd命令进入到目录中：

```
cd mip-project
```

### 2.初始化mip配置
我们在当前根目录下进行初始化mip 配置：  

```
$ mip init

```

此时会创建`mip.config`文件，  

![mip.config](./img/12_mipconfig.jpg)

### 3.新建一个MIP网页(todo)

```
$ mip add index.html
```
![index.html](./img/12_indexhtml.jpg)  

可以在新建网页的时候可以添加需要载入的mip组件，例如：

```
$ mip add index.html mip-img mip-video

```

将载入`mip-img`和`mip-video`两个组件

### 4.编写mip网页代码

在编写mip代码的时候需要注意符合mip网页规范，否则通不过mip校验程序，mip校验规则地址：

https://www.mipengine.org/doc/2-tech/2-validate-mip.html

### 5.校验MIP网页 

```
$ mip validate index.html
```

出现`ERROR`的条目通不过mip校验，需要进行修改。


![validate](./img/12_validate.jpg)









在这里继续gitbush here 输入以下命令

` mip server`  

![Alt text](./img/12_mipserver.jpg)


