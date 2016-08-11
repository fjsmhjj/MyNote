# Node.js Agent 安装方法
目前 Nodejs 提供两种方式安装方法

一、下载及安装

**安装方法一**

 * 定位至你的应用程序的根目录下

 * 1.2.8 以下的版本，请在应用程序的根目录下运行以下指令：

``` stylus
npm install oneapm --registry http://npm.oneapm.com
```

 * 1.2.8 及以上的版本，请在应用程序的根目录下运行以下指令：

``` stylus
npm install oneapm
```

* 等待安装成功


**安装方法二**

1.下载 OneAPM Nodejs Agent
 
下载 OneAPM Nodejs Agent 安装程序到所在项目的文件夹下或者使用

``` stylus
wget https://user.oneapm.com/account/70895d373d2c0424a381b90a574630b8/agent/
node/OneAPM_node_Agent_latest.tgz
```

2.安装 OneAPM Nodejs Agent
 
定位至你的应用程序的根目录下并运行

``` stylus
npm install <Location Of Your OneAPM Agent>/oneapm-latest.tgz
```

3.等待安装成功

二、配置

1. 将 node_modules/oneapm 中的 oneapm.js 文件复制到应用程序的根目录下
2. 修改配置文件 oneapm.js，设置 app_name，将 license_key 替换为 OneAPM 提供的license_key
3. 复制以下代码至应用程序主模块文件第一行

``` stylus
require('oneapm');
```

三、如有可能，重启您的应用服务器

四、静候几分钟开启您的应用性能监控之旅