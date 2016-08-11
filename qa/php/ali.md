阿里云ECS Linux服务器php-fpm启动报错：allow_call_time_pass_reference处理方法:

**问题描述：**

![](http://club.oneapm.com/uploads/default/original/2X/6/6aaecb6917c176d965ebf5fa8ed87bbd0ae85a48.png)

    php-fpm启动失败，报错：/etc/init.d/php-fpm restart Gracefully shutting down php-fpm warning， no pid file found - php-fpm is not running ? Starting php-fpm

    Fatal error:  Directive 'allow_call_time_pass_reference' is no longer available in PHP in Unknown on line 0

**分析解决：**

failed现象一般是由于php.ini配置中开启了 allow_call_time_pass_reference = on 参数导致，在php目前的高版本中未对此参数提供兼容支持，需要注释掉。

    在php.ini中找到对应条目，前面加；号注释后，重新启动php-fpm即可。
