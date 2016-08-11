# SaaS-Ai API 接口文档


**版权声明**

本文档版权归北京蓝海讯通科技股份有限公司所有，并保留一切权利。未经书面许可，任何公司和个人不得将此文档中的任何部分公开、转载或以其他方式散发给第三方。否则，必将追究其法律责任。

**免责声明**

本文档仅提供阶段性信息，所含内容可根据产品的实际情况随时更新，恕不另行通知。如因文档使用不当造成的直接或间接损失，本公司不承担任何责任。

**文档更新**

适用版本: SaaS-Ai v2 
本文档由北京蓝海讯通科技股份有限公司于2016年6月最后修订。


---

## 1. 监控API

### 1.1 参数说明

+ `spanTime`: 最近时间
+ `interval`: 时间间隔
+ `type`: 可取值列表如下
    + `WebTransaction`
    + `External`
    + `Apdex`
    + `Datastore`
    + `Database`
+ `start`: 整数 (翻页起始位置)
+ `limit`: 整数 (每页显示item数目)
+ `orderBy`: 可取值列表如下
    + `ORDERBY_S1_S2_DESC`: 吞吐量
    + `ORDERBY_S2_S1_DESC`: 平均响应时间
    + `ORDERBY_S3_S1_DESC`: 平均执行时间
    + `ORDERBY_S1_DESC`: 调用次数
    + `ORDERBY_S2_DESC`: 响应时间
    + `ORDERBY_S3_DESC`: 调用次数
    + `ORDERBY_S4_ASC`: 最小值
+ `endTime`: 截至时间
+ `fields`: 可取值列表如下
    + `Apdex`
    + `Errors`
+ `name`: 可取值列表如下
    + `WebTransaction`
    + `DatabaseWeb`
    + `MongoDBWeb`
    + `MemcachedWeb`
    + `RedisWeb`
    + `ExternalWeb`
    + `CPU`
    + `Mem`

### 1.2 总览API

