---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, manage, service

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}
{:tip: .tip}

# サービスのモニターおよび管理
{: #monitoring-and-managing-your-service}

ロード・バランサーのサマリー・ページでサービス名 URL をクリックすることによって、構成を編集したり、サービスのパフォーマンスをモニターしたりできます。

ロード・バランサー・サービス・インスタンスの**完全修飾ドメイン・ネーム (FQDN) アドレス**が、サービス名のすぐ下に表示されます。 エンド・ユーザーはこの FQDN アドレスを介してアプリケーションに接続できます。 ロード・バランサー・サービスのパブリック IP アドレスおよびプライベート IP アドレスは外部に公開されることはなく、FQDN アドレスのみが公開されます。

<img src="images/fqdn-address.png" alt="描画" style="width: 300px;"/>

**「概要」**タブには、サービスの状態情報が概要レベルで示されます。 アプリケーション・サーバーおよびそのポートの現在の正常性が表示されます。 また、システム・パフォーマンスのクイック・サマリーも示されます (スループット、接続レート、同時接続数など)。

システム・パフォーマンスのグラフをリアルタイムで表示するには、**「モニタリング」**タブに移動します。 それらのグラフは、個々のアプリケーション・ポート別に表示したり、さまざまな期間について表示したりできます。

<img src="images/monitor-lb.png" alt="描画" style="width: 300px;"/>

**「プロトコル」**タブ、**「サーバー・インスタンス」**タブ、および**「ヘルス・チェック」**タブに移動することによって、既存の構成を編集することができます。 例えば、「プロトコル」タブに移動すると、追加アプリケーション・ポートを定義したり、SSL 暗号リストをカスタマイズしたりできます。

<img src="images/protocols-monitor.png" alt="描画" style="width: 300px;"/>
