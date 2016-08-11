# Node.js Agent 安装准备
## 准备工作

 - 安装 node。要求安装 0.8 以上版本，0.10 以上版本新增部分新功能(如错误追踪)。模块上的研发工作会在最新发布的 Node Release 版本上进行。
 - 确保你的 npm 版本足够新，使用 npm -v 查看。要求至少使用 1.4.28 版本, 建议使用最新版本。
 - 通过 npm install oneapm 安装或 npm install /oneapm-x.x.x.tgz 下载模块安装，以监测您希望监测的应用。
 - 复制 "nodemodules/oneapm/" 中的 oneapm.js 到应用的根目录中。
 - 编辑 oneapm.js，然后将 license key 的值替换为您自己的 license key。
 - 添加 require('oneapm')；作为 app 主模块的第一行。

当您启动应用时，OneAPM 会随之启动，而数据会在几分钟后出现在 OneAPM 用户界面上。因为 Agent 要最大限度地减少带宽量消耗，每分钟只传输一次数据。所以如果您的测试模块运行不足一分钟，将不会有数据传输给 OneAPM。该模块会将日志写入应用程序目录下的 oneapm.log 文件中。如果 OneAPM 不发送数据或您 app 的崩溃信息，日志可以帮助 OneAPM 明确问题出在哪里。所以，若您需要我们帮助您解决问题，请将 bug 报告或支持请求连同日志文件一起发送给我们。
## 升级 npm
如果您现在使用的是 1.4.28 之前的版本，并且希望升级到最新版本，可以按下面步骤操作：

 1. 运行 npm -v，确保您已安装 npm 并且可以正常工作。
 2. 如果您的系统是 Linux、SmartOS、OSX 或者 *NIX，运行 ls –l $(which npm)，并检查文件是否需要 root 或 admin 权限才能访问。若需要，那么在命令前面加上 sudo。
 3. 运行 npm install –g npm@latest，升级 npm。