#### 1.2.1 总览响应时间

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
start:0
limit:5
name:WebTransaction
name:DatabaseWeb
name:MongoDBWeb
name:MemcachedWeb
name:RedisWeb
name:ExternalWeb
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/detail.json?api-key=api-key内容
&spanTime=1800000&interval=60000&start=0&limit=5&name=WebTransaction
&name=DatabaseWeb&name=MongoDBWeb&name=MemcachedWeb&name=RedisWeb
&name=ExternalWeb&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            454,  //调用次数
                            3.9524461030960083,  //响应时间总和
                            3.9524461030960083,  //执行时间
                            0.0030819999519735575,  //最小响应时间
                            0.040867000818252563,  //最大响应时间
                            0.07299500145018101  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				......
            ],
            "displayName": "WebTransaction",
            "id": 2428022611,
            "name": "WebTransaction",  //web事务
            "title": "WebTransaction",
            "type": "WebTransaction"
        },
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            212,  //调用次数
                            0.10384699981659651,  //响应时间总和
                            0.10384699981659651,  //执行时间
                            0.00034100000630132854,  //最小响应时间
                            0.0008360000210814178,  //最大响应时间
                            0.00005199999941396527  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				.....
            ],
            "displayName": "allWeb",
            "id": 2428022624,
            "name": "Database/allWeb", //web事务中的数据库类型metric
            "title": "Database",
            "type": "Database"
        },
        {
            "data": [], //num1~num6数据含义同上
            "displayName": "MongoDB/allWeb",
            "name": "Datastore/MongoDB/allWeb"  //web事务所有mongoDB操作总和
        },
        {
            "data": [],  //num1~num6数据含义同上
            "displayName": "Memcached/allWeb",
            "name": "Datastore/Memcached/allWeb" //web事务所有Memcached操作总和
        },
        {
            "data": [],  //num1~num6数据含义同上
            "displayName": "Redis/allWeb",
            "name": "Datastore/Redis/allWeb" //web事务所有redis操作总和
        },
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            106,  //调用次数
                            1.386326976120472,  //响应时间总和
                            1.386326976120472,  //执行时间
                            0.004679999779909849,  //最小响应时间
                            0.02655399963259697,  //最大响应时间
                            0.025056000566110015  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "allWeb",
            "id": 2428022647,
            "name": "External/allWeb", //web事务所有外部请求操作总和
            "title": "External",
            "type": "External"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.2.2 Apdex

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
start:0
limit:5
name:Apdex
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/detail.json?api-key=api-key内容
&spanTime=1800000&interval=60000&start=0&limit=5&name=Apdex&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "Apdex": [
                            454,  //正常调用次数
                            0,  //可容忍调用次数
                            0,  //不可容忍调用次数
                            0.5,  //ApdexT
                            0.5,  //ApdexT
                            0  //暂空
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				......
            ],
            "displayName": "Apdex",
            "id": 2428022549,
            "name": "Apdex", //所有Web事务Apdex指标
            "type": "Apdex"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.2.3 吞吐量

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
start:0
limit:5
name:WebTransaction
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/detail.json?api-key=api-key内容
&spanTime=1800000&interval=60000&start=0&limit=5&name=WebTransaction&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                 {
                    "fields": {
                        "result": [
                            46,  //调用次数
                            0.42274001240730286,  //响应时间总和
                            0.42274001240730286,  //执行时间
                            0.0032569998875260353,  //最小响应时间
                            0.036476001143455505,  //最大响应时间
                            0.0077840001322329044  //响应时间平方和
                        ]
                    },
                    "time": { //该段采样时间内的数据
                        "endTime": 1465378440000,
                        "startTime": 1465378380000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "WebTransaction",
            "id": 2428022611,
            "name": "WebTransaction",
            "title": "WebTransaction",
            "type": "WebTransaction"
        }
    ],
    "timeSpan": {
        "endTime": 1465378482826,
        "startTime": 1465376682826
    }
}
```

#### 1.2.4 Web事务

##### 1.2.4.1 获取每条Web事务的id

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:
type:WebTransaction
start:0
limit:3
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279716/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=&type=WebTransaction&start=0
&limit=3&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            9141,
                            451.3370990753174,
                            451.3370990753174,
                            0.01962300017476082,
                            1.129634976387024,
                            46.07066595554352
                        ]
                    },
                    "time": {
                        "endTime": 1465695720000,
                        "startTime": 1465693920000
                    }
                }
            ],
            "displayName": "Uri/discuz/upload/misc.php",
            "id": 2448907286,  // 获取该条Web事务对应的id
            "name": "WebTransaction/Uri/discuz/upload/misc.php",
            "title": "WebTransaction/Uri/discuz/upload/misc.php",
            "type": "WebTransaction"
        },
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            7999,
                            296.83630180358887,
                            296.83630180358887,
                            0.03432599827647209,
                            0.043685998767614365,
                            11.021471977233887
                        ]
                    },
                    "time": {
                        "endTime": 1465695720000,
                        "startTime": 1465693920000
                    }
                }
            ],
            "displayName": "Uri/discuz/upload/forum.php",
            "id": 2448907283,  // 获取该条Web事务对应的id
            "name": "WebTransaction/Uri/discuz/upload/forum.php",
            "title": "WebTransaction/Uri/discuz/upload/forum.php",
            "type": "WebTransaction"
        },
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            5713,
                            187.84444761276245,
                            187.84444761276245,
                            0.018213000148534775,
                            0.05569300055503845,
                            7.0720009952783585
                        ]
                    },
                    "time": {
                        "endTime": 1465695720000,
                        "startTime": 1465693920000
                    }
                }
            ],
            "displayName": "Uri/discuz/upload/member.php",
            "id": 2448907468,  // 获取该条Web事务对应的id
            "name": "WebTransaction/Uri/discuz/upload/member.php",
            "title": "WebTransaction/Uri/discuz/upload/member.php",
            "type": "WebTransaction"
        }
    ],
    "timeSpan": {
        "endTime": 1465695730381,
        "startTime": 1465693930381
    }
}
```

##### 1.2.4.2 根据Web事务id获取Web事务信息

+ url

`/ai/applications/{applicationId}/transactions/traces.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

begin:1800000
spanTime:1800000
offset:0
limit:3
orderBy:[object Object]
transType:webTransaction
metricId:2448907286
endTime:

**例子**

以`metricId=2448907286`为例，获取该条Web事务对应的信息。

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279716/transactions/traces.json
?api-key=api-key内容&begin=1800000&spanTime=1800000&offset=0&limit=3
&orderBy=%5Bobject+Object%5D&transType=webTransaction&metricId=2448907286&endTime=
```

