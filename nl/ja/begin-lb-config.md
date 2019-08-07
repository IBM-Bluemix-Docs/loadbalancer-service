---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: parameters, load balancing, configure, protocol, health check

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

# {{site.data.keyword.loadbalancer_full}} パラメーターの構成
{: #configuring-ibm-cloud-load-balancer-parameters}

[ロード・バランサーの作成](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)後、柔軟なロード・バランシングのために構成することができます。構成するには、以下の手順に従ってください。

1. ロード・バランサーに名前を付け、説明を追加します (説明はオプションです)。

	<img src="images/lb-config-basic.png" alt="描画" style="width: 300px;"/>

2. アプリケーションが listen を行うポートおよびプロトコルを特定して、アプリケーション・プロファイルの詳細を入力します。 フロントエンドとバックエンドの両方に同じ構成を使用することも、異なるフロントエンド・ポートを公開することも (例えばセキュリティー上の目的のために) できます。

3. デフォルトのロード・バランシング方式は**ラウンドロビン**です。 アプリケーションのニーズに応じて、ドロップダウン・リストから「**重みづけしたラウンドロビン**」または「**最小接続**」に変更することができます。

4. オプションで、**スティッキー・セッション**を有効にすることができます。 有効になっていると、ある特定のエンド・ユーザーからのすべての要求 (例えば、同じソース IP のもの) は、システムで定義された「スティッキー」な時間の間は、同じバックエンド・サーバーに向かいます。

5. アプリケーションに対して**最大接続制限**を設定することもできます。

6. アプリケーションが listen を行うことのできる追加ポートおよびプロトコルを指定するには、**「プロトコルの追加」**をクリックします。 すべてのフロントエンド・ポートが固有であるように注意してください。 フロントエンド・プロトコルとして、HTTP、HTTPS、または TCP を選択できます。

	<img src="images/lb-add-protocol.png" alt="描画" style="width: 300px;"/>

	最大 2 ポートを初期構成時に定義できます。 サービス・インスタンス作成後にポートを追加できます。 許容される最大ポート数について詳しくは、[ポート数の制限](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-)に関する個所を参照してください。
{:note:}

7. {{site.data.keyword.loadbalancer_full}} は、着信 HTTPS (HTTP over SSL) 接続を終了し、プレーン・テキスト HTTP でバックエンド・アプリケーション・サーバーと通信できるので、バックエンド・プロトコルに HTTP が選択されている場合にはプロセッサー集約的な SSL タスクによるサーバーへの負荷を軽減します。 選択されているバックエンド・プロトコルが HTTPS の場合、トラフィックはロード・バランサーとバックエンド・サーバーの間で暗号化されます。 SSL 証明書をアップロードする必要があります。 ドロップダウン・リストから、使用可能な証明書のうちの 1 つを選択してください。  

	<img src="images/lb-ssl-cert.png" alt="描画" style="width: 300px;"/>

	既存の証明書がない場合は、**「新規証明書の追加 (Add a new Certificate)」**をクリックしてください。 そうすると、IBM Cloud 証明書サービスで、新規証明書を購入するか、既存の証明書をアップロードすることができます。

	証明書を追加した後、ロード・バランサーの構成ページに戻り、「SSL 証明書」ドロップダウン・リストの下にある最新表示アイコンをクリックして、新しくアップロードした証明書を表示および追加します。

	<img src="images/order-ssl-cert.png" alt="描画" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="描画" style="width: 300px;"/>

	HTTPS リスナーと関連付けられた証明書は決して削除しないでください。削除すると機能の問題が発生することがあります。{: note}

8. **「次へ」**をクリックします。

## ヘルス・チェックの構成
{: #configure-health-checks}

各アプリケーション・ポートにヘルス・チェック定義が必須です。 それらのポートは、前の基本構成メニューで識別されたバックエンド・ポートです。

<img src="images/config-health-check.png" alt="描画" style="width: 300px;"/>

これらのバックエンド・ポート用のデフォルトのヘルス・チェック構成はシステムによって事前設定されます。 アプリケーションのニーズに合うように以下の設定をカスタマイズできます。

* **間隔 (Interval)**: 2 つの連続するヘルス・チェック試行の間隔 (秒単位)
* **タイムアウト (Timeout)**: ヘルス・チェック要求に対してシステムが応答を待機する最大時間
* **最大試行回数 (MaxRetries)**: ポートが正常でないと宣言する前にシステムが行う追加のヘルス・チェック試行の最大回数
* **パス**: ヘルス・チェックの HTTP URL パス     

**「次へ」**をクリックして選択を有効にします。

## 次に行うこと
{: #what-s-next}

起点プールやヘルス・チェック・メカニズムなど、[アプリケーションのリソースを識別](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources)します。
