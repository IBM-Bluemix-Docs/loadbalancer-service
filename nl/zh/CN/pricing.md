---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: pricing, usage, month

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


# {{site.data.keyword.loadbalancer_full}} 定价
{: #ibm-cloud-load-balancer-pricing}

{{site.data.keyword.loadbalancer_full}} 定价基于以下三个度量值，每月进行计算：

* 服务使用小时数
* 已处理数据
* 出站公共带宽 (Egress)

所有价格因地理区域而异。{{site.data.keyword.loadbalancer_full}} 服务使用的出站公共带宽根据标准数据传输费用 [0.09 美元/GB ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/bandwidth) 进行计费。
{: note}

以下图表详细描述了 {{site.data.keyword.loadbalancer_full}} 对每月使用 4500 GB 公共负载均衡的客户进行定价的示例：

| | 每月| 速率 | 成本|
| ------------- | ------------- | ------------- | ------------- |
| **服务使用情况** | 720 小时|0.025 美元/小时|18 美元/月|
| **已处理数据** | 4500GB | 0.008 美元/GB |36 美元/月|

上述场景的总费用为 54 美元/月，加上标准数据传输费用 [0.09 美元/GB ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/bandwidth)。

![定价](./images/pricing.png)


所有价格因地理区域而异；示例和图中的定价为达拉斯的美元定价；服务使用情况费用 0.025 美元/小时未显示在图中。
{: note}

要查看您所在区域的特定定价信息，可以完成简单的[注册流程 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)。