+ 结果：

```
[
    {
        "agentName": "PHP:php-testapplication11:7070(iZ25znillayZ)",
        "agentRunId": 64505,
        "duration": 20,
        "guid": "411E74C1F4CF417A",
        "isPersist": 1,
        "ratio": 0.3125,
        "requestUrl": "http://123.56.244.166:7070/discuz/upload/misc.php",
        "rootMetricName": "Uri/discuz/upload/misc.php",
        "rootType": "WebTransaction",
        "startTime": "2016-06-12 09:13:22",
        "transactionId": 2616699015,
        "xrayId": 0
    },
    {
        "agentName": "PHP:php-testapplication11:7070(iZ25znillayZ)",
        "agentRunId": 64505,
        "duration": 22,
        "guid": "5DF06134559942AA",
        "isPersist": 1,
        "ratio": 0.34375,
        "requestUrl": "http://123.56.244.166:7070/discuz/upload/misc.php",
        "rootMetricName": "Uri/discuz/upload/misc.php",
        "rootType": "WebTransaction",
        "startTime": "2016-06-12 09:13:22",
        "transactionId": 2616699016,
        "xrayId": 0
    },
    {
        "agentName": "PHP:php-testapplication11:7070(iZ25znillayZ)",
        "agentRunId": 64505,
        "duration": 22,
        "guid": "326679066A2646D4",
        "isPersist": 1,
        "ratio": 0.34375,
        "requestUrl": "http://123.56.244.166:7070/discuz/upload/misc.php",
        "rootMetricName": "Uri/discuz/upload/misc.php",
        "rootType": "WebTransaction",
        "startTime": "2016-06-12 09:14:22",
        "transactionId": 2616708988,
        "xrayId": 0
    }
]
```

#### 1.2.5 错误率

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
fields:Errors
start:0
limit:5
name:WebTransaction
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/detail.json?api-key=api-key内容
&spanTime=1800000&interval=60000&fields=Errors&start=0&limit=5
&name=WebTransaction&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            454,  //调用次数
                            3.9524461030960083,  //响应时间总和
                            3.9524461030960083,  //响应时间总和
                            0.0030819999519735575,  //最小响应时间
                            0.040867000818252563,  //最大响应时间
                            0.07299500331282616	 //响应时间平方和
                        ]
                    },
                    "time": { //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "WebTransaction",
            "id": 2428022611,
            "name": "WebTransaction",
            "title": "WebTransaction",
            "type": "WebTransaction"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.2.6 服务器

+ url

`/ai/applications/{applicationId}/agents/overviews.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

begin:1800000
spanTime:1800000
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/agents/overviews.json
?api-key-api-key内容&begin=1800000&spanTime=1800000&endTime=
```

+ 结果：

```
[
    {
        "agentRunId": 63656,
        "agentVersion": "3.2.1",
        "apdexScore": 1,
        "applicationId": 2279554,
        "avgResponseTime": 0.008786079508692443,
        "cpm": 45.36666666666667, //吞吐量(call per minutes)
        "cpuRate": 0.0009820000113298496,
        "errorRate": 0,
        "hide": false,
        "host": "webapp1.webapp-mysql.local.flyacmeair.net",
        "identifier": "java:Acmeair-webapp:80(webapp1.webapp-mysql.local.flyacmeair.net)",
        "memUsed": 148.09695773654514,
        "memo": ";hide:false",
        "name": "java:Acmeair-webapp:80(webapp1.webapp-mysql.local.flyacmeair.net)" //显示名称
    }
]
```

### 1.3 Web事务API

#### 1.3.1 响应时间占比

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:WebTransaction
start:0
limit:20
orderBy:ORDERBY_S2_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=WebTransaction&start=0&limit=20&orderBy=ORDERBY_S2_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            1606,  //调用次数
                            53.30757984519005,  //响应时间总和
                            53.30757984519005,  //响应时间总和
                            0.02609900012612343,  //最小响应时间
                            0.07180699706077576,  //最大响应时间
                            1.8123899982310832  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465182000000
                    }
                }
            ],
            "displayName": "EJB/Entity/customersession/getId",
            "id": 2428022592,
            "name": "WebTransaction/EJB/Entity/customersession/getId",
            "title": "WebTransaction/EJB/Entity/customersession/getId",
            "type": "WebTransaction"
        },
        ......  //其它Web事务的数据
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.3.2 平均响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:WebTransaction
start:0
limit:20
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=WebTransaction&start=0
&limit=20&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：同上

