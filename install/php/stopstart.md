#PHP Agent开启关闭

### 关闭探针：

1、安装探针成功之后，在php.ini中找到oneapm配置模块，注释掉extension=oneapm.so 配置。

![](http://club.oneapm.com/uploads/default/original/2X/1/1629fba2c3d9b96a5720615e33032d983a24a299.png) <br>

php.ini查找oneapm配置模块

![](http://club.oneapm.com/uploads/default/original/2X/0/06bd130efec9795fc82539c8980ce9eb2694a085.png) <br>

未修改前的配置

![](http://club.oneapm.com/uploads/default/original/2X/8/8af9d2bfe0cf02d81af5c222eb082bfdfa4847ba.png) <br>

加了注释的配置

2、杀死oneapm-daemon进程。

![](http://club.oneapm.com/uploads/default/original/2X/7/7d5018d27b73245670048165846996184ddf0bc4.png) <br>

(说明：defunct进程有的存在有的不存在，并不影响使用)

3、重启php、apache或者nginx。

![](http://club.oneapm.com/uploads/default/original/2X/8/8dad21d5e0a53df6e7a464abf9c5f715f9397f74.png) <br>

重启之后 ps -ef|grep oneapm-daemon  查询进程，已经不存在，这个时候探针已经成功关闭。

### 开启探针：

1、打开php.ini文件，找到oneapm配置模块，并去掉 ;extension=oneapm.so 前面的注释。

![](http://club.oneapm.com/uploads/default/original/2X/1/1629fba2c3d9b96a5720615e33032d983a24a299.png) <br>

php.ini查找oneapm配置模块

![](http://club.oneapm.com/uploads/default/original/2X/8/8af9d2bfe0cf02d81af5c222eb082bfdfa4847ba.png) <br>

加了注释的配置

![](http://club.oneapm.com/uploads/default/original/2X/0/06bd130efec9795fc82539c8980ce9eb2694a085.png) <br>

去掉注释的配置

2、保存配置。重启php、apache或者nginx，可以看到oneapm-daemon也会随之重启，这时候开启探针成功。

![](http://club.oneapm.com/uploads/default/original/2X/8/86360f69eedf5174eff76eb245403421c5129ead.png) <br>

如果重启之后oneapm-daemon未能启动，可以手动重启。

sudo /usr/bin/oneapm-daemon
