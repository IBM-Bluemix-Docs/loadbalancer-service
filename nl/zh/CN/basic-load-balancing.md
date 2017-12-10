---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 基本负载均衡
IBM Bluemix Load Balancer 服务在同一个数据中心内本地存在的多个服务器实例（裸机和虚拟服务器）之间分配流量。 

## 公用 Load Balancer 
对于您的 Load Balancer 服务实例，会分配一个公共可访问的标准域名。您可以使用此域名来访问在 Load Balancer 服务背后托管的应用程序。托管您应用程序的后端计算实例必须位于 IBM Cloud 专用网络。 

**注：**作为最佳作法，我们建议您以“仅限专用”来供应后端服务器，除非它们需要直接公共连通性。此作法可帮助实现更佳的安全性，且可保留您的公共 IP 地址。在这些后端服务器上托管的应用程序仍可使用 Load Balancer 通过公用网络进行访问。  

## 前端和后端应用程序端口/协议
您最多可以定义 10 个前端应用程序端口（协议）并将它们映射到后端应用程序服务器上的各自端口（协议）。分配给您的 Load Balancer 服务实例和前端应用程序端口的标准域名会向外部世界公开。在这些端口上接收入局用户请求。 

另一方面，后端端口仅内部知晓。这些后端端口可能与前端端口相同，也可能不同。举例来说，Load Balancer 可能会配置为在前端端口 80 上接收入局 Web/HTTP 流量，而后端服务器则在定制端口 81 上进行侦听。 

受支持的前端端口/协议为 HTTP、HTTPS 和 TCP。受支持的后端端口/协议为 HTTP 和 TCP。必须在 Load Balancer 上终止入局 HTTPS 流量，才能允许与后端服务器进行纯文本 HTTP 通信。 

**注：**

* 在初始配置期间，您最多仅可以定义两个前端端口。创建 Load Balancer 后，您可以编辑端口配置，以定义附加端口，最多可定义 10 个端口。
* 所有 10 个前端端口必须映射到相同的后端服务器实例集。
* Load Balancer 背后可放置的最大服务器实例数为 50。
* 端口范围 56500 到 56520 保留用于管理目的，不能用作前端虚拟端口。 

## 负载均衡方法
以下三种负载均衡方法可用于在后端应用程序服务器之间分配流量：

* **循环法：**循环法是缺省负载均衡方法。使用此方法，Load Balancer 以一种循环的方式，将入局客户机连接转发到后端服务器。因此，所有后端服务器大概会接收到相等数目的客户机连接。

* **加权循环法：**使用此方法，Load Balancer 按分配给后端服务器的权重比例，将入局客户机连接转发到后端服务器。每个服务器分配的缺省权重为 50，可以定制为 0 到 100 之间的任何值。 

	举例来说，如果有三个应用程序服务器 A、B 和 C，其权重分别定制为 60、60 和 30，那么服务器 A 和 B 将接收相等数目的连接，而服务器 C 将接收一半数目的连接。 

	**注：** 

	* 将服务器权重重置为“0”表示不会将新连接转发到该服务器，但是只要其处于活动状态，任何现有的流量仍会继续向其流动。使用权重“0”可帮助服务器正常关闭，将其从服务轮替中除去。 
	* 服务器权重值仅适用于“加权循环法”。“循环法”和“最少连接数”负载均衡方法不使用权重值。 

* **最少连接数：**使用此方法，在给定时间提供最少连接数的服务器实例接收下一个客户机连接。 