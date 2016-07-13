## 什么是Grafana
 
Grafana 是 Graphite 和 InfluxDB 仪表盘和图形编辑器。Grafana 是开源的，功能齐全的度量仪表盘和图形编辑器，支持 Graphite，InfluxDB 和 OpenTSDB。


### Grafana官网

Granfana官网：http://grafana.org


### Granfana官网安装参考文档

安装文档：http://docs.grafana.org/installation/


### grafana和LDAP集成：

LDAP集成：http://docs.grafana.org/installation/ldap/



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
     
     
     

英文版：

---
page_title: Grafana Installation
page_description: Install guide for Grafana.
page_keywords: grafana, installation, documentation
---

# Installation

Grafana is easily installed via a Debian/Ubuntu package (.deb), via
Redhat/Centos package (.rpm) or manually via a tarball that contains all
required files and binaries. If you can't find a package or binary for
your platform, you might be able to build one yourself. Read the [build
from source](../project/building_from_source) instructions for more
information.

## Platforms
- [Installing on Debian / Ubuntu](debian.md)
- [Installing on RPM-based Linux (CentOS, Fedora, OpenSuse, RedHat)](rpm.md)
- [Installing on Mac OS X](mac.md)
- [Installing on Windows](windows.md)
- [Installing on Docker](docker.md)
- [Installing using Provisioning (Chef, Puppet, Salt, Ansible, etc)](provisioning.md)
- [Nightly Builds](http://grafana.org/download/builds.html)

## Configuration

The back-end web server has a number of configuration options. Go the
[Configuration](/installation/configuration) page for details on all
those options.

## Adding data sources

- [Graphite](../datasources/graphite.md)
- [InfluxDB](../datasources/influxdb.md)
- [OpenTSDB](../datasources/opentsdb.md)



