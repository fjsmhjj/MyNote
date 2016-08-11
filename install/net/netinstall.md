# .NET Agent 安装方法

### IIS 安装步骤：

* 登录 www.oneapm.com 官网，免费注册账号并登陆。

* 添加应用，选择 .NET，并记录 license key 值。

![](https://oneapm.kf5.com/attachments/download/404268/001568351c5e1443722ac3cc5bbc541)

* 在 IIS 安装栏目下，选择合适的安装包。

![](https://oneapm.kf5.com/attachments/download/404269/001568351ded5a31f73ab1bf923ddd4)

* 在您应用的服务器端安装Agent，安装过程中，需要输入之前记录的 license key 。

* 重启 IIS。

* 访问您的应用，静候几分钟，将可以在官网上开始应用性能之旅。


### Non-IIS 安装步骤：

* 登录 www.oneapm.com 官网，免费注册账号并登陆。

* 添加应用，选择 .NET，并记录 license key 值。

![](https://oneapm.kf5.com/attachments/download/404272/00156835271691796eb35177079d211)


* 在 Non-IIS 安装栏目下，选择合适的安装包。

![](https://oneapm.kf5.com/attachments/download/404273/00156835287371b919350f3749b8ed7)

* 在您应用的服务器端安装Agent，安装过程中，需要输入之前记录的 license key 。

* 打开配置文件 OneAPM.config，在配置文件中添加如下字段。

![](https://oneapm.kf5.com/attachments/download/404274/001568352953b5d64e1f21a2ffb47a5)
* 如有可能，重启您的应用服务器。

* 访问您的应用，静候几分钟，将可以在官网上开始应用性能之旅。
