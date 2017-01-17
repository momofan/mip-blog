# 开发教程(四)  MIP组件平台使用说明
使用组件审核平台上传mip组件，经过自动校验之后，提交平台审核，通过审核的组件会定时推送到线上，供网站使用。

## 使用说明

使用平台前请参考前三章文档

- [MIP开发教程(一)  MIP-CLI工具安装与环境部署](https://github.com/mipengine/mip-blog/blob/master/11_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%80)%20%20MIP-CLI%E5%B7%A5%E5%85%B7%E5%AE%89%E8%A3%85%E4%B8%8E%E7%8E%AF%E5%A2%83%E9%83%A8%E7%BD%B2.md)
- [MIP开发教程(二)  使用MIP-CLI工具调试MIP网页](https://github.com/mipengine/mip-blog/blob/master/12_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%BA%8C)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95MIP%E7%BD%91%E9%A1%B5.md)  
- [MIP开发教程(三)  使用MIP-CLI工具调试组件](https://github.com/mipengine/mip-blog/blob/master/13_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%89)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95%E7%BB%84%E4%BB%B6.md)  

### 登录平台

使用｀百度帐号｀登录组件平台，登录成功之后需要设置自己的个人信息，以便于组件上线之后通知组件所有人。

![mip-platform-login](https://raw.githubusercontent.com/mipengine/mip-cli/gh-pages/example/mip-platform-login.png)

### 上传组件

点击`上传组件`按钮，上传mip组件`zip`压缩包，组件`zip`压缩包格式参考[组件压缩包示例](https://github.com/mipengine/mip-blog/blob/master/img/13_)(https://raw.githubusercontent.com/mipengine/mip-cli/gh-pages/example/mip-test.zip)
mip组件编写和调试，参考[MIP开发教程(三)  使用MIP-CLI工具调试组件](https://github.com/mipengine/mip-blog/blob/master/13_MIP%E5%BC%80%E5%8F%91%E6%95%99%E7%A8%8B(%E4%B8%89)%20%20%E4%BD%BF%E7%94%A8MIP-CLI%E5%B7%A5%E5%85%B7%E8%B0%83%E8%AF%95%E7%BB%84%E4%BB%B6.md)。



组件通过校验后，可以提交审核，没有通过校验的组件，需要进行修改，直到通过校验。

![mip-platform-upload](https://raw.githubusercontent.com/mipengine/mip-cli/gh-pages/example/mip-platform-upload.png)

### 审核组件

组件提交审核之后会被锁定，不能再进行上传或修改，需要管理员通过审核或者打回之后才能继续修改，管理员打回的组件，
需要根据打回原因进行相应修改后再提交。

### 上线组件

组件通过审核后，会在下一个上线窗口进行上线，组件上线之后，在本地可以引入上线后的组件进行验证，
用户可以在`组件提交记录`页面查看组件版本审核历史。

![mip-extensions-audit-record](https://raw.githubusercontent.com/mipengine/mip-cli/gh-pages/example/mip-extensions-audit-record.png)
