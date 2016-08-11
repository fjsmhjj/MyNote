# .NET Agent 兼容环境和功能列表


OneAPM 的 .NET Agent 在监控的 .NET 应用程序内部运行。对所有 .NET 兼容语言均可用，比如 VB.NET，C#，C++/CLI。

安装.NET Agent，您必须在操作系统的 admin 组中有管理员权限（不是用户权限）。您需要以用户管理者的身份登录，或者（在比较新的操作系统中）在权限弹窗出现时提供权限确认。

**注意：虽然 OneAPM 的 .NET Agent 监控 .NET应用程序，但它并不监控不基于 .NET 的 经典ASP 应用。**<br>

## 兼容和需求

.NET Agent 在监控的 .NET 程序中运行。Agent并不需要关联单独的程序或者 Windows 服务。IIS启动后，它将自动运行。

在您安装 .NET Agent 之前，请确保您的应用程序符合安装需求。


## 支持列表

### .NET


* .NET 2.0 或更高版本

### CLRs


* 2.0  

* 4.0

### .NET框架


* .NET Framework 2.0

* .NET Framework 3.0

* .NET Framework 3.5

* .NET Framework 4.0

* .NET Framework 4.5

* .NET Framework 4.5.1

### 操作系统


* Windows Server 2003

* Windows Server 2008

* Windows Server 2012

* Windows Vista

* Windows 7

注意： OneAPM 不支持 Windows XP、.NET 1.x  和 Windows RT。

### 数据库


.NET agent 可以监控 .NET 应用以下数据库发出的请求的性能，但 agent 不会直接监控数据库的处理过程。

* SQL Server

* Oracle

* MySQL

* PostgreSQL

* Enterprise library

* MongoDB

* Memcached

* Redis

注意：在 SQL trace 中捕获的 .Net SQL 参数不会为参数化的查询或者存储过程列出参数。

### 应用程序框架


* ASP .NET MVC 2

* ASP .NET MVC 3

* ASP .NET MVC 4

* ASP .NET MVC 5

* ASP .NET Web API

* ASP .NET Web Forms

* SOAP-based Web Services

* 支持WCF（包括自托管的WCF）

* 支持 ServiceStack 框架 V3，V4版本， 以及ServiceStack Rest Url的合并。

注意：OneAPM 目前不支持 Mono，是一个在 Linux 上运行的 .Net 框架。因为目前没有 Profiler API 可以作为剖析器嵌入 Mono 的 .Net 应用。Profiler API 是一个 Component Object Model （COM）为基础的界面，不受 Linux 支持。

* 支持 self-host WCF services

### CMS


* Umbraco

* DotNetNuke
