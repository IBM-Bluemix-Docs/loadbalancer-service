---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 第 7 層儲存區
{: #layer-7-pool}

第 7 層 (L7) 儲存區是用來處理送入要求之伺服器（成員）的邏輯分組。

第 7 層負載平衡特性可以根據原則及規則，將送入的資料流量導向至不同的後端儲存區。此特性的支援方式是將多個 L7 儲存區與負載平衡器相關聯。第 7 層儲存區是與動作為 `redirect to pool` 的第 7 層原則搭配使用。

L7 儲存區僅支援 HTTP 作為後端通訊協定。

## 階段作業持續性
可以針對每個第 7 層儲存區配置階段作業持續性。如需詳細資料，請參閱  
[進階資料流量](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer)小節。

## 第 7 層成員

與「第 7 層儲存區」相關聯的後端伺服器稱為「第 7 層成員」。

每次指定不同的埠號，即可多次將相同的後端伺服器新增至 L7 儲存區。

## 配置性能檢查
每個第 7 層儲存區的性能檢查定義都是必要的。系統會預先移入 L7 儲存區的預設性能檢查配置。

您可以自訂下列設定，以符合應用程式需求：

 * **間隔**：兩個連續性能檢查嘗試之間的間隔（以秒為單位）。
 * **逾時**：系統將等待性能檢查要求之回應的時間量上限。
 * **最大嘗試次數**：將服務宣告為性能不佳之前，系統將進行的額外性能檢查嘗試次數上限。
 * **URL 路徑**：第 7 層性能檢查的 HTTP URL 路徑。
