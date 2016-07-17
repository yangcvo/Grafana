## 什么是Grafana
 
Grafana 是 Graphite 和 InfluxDB 仪表盘和图形编辑器。Grafana 是开源的，功能齐全的度量仪表盘和图形编辑器，支持 Graphite，InfluxDB 和 OpenTSDB。


### Grafana官网

Granfana官网：http://grafana.org


### Granfana官网安装参考文档

安装文档：http://docs.grafana.org/installation/


### grafana和LDAP集成：

LDAP集成：http://docs.grafana.org/installation/ldap/


### zabbix+Grafana 结合监控与使用安装使用文档：

[ zabbix+Grafana 结合监控与使用](http://blog.yangcvo.me/2016/07/13/zabbix-Grafana安装使用结合/)

Grafana 主要特性：灵活丰富的图形化选项；可以混合多种风格；支持白天和夜间模式；多个数据源；Graphite 和 InfluxDB 查询编辑器等等。

###Graphite 指标编辑器

* Graphite 指标表达解析器
* 功能齐全的查询功能
* 快速添加和编辑函数和参数
* 模板化查询
* See it in action

##图形化

* 快速渲染，甚至是较大的时间跨度
* 点击和拖拽缩放
* 多个 Y 轴 
* 条形，折线，点 
* 智能 Y 轴格式化
* 系列切换和颜色选择 
* Legend values 和格式化选项
* 网格阈值，轴标签
* Annotations

###仪表盘

* 创建，编辑，保存和搜索仪表盘
* 修改列宽和行高
* 拖拽面板重新编排
* 使用 InfluxDB 或者 Elasticsearch 作为仪表盘存储
* 导入和导出仪表盘（JSON 文件）
* 从 Graphite 导入仪表盘

###模板

* Scripted dashboards
* Dashboard playlists
* 时间范围控制

###InfluxDB

* 使用 InfluxDB 作为指标数据源，注释源和仪表盘存储
* 查询编辑器
* OpenTSDB



### 温馨提示：

     grafana的版本和grafana-zabbix的版本必须匹配，否则会出现异常。
     本文以grafana2.5版本为例讲解，如果后面grafana和grafana-zabbix更新，需要将2个版本匹配即可。
     
     
     

## 入门Grafana-zabbix 


``` bash
点击Add添加
我们现在需要以下的监控项：
group代表所有Zabbix监控模板，
host代表zabbix的监控主机，
application代表主机下的监控类型，
items代表监控类型下的监控项。
如果只用上面这几种监控选择，要么仪表中需要显示一个监控类型下的某几个监控项，将需要的监控项合成一个新的监控。下面显示的是已经添加好的监控，这里只上传添加的内容，具体的步骤按内容写就可以。
注意：参数中，“*”的意思就是全匹配，比如MySQL.*就是MySQL下所有的监控项。  
```


你经过安装和配置 Grafana-的zabbix数据源，让我们创建一个简单的仪表板。

### 简单图

新图面板添加到仪表板。从下拉菜单中选择指标或开始键入筛选结果


![](http://docs.grafana-zabbix.org/img/getstarting-metrics_filtering.png)


让我们创建15分钟，平均处理器负载图形。选择主机组，主机，应用程序（可选-你可以留空）和项目。


![](http://docs.grafana-zabbix.org/img/getstarting-processor_load.png)


多个项目在一个图

您可以使用很多度量字段内正则表达式项目建设图。Grafana使用JavaScript正则表达式的实现。例如，如果你需要显示的CPU时间（用户，系统，IOWAIT等），你可以使用这个表达式在项目现场创建图表：


```
/CPU (?!idle).* time/
```
![](http://docs.grafana-zabbix.org/img/getstarting-regex_cpu_time.png)


使用正则表达式另一种情况是在比较了不同主机的相同指标。使用`/.*/`的正则表达式显示所有指标或写自己的过滤器。例如，我想显示CPU系统时间为哪个名字开始与所有主机后端的所有主机组。我用`/.*/`为Group`/ ^backend/`用于主机和CPU system time的项目。


![](http://docs.grafana-zabbix.org/img/getstarting-regex_backend_system_time.png)


### 条图


让我们创建一个显示MySQL数据库的查询统计的图表。选择组，主机，应用程序（MySQL的在我的情况）和项目。我用`/MySQL .* operations/`正则表达式来过滤不同类型的操作。


![](http://docs.grafana-zabbix.org/img/getstarting-mysql_operations_1.png)

要显示图形为条形图，转到显示选项卡，取消选中线并设置Bars。此外，启用堆栈复选框显示堆叠条形。


![](http://docs.grafana-zabbix.org/img/getstarting-mysql_operations_2.png)

但是，因为它包含了太多的Bars这个图看起来并不好。我们可以通过修复它最大的数据点的参数。进入度量选项卡并设置最大数据点到50为例。

![](http://docs.grafana-zabbix.org/img/getstarting-mysql_operations_3.png)

好了。

###Singlestat和仪表

有时你可能需要出示只为特定指标一个大单值。使用Grafana的Singlestat面板在这种情况下。让我们创建面板，显示CPU用户时间指标。

![](http://docs.grafana-zabbix.org/img/getstarting-singlestat_1.png)


假设你要设置单位百分比，并显示仪表该值。进入选项卡，并设置单位百分比（0-100） 。然后，使显示的选项计和（在本例0-100）为度量标准设置的最小值和最大值。设置阈值，如果你想看到它在计（`50,80`为例）。

![](http://docs.grafana-zabbix.org/img/getstarting-singlestat_2.png)

太好了，看起来很酷。了解更多关于Singlestat面板[Grafana文档](http://docs.grafana.org/reference/singlestat/)。


![](http://docs.grafana-zabbix.org/img/getstarting-dashboard_1.png)


![](https://cloud.githubusercontent.com/assets/4932851/8288883/9ec5b240-1921-11e5-9e0f-04d075b885e9.gif)
