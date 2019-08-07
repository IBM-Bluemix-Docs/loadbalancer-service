---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, metrics, throughput, connection

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# 使用 {{site.data.keyword.loadbalancer_full}} 监视度量值
{: #monitoring-metrics-with-ibm-cloud-load-balancer}

负载均衡器监视以下度量值：

* 吞吐量
* 活动连接数
* 连接速率

这些度量值将可视化为图形，可通过选择**监视**选项卡进行查看，并可使用 `getListenerTimeSeriesData` API 以编程方式提供这些度量值作为时间序列数据点。

每个数据点包含 UNIX 戳记时间格式的时间戳记，以及在该时间戳记结束的那个时间间隔的度量值。用户可以指定要报告度量值的协议和时间间隔。

支持的协议包括：

* HTTP
* HTTPS
* TCP

如果指定协议，将按该协议过滤度量值。

例如，如果未指定协议，并且度量值为*吞吐量*，那么将报告所有协议的总吞吐量。

如果协议为 *HTTP*，那么仅报告 HTTP 流量的吞吐量。

用户还可以指定要报告度量值的时间间隔。支持的时间间隔有：

* 1 小时
* 6 小时
* 12 小时
* 24 小时
* 1 周
* 2 周

针对每个时间间隔报告的数据点的数量大致相同。  
例如，如果时间间隔为 1 小时，那么每个数据点表示 5 分钟的数据。

如果时间间隔为 2 周，那么每个数据点表示 24 小时的数据。

下表显示如何从时间间隔派生数据点：

|时间间隔 | 数据点精度 |数据点数量|                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
|1 小时|5 分钟 | 12   |
|6 小时|30 分钟 | 12  |
|12 小时|1 小时| 12 |
|24 小时| 2 小时| 12 |
| 1 周| 12 小时| 12 |
| 2 周| 24 小时| 12 |

## 如何启用度量值监视
{: #how-to-enable-metrics-monitoring}

为了检索监视度量值，您必须将 SoftLayer 帐户与 IBM© Cloud 帐户链接起来。请参阅[本主题](/docs/account?topic=account-unifyingaccounts#link_accounts)以获取更多信息。