#### 1.3.3 性能指数

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:WebTransaction
fields:Apdex
start:0
limit:20
orderBy:ORDERBY_S4_ASC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=WebTransaction&fields=Apdex&start=0
&limit=20&orderBy=ORDERBY_S4_ASC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "Apdex": [
                            1606, //正常调用次数
                            0,  //可容忍调用次数
                            0,  //不可容忍调用次数
                            0.5,  //ApdexT
                            0.5,  //ApdexT
                            0  //暂空
                        ]
                    },
                    "time": {
                        "endTime": 0,
                        "startTime": 1465182000000
                    }
                },
                {
                    "fields": {
                        "result": [
                            1606,  //调用次数
                            53.30757984519005,  //响应时间总和
                            53.30757984519005,  //响应时间总和
                            0.02609900012612343,  //最小响应时间
                            0.07180699706077576,  //最大响应时间
                            1.8123899982310832  //响应时间平方和
                        ]
                    },
                    "time": {
                        "endTime": 1465203600000,
                        "startTime": 1465182000000
                    }
                }
            ],
            "displayName": "EJB/Entity/customersession/getId",
            "id": 2428022592,
            "name": "WebTransaction/EJB/Entity/customersession/getId",
            "title": "WebTransaction/EJB/Entity/customersession/getId",
            "type": "WebTransaction"
        },
        ...... //其它Web事务的数据
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.3.4 吞吐量

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:WebTransaction
start:0
limit:20
orderBy:ORDERBY_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=WebTransaction&start=0
&limit=20&orderBy=ORDERBY_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            1284,  //调用次数
                            42.55347189307213,  //响应时间总和
                            42.55347189307213,  //响应时间总和
                            0.026921000331640244,  //最小响应时间
                            0.07180699706077576,  //最大响应时间
                            1.4423809978179634  //响应时间平方和
                        ]
                    },
                    "time": {
                        "endTime": 1465203600000,
                        "startTime": 1465182000000
                    }
                }
            ],
            "displayName": "EJB/Entity/customersession/getId",
            "id": 2428022592,
            "name": "WebTransaction/EJB/Entity/customersession/getId",
            "title": "WebTransaction/EJB/Entity/customersession/getId",
            "type": "WebTransaction"
        }
		......  //其它Web事务的数据
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.3.5 Top5 Web事务的响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

agentRunId:63656
spanTime:21600000
interval:600000
type:WebTransaction
start:0
limit:5
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&agentRunId=63656&spanTime=21600000&interval=600000
&type=WebTransaction&start=0&limit=5&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            52,  //调用次数
                            1.6603790074586868,  //响应时间总和
                            1.6603790074586868,  //响应时间总和
                            0.027338000014424324,  //最小响应时间
                            0.03795500099658966,  //最大响应时间
                            0.053344000363722444  //响应时间平方和
                        ]
                    },
                    "time": { //该段采样时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				......//其它采样时间段内的数据
            ],
            "displayName": "EJB/Entity/customersession/getId",
            "id": 2428022592,
            "name": "WebTransaction/EJB/Entity/customersession/getId",
            "title": "WebTransaction/EJB/Entity/customersession/getId",
            "type": "WebTransaction"
        },
		...... //其它Web事务的数据
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.3.5 吞吐量（折线图）

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

