---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: basics, load balancing

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# 执行 {{site.data.keyword.loadbalancer_full}} 基本功能
{: #performing-ibm-cloud-load-balancer-basics}

{{site.data.keyword.loadbalancer_full}} 服务在同一个数据中心内本地存在的多个服务器实例（裸机和虚拟服务器）之间分配流量。

## 公用 Load Balancer
{: #public-load-balancer}

对于您的 Load Balancer 服务实例，会分配一个公共可访问的标准域名。您必须使用此域名来访问在 Load Balancer 服务背后托管的应用程序。此域名可注册一个或多个公用 IP 地址。公用 IP 地址和公用 IP 地址数可能会根据维护和缩放活动（对于最终用户是透明的）而随时间改变。托管您应用程序的后端计算实例必须位于 IBM Cloud 专用网络。

作为最佳做法，我们建议您以“仅限专用”的方式供应后端服务器，除非它们需要直接公共连接。此作法可帮助实现更佳的安全性，且可保留您的公共 IP 地址。在这些后端服务器上托管的应用程序仍可使用 Load Balancer 通过公用网络进行访问。
{: note}  

创建 Load Balancer 服务实例时，您可以选择从帐户下的 IBM 系统池（缺省值）或公用 VLAN 分配负载均衡器公共 IP 地址。

## 内部负载均衡器
{: #internal-load-balancer}

内部负载均衡器仅可在 IBM Cloud 专用网络中进行访问。

就像公用负载均衡器一样，内部负载均衡器服务实例也分配有标准域名。但是，此域名注册了一个或多个专用 IP 地址。

与公用负载均衡器类似，专用 IP 地址及其数量可能会根据维护和缩放活动（对于最终用户是透明的）而随时间改变。

托管应用程序的后端计算实例也必须位于 IBM Cloud 专用网络上。
{: note}

## 前端和后端应用程序端口/协议
{: #front-end-and-back-end-application-ports-protocols}

您最多可以定义 10 个前端应用程序端口（协议）并将它们映射到后端应用程序服务器上的各自端口（协议）。分配给您的 Load Balancer 服务实例和前端应用程序端口的标准域名会向外部世界公开。在这些端口上接收入局用户请求。

另一方面，后端端口仅内部知晓。这些后端端口可能与前端端口相同，也可能不同。举例来说，Load Balancer 可能会配置为在前端端口 80 上接收入局 Web/HTTP 流量，而后端服务器则在定制端口 81 上进行侦听。

受支持的前端端口/协议为 HTTP、HTTPS 和 TCP。受支持的后端端口/协议也为 HTTP、HTTPS 和 TCP。必须在 Load Balancer 上终止入局 HTTPS 流量，才能允许与后端服务器进行纯文本 HTTP 通信。如果后端协议为 HTTPS，那么 Load Balancer 与后端服务器之间的流量将会加密。

### 注意事项
{: #considerations}

* 在初始配置期间，您最多仅可以定义两个前端端口。创建 Load Balancer 后，您可以编辑端口配置，以定义附加端口，最多可定义 10 个端口。
* 所有 10 个前端端口必须映射到相同的后端服务器实例集。
* Load Balancer 背后可放置的最大服务器实例数为 50。
* 端口范围 56500 到 56520 保留用于管理目的，不能用作前端虚拟端口。
* TCP 端口 56501 用于管理。如果选择从公用 VLAN 分配 Load Balancer 公共 IP 地址，请确保公用 VLAN 上可能已部署的任何防火墙均未阻止此管理端口以及应用程序端口的流量。如果选择 IBM 系统池选项来分配 Load Balancer 公共 IP 地址则无需如此。

## 负载均衡方法
{: #load-balancing-methods}

以下三种负载均衡方法可用于在后端应用程序服务器之间分配流量：

* **循环法：**循环法是缺省负载均衡方法。使用此方法，Load Balancer 以一种循环的方式，将入局客户机连接转发到后端服务器。因此，所有后端服务器大概会接收到相等数目的客户机连接。

* **加权循环法：**使用此方法，Load Balancer 按分配给后端服务器的权重比例，将入局客户机连接转发到后端服务器。每个服务器分配的缺省权重为 50，可以定制为 0 到 100 之间的任何值。

	举例来说，如果有三个应用程序服务器 A、B 和 C，其权重分别定制为 60、60 和 30，那么服务器 A 和 B 将接收相等数目的连接，而服务器 C 将接收一半数目的连接。


	将服务器权重重置为“0”表示不会将新连接转发到该服务器，但是只要其处于活动状态，任何现有的流量仍会继续向其流动。使用权重“0”可帮助服务器正常关闭，将其从服务轮替中除去。
	{: note}

	服务器权重值仅适用于“加权循环法”。“循环法”和“最少连接数”负载均衡方法不使用权重值。
	{: note}

* **最少连接数：**使用此方法，在给定时间提供最少连接数的服务器实例接收下一个客户机连接。

## 水平伸缩
{: #horizontal-scaling}

Load Balancer 会根据负载自动调整其容量。出现这种情况时，您会看到与 Load Balancer 的 DNS 名称相关联的 IP 地址数发生变化。
