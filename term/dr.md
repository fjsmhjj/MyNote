# Data Retention

- Data retention（数据存储）是指 Application Insight 内置的数据存储功能，系统将会自动保存从 OneAPM 探针接受到的数据。

###存储时间

- Application Insight 免费版用户数据的存储时间为 1 天；专业版用户 Metric Data 存储时间为 30 天， Trace Data 存储时间为 15 天。

- 数据存储时间如下表所示： 

<table>
	<thead>
  		<tr>
    		<th>数据类型</th>
			<th>免费版</th>
    		<th>专业版</th>
 		</tr> 
 	</thead>
	<tbody>
		<tr>
			<td>Metric Data</td>
			<td>1 天</td>
            <td>30 天</td>
        </tr>
		<tr>
			<td>Trace Data</td>
			<td>1 天</td>
            <td>15 天</td>
		</tr>
	</tbody>
</table>



###数据类型
- Application Insight 的数据类型包括 Metric Data 和 Trace Data 两类。
####1. Metric Data
- Metric Data 是指 Application Insight 基于用户数据得出的统计结果。如图中标注的 Apdex、Web 事务响应时间、Web 事务吞吐量和错误率等性能数据。

![](http://i.imgur.com/AeDSQC6.png)

- 主要的 Metric Data 如下表所示：

<table>
	<thead>
		<tr>
			<th>产品</th>
			<th>Metric Data</th>
	   	</tr>
	</thead>
	<tbody>
		<tr>
			<td>　　　　　　　　Application Insight</td>
			<td>
				　　　　　　　　Apdex<br>
   				　　　　　　　　吞吐量<br>
 				　　　　　　　　响应时间<br>
 			 	　　　　　　　　错误率<br>
 			 	　　　　　　　　CPU 使用率<br>
 			 	　　　　　　　　Memory 使用率<br>
			</td> 
		</tr>
	</tbody>
</table>
####2. Trace Data
- Trace Data 是指 Application Insight 得到的影响用户应用性能的关键信息。
如图中标注的错误列表

![](http://i.imgur.com/RKnE8BN.png)

- Trace Data 包含内容如下表所示： 

<table>
	<thead>
		<tr>
			<th>产品</th>
			<th>Trace Data</th>
	   	</tr>
	</thead>
	<tbody>
		<tr>
			<td>　　　　　　　　Application Insight</td>
			<td>
				　　　　　　　慢事务追踪<br>
   			    　　　　　　　最慢组件<br>
 				　　　　　　　错误列表<br>
			</td> 
		</tr>
	</tbody>
</table>
###数据展示
- Application Insight 以列表、拓扑图、折线图等多种形式向用户展示数据信息。根据用户查询时间范围选择的不同，提供相应的时间粒度。<br>
####时间选择
- Application Insight 提供不同的时间选择范围。如图所示：

![](http://i.imgur.com/0ycCri7.png)

- 以 Web 事务折线图为例，图中为最近 30 分钟的数据信息，折线图中时间粒度为 1 分钟，即折线图中点间最小时间间隔为 1 分钟。<br>
 
![](http://i.imgur.com/LsVxhmq.png)

##帮助

- 如需更多信息，欢迎访问 [http://support.oneapm.com](http://support.oneapm.com)