agentRunId:63656
spanTime:21600000
interval:600000
start:0
limit:5
name:WebTransaction
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/detail.json?api-key=api-key内容
&agentRunId=63656&spanTime=21600000&interval=600000&start=0&limit=5
&name=WebTransaction&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            454,
                            3.9524461030960083,
                            3.9524461030960083,
                            0.0030819999519735575,
                            0.040867000818252563,
                            0.07299500145018101
                        ]
                    },
                    "time": { //该段时间内的数据
                        "endTime": 1465203600000,
                        "startTime": 1465203000000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "WebTransaction",
            "id": 2428022611,
            "name": "WebTransaction",
            "title": "WebTransaction",
            "type": "WebTransaction"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

### 1.4 数据库API

#### 1.4.1 平均响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:Datastore
start:0
limit:20
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=Datastore&start=0&limit=20
&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            4420,  //调用次数
                            2.1211180007085204,  //响应时间总和
                            2.1211180007085204,  //响应时间总和
                            0.00033400001120753586,  //最小响应时间
                            0.006529000122100115,  //最大响应时间
                            0.001099000010981399  //响应时间平方和
                        ]
                    },
                    "time": {
                        "endTime": 1465203600000,
                        "startTime": 1465182000000
                    }
                }
            ],
            "displayName": "Database customer-select",
            "id": 2428022567,
            "name": "Database/customer/select", //Database/{数据库表名}/{数据库操作}
            "title": "",
            "type": "Database"
        },
        ...... //其它数据库的操作的数据
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.4.2 总响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:Datastore
start:0
limit:20
orderBy:ORDERBY_S2_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=Datastore&start=0&limit=20
&orderBy=ORDERBY_S2_DESC&endTime=
```

+ 结果：同上

#### 1.4.3 吞吐量

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:Datastore
start:0
limit:20
orderBy:ORDERBY_S1_S2_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=Datastore&start=0&limit=20
&orderBy=ORDERBY_S1_S2_DESC&endTime=
```

+ 结果：同上

#### 1.4.4 响应时间（折线图）

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
type:Datastore
start:0
limit:5
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=60000&type=Datastore&start=0
&limit=5&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            15,  //调用次数
                            0.006845000199973583,  //响应时间总和
                            0.006845000199973583,  //执行时间
                            0.0003480000013951212,  //最小响应时间
                            0.000598000013269484,  //最大响应时间
                            0.000003000000106112566  //响应时间平方和
                        ]
                    },
                    "time": { //该段采样时间内的数据
                        "endTime": 1465374600000,
                        "startTime": 1465374540000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "Database customer-select",
            "id": 2428022567,
            "name": "Database/customer/select", //Database/{数据库表名}/{数据库操作}
            "title": "",
            "type": "Database"
        }
		...... //其它数据库表的数据库操作的数据
    ],
    "timeSpan": {
        "endTime": 1465374637999,
        "startTime": 1465372837999
    }
}
```

#### 1.4.5 吞吐量（折线图）

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
type:Datastore
start:0
limit:5
orderBy:ORDERBY_S1_S2_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=60000&type=Datastore&start=0
&limit=5&orderBy=ORDERBY_S1_S2_DESC&endTime=
```

+ 结果：同上

### 1.5 外部服务API

#### 1.5.1 平均响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:
type:External
start:0
limit:20
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=External&start=0&limit=20
&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            3860,  // 调用次数
                            53.989871092140675,  // 响应时间总和
                            53.989871092140675,  // 执行时间
                            0.0035260000731796026,  //最小响应时间
                            0.06016800180077553,  //最大响应时间
                            1.0994140019174665  //响应时间平方和
                        ]
                    },
                    "time": {
                        "endTime": 1465203600000,
                        "startTime": 1465182000000
                    }
                }
            ],
            "displayName": "auth1.auth-service-mysql.local.flyacmeair.net/all",
            "id": 2428022621,
            "name": "External/auth1.auth-service-mysql.local.flyacmeair.net/all", //所有到目标主机地址的外部请求总和
            "title": "External/auth1.auth-service-mysql.local.flyacmeair.net",
            "type": "External"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.5.2 吞吐量

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

type:External
orderBy:ORDERBY_S1_DESC

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=21600000&interval=&type=External&start=0&limit=20
&orderBy=ORDERBY_S1_DESC&endTime=1465203600000
```

+ 结果： 同上

#### <h4 id="1.5.3">1.5.3 Top5 外部服务的响应时间</h4>

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
type:External
start:0
limit:5
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279554/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=60000&type=External&start=0&limit=5&endTime=
```

