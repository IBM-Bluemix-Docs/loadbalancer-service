---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 第 7 层负载均衡
{: #layer-7-load-balancing}

IBM© Cloud Load Balancer 服务使用第 7 层（应用程序层）数据在多个服务器实例（包括裸机服务器实例和虚拟服务器实例）之间分配流量。 

 * 要分配的数据流量使用策略和规则进行分类。 
 * 策略定义数据流量与某个策略的所有关联规则匹配时要执行的操作。
 * 仅 HTTP 和 HTTPS 流量支持第 7 层 (L7) 负载均衡。

## 第 7 层策略和规则 
第 7 层策略与前端应用程序端口相关联。多个策略可以与一个前端端口相关联。 

 * 这些策略将根据为每个策略指定的优先级按顺序求值。 
 * 与策略匹配时，将执行关联的操作。
 * 每个 L7 规则都与一个策略相关联。 
 * 如果与该策略关联的所有规则均求值为 `true`，说明与该策略匹配，因此会执行关联的操作。

请参阅 [L7 策略和规则](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy)获取更多详细信息。

## 第 7 层池
每个第 7 层负载均衡器池都包含一个或多个逻辑服务器实例。 

 * 每个逻辑服务器实例通过 IP 地址和端口号进行标识。 
 * 每个池都有一个与其关联的运行状况监视器，用于监视池中所有服务器的运行状况。
 * 可以将池配置用于会话持久性。 
 * 使用客户机的源 IP 地址来配置会话持久性。

请参阅 [L7 池](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool)获取更多详细信息。
