#调试MIP网页

首先创建一个本地开发组件用的文件夹，存储位置自选，建议存储空间足够大，这时我们已经安装好了git，右键点击此文件夹弹出菜单 我们选择
![Alt text](./img/12_gitbash.png)

输入这行命令 克隆一个mip-extensions的版本库

`$ git clone  https://github.com/mipengine/mip-extensions.git`

出现如下代表克隆完成

![Alt text](./img/12_gitclone.jpg)

这时你会发现之前创建的文件夹里多了这个文件夹

![Alt text](./img/12_mip-extensions.jpg)

接下来我们在当前根目录下进行初始化mip 配置：

`$ mip init`

会创建mip.config文件，相关配置如下：
在这里继续gitbush here 输入以下命令
` mip server`
![Alt text](./img/12_mipserver.jpg)