+ 结果： 

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            8,  //调用次数
                            0.10915900021791458,  //响应时间总和
                            0.10915900021791458,  //执行时间
                            0.004902999848127365,  //最小响应时间
                            0.02677999995648861,  //最大响应时间
                            0.002090000081807375  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465376520000,
                        "startTime": 1465376460000
                    }
                },
				...... //其它采样时间段内的数据
            ],
            "displayName": "auth1.auth-service-mysql.local.flyacmeair.net/all",
            "id": 2428022621,
            "name": "External/auth1.auth-service-mysql.local.flyacmeair.net/all", //所有到目标主机地址的外部请求总和
            "title": "External/auth1.auth-service-mysql.local.flyacmeair.net",
            "type": "External"
        }
    ],
    "timeSpan": {
        "endTime": 1465376556543,
        "startTime": 1465374756543
    }
}
```

#### 1.5.4 吞吐量（折线图）

同[Top5 外部服务的响应时间](#1.5.3)

### 1.6 后台任务API

#### 1.6.1 平均响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:
type:OtherTransaction
start:0
limit:20
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=&type=OtherTransaction&start=0
&limit=20&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            5,  //调用次数
                            0.012357000261545181,  //响应时间总和
                            0,  //暂空
                            0.00007000000186963007,  //最小响应时间
                            0.009735999628901482,  //最大响应时间
                            0.000097999996796716  //响应时间平方和
                        ]
                    },
                    "time": {
                        "endTime": 1465700520000,
                        "startTime": 1465698720000
                    }
                }
            ],
            "displayName": "org.apache.catalina.servlets.DefaultServlet/init",
            "id": 2872134663,
            "name": "OtherTransaction/Java/org.apache.catalina.servlets.DefaultServlet/init",
            "title": "",
            "type": "OtherTransaction"
        },
        ...... //其它后台任务的数据
    ],
    "timeSpan": {
        "endTime": 1465700540060,
        "startTime": 1465698740060
    }
}
```

#### 1.6.2 性能指数

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:3600000
interval:
type:OtherTransaction
fields:Apdex
start:0
limit:20
orderBy:ORDERBY_S4_ASC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=3600000&interval=&type=OtherTransaction
&fields=Apdex&start=0&limit=20&orderBy=ORDERBY_S4_ASC&endTime=
```

+ 结果：同上

#### 1.6.3 吞吐量

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:3600000
interval:
type:OtherTransaction
start:0
limit:20
orderBy:ORDERBY_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=3600000&interval=&type=OtherTransaction&start=0
&limit=20&orderBy=ORDERBY_S1_DESC&endTime=
```

+ 结果：同上

#### 1.6.4 响应时间占比

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:3600000
interval:
type:OtherTransaction
start:0
limit:20
orderBy:ORDERBY_S2_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=3600000&interval=&type=OtherTransaction&start=0
&limit=20&orderBy=ORDERBY_S2_DESC&endTime=
```

+ 结果：同上

#### 1.6.5 Top5后台任务的响应时间

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
type:OtherTransaction
start:0
limit:5
orderBy:ORDERBY_S2_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=60000&type=OtherTransaction&start=0
&limit=5&orderBy=ORDERBY_S2_S1_DESC&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            5,  //调用次数
                            0.012357000261545181,  //响应时间总和
                            0,  //暂空
                            0.00007000000186963007,  //最小响应时间
                            0.009735999628901482,  //最大响应时间
                            0.000097999996796716  //响应时间平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465699620000,
                        "startTime": 1465699560000
                    }
                },
                ...... //其它采样时间段内的数据
            ],
            "displayName": "org.apache.catalina.servlets.DefaultServlet/init",
            "id": 2872134663,
            "name": "OtherTransaction/Java/org.apache.catalina.servlets.DefaultServlet/init",
            "title": "",
            "type": "OtherTransaction"
        },
        ...... //其它后台任务的数据
    ],
    "timeSpan": {
        "endTime": 1465700086054,
        "startTime": 1465698286054
    }
}
```

#### 1.6.6 吞吐量（折线图）

+ url

`/ai/applications/{applicationId}/stats/topn.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:1800000
interval:60000
type:OtherTransaction
start:0
limit:5
orderBy:ORDERBY_S1_DESC
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2283633/stats/topn.json?api-key=api-key内容
&spanTime=1800000&interval=60000&type=OtherTransaction&start=0&limit=5
&orderBy=ORDERBY_S1_DESC&endTime=
```

+ 结果：同上

