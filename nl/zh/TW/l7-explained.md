---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 第 7 層負載平衡
{: #layer-7-load-balancing}

「{{site.data.keyword.loadbalancer_full}} 服務」會使用第 7 層（應用程式層）資料，將資料流量分散到多個伺服器實例（包括裸機及虛擬伺服器實例）。

 * 要分散的資料流量會使用原則及規則進行分類。
 * 原則定義在資料流量符合所有與原則相關聯的規則時要採取的動作。
 * 只有 HTTP 及 HTTPS 資料流量才支援第 7 層 (L7) 負載平衡。

## 第 7 層原則及規則
{: #layer-7-policies-and-rules}
第 7 層原則與前端應用程式埠相關聯。多個原則可以與某個前端埠相關聯。

 * 根據指派給每個原則的優先順序，依序評估這些原則。
 * 符合原則時，會採取關聯的動作。
 * 每個 L7 規則都會與一個原則相關聯。
 * 如果所有與原則相關聯的規則都評估為 `true`，則會比對原則，因此採取關聯的動作。

如需其他詳細資料，請參閱 [L7 原則及規則](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy)。

## 第 7 層儲存區
{: #layer-7-pools}
每個第 7 層負載平衡器儲存區都包含一個以上的邏輯伺服器實例。

 * 每部邏輯伺服器實例會以 IP 位址及埠號來識別。
 * 每個儲存區都有相關聯的性能監視器，用來監視儲存區中所有伺服器的性能。
 * 可以配置儲存區的階段作業持續性。
 * 使用用戶端的來源 IP 位址來配置階段作業持續性。

如需其他詳細資料，請參閱 [L7 儲存區](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool)。
