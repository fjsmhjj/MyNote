
# .NET Agent 参数配置

* OneAPM .NET Agent 从 oneapm.config 配置文件中获取配置信息。你可以在这些位置找到该配置文件：
Agent 版本为 .NET Agent v1.2.0.0及以上：

* 开始菜单\所有程序\OneAPM\.Net.Agent\OneAPM.config

![](https://oneapm.kf5.com/attachments/download/342174/00156582d9bc34d56e7d79429069b37)

* OneAPM Agent 安装后的目录：
```
Default： %ALLUSERSPROFILE%\OneAPM\.NET Agent
Windows 2003 only： %ALLUSEQinRSPROFILE%\Application Data\OneAPM\.NET.Agent
```
**注：** %ALLUSERSPROFILE% 是指列出所有用户 Profile 文件位置。

# 参数说明
```
      <configuration xmlns="urn：OneAPM-config" agentEnabled="true">
```

### agentEnabled

 * **默认值：** true
 * **生效方式：** 重新加载 Agent
 * **可选参数：** [ true | false ]
 * **参数说明：** 设置为 true 将启用 OneAPM Agent，设置为 false 将停用 OneAPM Agent。
```
 <service licenseKey="OneAPM 提供的 LICENSE" ssl="false" host="tpm.oneapm.com" port="80"/>
```

 * **参数说明：** 设置为 true 将启用 OneAPM Agent，设置为 false 将停用 OneAPM Agent。</td>

         <service licenseKey="OneAPM 提供的 LICENSE" ssl="false" host="tpm.oneapm.com" port="80"/>


### licenseKey

 * **生效方式：** 重新加载 Agent
 * **可选参数：** OneAPM 提供的 license 许可
 * **参数说明：** 配置正确的 License 许可后，OneAPM Agent 将与 OneAPM server 通信，使得 OneAPM 探针正常工作。

### ssl

* **默认值：** false
* **生效方式：** 重新加载 Agent
* **可选参数：** [ true | false ]
* **参数说明：** 设置为 true，指定 OneAPM Agent 使用 HTTPS 与 OneAPM Server 加密通信，设置为 false 则采用 HTTP 方式通信。

### host


* **生效方式：** 重新加载 Agent
* **可选参数：** [ IP地址| 域名 ]
* **参数说明：** 指定 OneAPM agent 与 OneAPM server 的通信地址。

### port

* **默认值：** 80
* **生效方式：** TCP 端口
* **参数说明：** 指定 OneAPM Agent 与 OneAPM server 的通信端口。
```
  <proxy host="hostname"  port="81"  domain="mydomain.com"  user="oneapm"  password="xyz"/>
```
* 使用代理服务器上网时，需要配置 Proxy 节点。它是 Service 节点的子节点。

### host

* **生效方式：** 重新加载 Agent
* **可选参数：** IP 地址
* **参数说明：** 代理服务器 IP。

### port


* **生效方式：** 重新加载 Agent
* **可选参数：** 端口
* **参数说明：** 代理服务器通信端口

### domain

* **生效方式：** 重新加载 Agent
* **可选参数：** 域名
* **参数说明：** 代理服务器域名


### user

* **生效方式：** 重新加载 Agent
* **可选参数：** 用户名
* **参数说明：** 代理服务器用户名

### password

* **生效方式：** 重新加载 Agent
* **可选参数：** 密码
* **参数说明：** 代理服务器密码


### 配置站点显示名称
* 站点显示名称
```
<application enableAutoAppNaming="false">
  <name>MyApplication</name>
</application>
```

### enableAutoAppNaming

* **默认值：** false
* **生效方式：** 重新加载 Agent
* **可选参数：** true|false
* **参数说明：** 设置为 false，按服务器显示站点；设置为 true，以站点所在 IIS 应用程序池作为应用程序显示。


### name

* **默认值：** My Application
* **生效方式：** 重新加载 Agent
* **参数说明：** 初始化应用程序名称，当中间件部署多个应用时，OneAPM Agent 将所有应用程序数据统一记录到初始化应用程序中。
```
        <log level="off" />
```

### log level

* **默认值：** off
* **生效方式：** 立即生效
* **参数类型：** ［off｜fatal｜error｜warn｜info｜debug｜trace｜finest（all）］
* **参数说明：** 设置非 off 值将记录 OneAPM Agent 的工作日志，当您需要进行故障分析时，参数级别决定日志的细度。


### 日志输出级别

* **fatal：** 严重 fatal
* **error：** 错误 fatal+error
* **warn：** 警告 fatal+error+warn
* **info：** 正常 fatal+error+warn＋info
* **debug：** 调试 fatal+error+warn＋info＋debug
* **trace：** 细度 fatal+error+warn＋info＋debug＋trace
* **fatal：** 最好 fatal+error+warn＋info＋debug＋trace+ fatal
```
< requestParameters enabled="false">
    <ignore>credit_card</ignore>
</requestParameters>
```

### requestParameters enabled

* **默认值：** false
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 参数用于控制是否启用请求 HTTP 参数过滤的功能。

### ignore

* **生效方式：** 重新加载 Agent
* **参数说明：** 过滤业务 HTTP 请求参数，例：credit_card，多个参数以逗号分隔。
```
<transactionTracer enabled="true" transactionThreshold="apdex_f"
         stackTraceThreshold="500" recordSql="obfuscated"
         explainEnabled="true" explainThreshold="500" />
```

### enabled

* **默认值：** true  
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 参数为 transaction tracer 的子参数，用于控制是否启用 transaction tracer 功能。


### transactionThreshold

* **默认值：** apdex_f
* **生效方式：** 重新加载 Agent
* **参数说明：** 当事务执行时间超过该值时，事务将生成 Trace。该参数以秒为单位可以设置整数或浮点数。
* **注意：** 参数为 apdex_f 时，OneAPM 将使用 apdex_t 的 4 倍参数值。

### stackTraceThreshold


* **默认值：** 500
* **生效方式：** 重新加载 Agent
* **参数说明：** 参数以毫秒为单位，当 Web 事务或 SQL 响应时间超过该值时，OneAPM 将收集并展示相应 stackTrace。

### recordSql


* **默认值：** obfuscated
* **生效方式：** 重新加载 Agent
* **参数类型：** [ off | raw | obfuscated ]
* **参数说明：** 当启用 transaction_tracer 功能时，该参数标记 SQL 记录的模式，off 为不记录 SQL，raw 为不进行处理并记录原始的 SQL 语句，obfuscated 为经过处理的 SQL 语句，加密显示语句的字符串或数字参数。

### explainEnabled

* **默认值：** true
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 参数以毫秒为单位，设置为 true，将在 SQL 语句的 TRACE 中生成缓慢 SQL 语句的执行计划。


### explainThreshold

* **默认值：** 500
* **生效方式：** 重新加载 Agent
* **参数说明：** 当 explain_enabled 为 true 时，OneAPM agent 捕捉 SQL 执行时间超过该值的 SQL 并生成执行计划。
```
<crossApplicationTracer enabled="true" />
```

### crossApplicationTracer enable

* **功能说明：** 跨越应用程序记录外部调用次数与响应时间。
* **默认值：** true
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 设置为 true，将记录跨越应用程序记录外部调用次数与响应时间。
```
         <errorCollector enabled="true">
            <ignoreErrors>
              <exception>System.IO.FileNotFoundException</exception>  
              <exception>System.Threading.ThreadAbortException</exception>   
            </ignoreErrors>
            <ignoreStatusCodes>
              <code>401</code>
              <code>404</code>
            </ignoreStatusCodes>
         </errorCollector>
```

### errorCollector enabled

* **默认值：** true
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 参数为用于控制是否启用 error 收集功能。

### ignore_errors

* **生效方式：** 重新加载 Agent
* **参数说明：** 当启用 error 收集功能后，该参数用于忽略指定业务代码中类引发的错误信息。多个类名称以<exception></exception>分隔。


### ignoreStatusCodes

* **默认值：** 404
* **生效方式：** 重新加载 Agent
* **参数类型：** 错误代码
* **参数说明：** 该参数用于忽略指定业务 HTTP 的错误代码，多个代码以<code></code>分隔，例如 404，505



### 配置浏览器监控
* 浏览器监控
```
       <browserMonitoring autoInstrument="false" sslForHttp="false"
      isJsText="false" byteMode="true" />
```
### autoInstrument


* **默认值：** false
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 启用真实用户体验，OneAPM Agent 能够记录用户浏览器下载和加载应用系统的时间。设置为 true，OneAPM Agent 自动在 ASP 中插入 API 指令，注入JavaScript 语句进行监控。

### isJsText


* **默认值：** false
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 参数为 browser_monitoring 的子参数，用于控制是否启用监控 JavaScript 功能。

### sslForHttp


* **默认值：** false
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 设置为 true，指定 OneAPM Agent 使用 HTTPS 与 OneAPM Server 加密通信，设置为 false 则采用 HTTP 方式通信。

### byteMode


* **默认值：** true
* **生效方式：** 重新加载 Agent
* **参数类型：** [ true | false ]
* **参数说明：** 设置为 true，浏览器监控会采用字节流方式插入探针；设置为 false，则采用字符流方式。
```
         <assembles>
            <ignore name="PllC.Comm.Trace"/>
            <ignore name="PllC.Runtime.Protect"/>
            <ignore name="PllC.Runtime.Protect64"/>
         </assembles>
```

* **生效方式：** 重新加载 Agent
* **参数说明：** 忽略某些 assembly 的配置，用户可以自己配置和添加忽略这些加密的 assembly 。