#### 1.6.7 CPU使用率

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:600000
start:0
limit:5
orderBy:ORDERBY_S1_DESC
name:CPU
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279556/stats/detail.json?api-key=api-key内容
&spanTime=21600000&interval=600000&start=0&limit=5&orderBy=ORDERBY_S1_DESC
&name=CPU&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            10,  //采样次数
                            0.010583000024780631,  //采样值总和
                            0.010583000024780631,  //采样值总和
                            0.0010189999593421817,  //采样中的最小值
                            0.0011070000473409891,  //采样中的最大值
                            0.000009999999974752427  //采样结果的平方和
                        ]
                    },
                    "time": {  //该段采样时间内的数据
                        "endTime": 1465182600000,
                        "startTime": 1465182000000
                    }
                },
                ...... //其它采样时间段内的数据
            ],
            "displayName": "User/Utilization",
            "id": 2428017207,
            "name": "CPU/User/Utilization",  //CPU利用率
            "type": "CPU"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

#### 1.6.8 内存使用情况

+ url

`/ai/applications/{applicationId}/stats/detail.json`

+ Request Method:

`GET`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

spanTime:21600000
interval:600000
start:0
limit:5
orderBy:ORDERBY_S1_DESC
name:MemoryUsed
endTime:

**例子**

+ Request URL:

```
https://api.oneapm.com/ai/applications/2279556/stats/detail.json?api-key=api-key内容
&spanTime=21600000&interval=600000&start=0&limit=5
&orderBy=ORDERBY_S1_DESC&name=MemoryUsed&endTime=
```

+ 结果：

```
{
    "results": [
        {
            "data": [
                {
                    "fields": {
                        "result": [
                            120,  //采样次数
                            16439.0947265625,  //采样值总和
                            16439.0947265625,  //采样值总和
                            127.20303344726562,  //采样中的最小值
                            146.8770751953125,  //采样中的最大值
                            2255517.5  //采样结果的平方和
                        ]
                    },
                    "time": { //该段采样时间内的数据
                        "endTime": 1465182600000,
                        "startTime": 1465182000000
                    }
                },
                ...... //其它采样时间段内的数据
            ],
            "displayName": "Used",
            "id": 2428017316,
            "name": "Memory/Used",  //物理内存使用率
            "type": "Memory"
        }
    ],
    "timeSpan": {
        "endTime": 1465203480000,
        "startTime": 1465181880000
    }
}
```

## 2. 报表API

### 2.1 Web事务报表API

+ url

`/ai/applications/{applicationId}/reports/transaction.json`

+ Request Method:

`POST`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

yesterday:yesterday
sameDayWeek:sameDayWeek
sevenDay:sevenDay
orderBy:throughput(default)|averageTime|totalTime

**例子**

+ Request URL:
`https://api.oneapm.com/ai/applications/2279554/reports/transaction.json?api-key=api-key内容`
+ Posted Form Data：
`yesterday=yesterday&sameDayWeek=sameDayWeek&sevenDay=sevenDay&orderBy=averageTime`
+ 结果：

```
[
    {
        "metricId": 2428022546,
        "metricName": "EJB/Entity/flightSegment/getFlightName",
        "values": {  // 结果集
            "yesterday": {  // 昨天的数据
                "apdexScore": 1,  // 性能指数apdex
                "averageTime": 0.00393173165604137,  // 平均响应时间
                "cpm": 26.827083333333334,  // 吞吐量
                "dissate": 0,  // 不满意次数
                "endTime": 1465228799000,
                "errorRate": 0,  // 错误率
                "metricId": 2428022546,
                "startTime": 1465142399000
            },
            "sameDayWeek": {  // 上周同一天的数据
                "apdexScore": 0,
                "averageTime": 0,
                "cpm": 0,
                "dissate": 0,
                "endTime": 1464710399000,
                "errorRate": 0,
                "metricId": 2428022546,
                "startTime": 1464623999000
            },
            "sevenDay": {  // 7天内的数据
                "apdexScore": 1,
                "averageTime": 0.004003353749600751,
                "cpm": 24.85952380952381,
                "dissate": 0,
                "endTime": 1465315199000,
                "errorRate": 0,
                "metricId": 2428022546,
                "startTime": 1464710399000
            },
            "today": {  // 今天的数据
                "apdexScore": 1,
                "averageTime": 0.0039242472308862126,
                "cpm": 13.10138888888889,
                "dissate": 0,
                "endTime": 1465315199000,
                "errorRate": 0,
                "metricId": 2428022546,
                "startTime": 1465228799000
            }
        }
    }
]
```

### 2.2 数据库报表API

+ url

`/ai/applications/{applicationId}/reports/database.json`

+ Request Method:

`POST`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

yesterday:yesterday
sameDayWeek:sameDayWeek
sevenDay:sevenDay
orderBy:throughput(default)|averageTime|totalTime

**例子**

+ Request URL:
`https://api.oneapm.com/ai/applications/2279554/reports/database.json?api-key=api-key内容`
+ Posted Form Data：
`yesterday=yesterday&sameDayWeek=sameDayWeek&sevenDay=sevenDay&orderBy=averageTime`
+ 结果：

```
[
    {
        "metricId": 2431115505,
        "metricName": "Database customer-update",
        "values": {  // 结果集
            "yesterday": {  // 昨天的数据
                "averageTime": 0.0005623816693930418,  // 平均响应时间
                "cpm": 1.3409722222222222,  // 吞吐量
                "endTime": 1465228799000,
                "metricId": 2431115505,
                "startTime": 1465142399000,
                "totalTime": 1.0859590035979636  // 总时间
            },
            "sameDayWeek": {  // 上周同一天的数据
                "averageTime": 0,
                "cpm": 0,
                "endTime": 1464710399000,
                "metricId": 2431115505,
                "startTime": 1464623999000,
                "totalTime": 0
            },
            "sevenDay": {  // 7天内的数据
                "averageTime": 0.0005590523701868545,
                "cpm": 1.2370039682539682,
                "endTime": 1465315199000,
                "metricId": 2431115505,
                "startTime": 1464710399000,
                "totalTime": 6.970824003859889
            },
            "today": {  // 今天的数据
                "averageTime": 0.0005545028321084272,
                "cpm": 0.6131944444444445,
                "endTime": 1465315199000,
                "metricId": 2431115505,
                "startTime": 1465228799000,
                "totalTime": 0.48962600075174123
            }
        }
    }
]
```

### 2.3 JVM报表API

+ url

`/ai/applications/{applicationId}/reports/jvm.json`

+ Request Method:

`POST`

+ Content-Type:

`application/x-www-form-urlencoded`

+ 参数：

yesterday:yesterday
sameDayWeek:sameDayWeek
sevenDay:sevenDay
orderBy:throughput(default)|averageTime|totalTime

**例子**

+ Request URL:
`https://api.oneapm.com/ai/applications/2279554/reports/jvm.json?api-key=api-key内容`
+ Posted Form Data：
`yesterday=yesterday&sameDayWeek=sameDayWeek&sevenDay=sevenDay&orderBy=averageTime`
+ 结果：

```
[
    {
        "metricId": 63656,
        "metricName": "java:Acmeair-webapp:80(webapp1.webapp-mysql.local.flyacmeair.net)",
        "values": {  // 结果集
            "yesterday": {  // 昨天的数据
                "apdexScore": 1,    // 性能指数apdex
                "averageTime": 0.008966938131547643,  // 平均响应时间
                "cpm": 45.60486111111111,  // 吞吐量
                "cpu": 0.0009731166840841373,  // CPU
                "endTime": 0,
                "errorRate": 0,  // 错误率
                "mem": 151.26934360169,  // 内存
                "metricId": 63656,
                "startTime": 0
            },
            "sameDayWeek": {  // 上周同一天的数据
                "apdexScore": 0,
                "averageTime": 0,
                "cpm": 0,
                "cpu": 0,
                "endTime": 0,
                "errorRate": 0,
                "mem": 0,
                "metricId": 63656,
                "startTime": 0
            },
            "sevenDay": {  // 7天内的数据
                "apdexScore": 0.9999881762029531,
                "averageTime": 0.008963754300236446,
                "cpm": 41.95198412698413,
                "cpu": 0.0009589939554731904,
                "endTime": 0,
                "errorRate": 0,
                "mem": 151.37865918322768,
                "metricId": 63656,
                "startTime": 0
            },
            "today": {  // 今天的数据
                "apdexScore": 0.9999654624576915,
                "averageTime": 0.008888333461524588,
                "cpm": 20.106944444444444,
                "cpu": 0.0007365501562195708,
                "endTime": 0,
                "errorRate": 0,
                "mem": 153.44450277036665,
                "metricId": 63656,
                "startTime": 0
            }
        }
    }
]
```
