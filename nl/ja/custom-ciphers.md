---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: cipher, suite, https

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

# HTTPS アプリケーション用の優先暗号スイートの選択
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

暗号アルゴリズムは、IBM© Cloud Load Balancer が HTTP クライアントとのセキュア接続を形成するのを支援します。

IBM によって提供されている承認済みの暗号スイートの中からいずれかを選択して、ロード・バランサーとクライアントの間の通信を保護できます。

既存のロード・バランサー用に優先暗号スイートを選択するか、新しくロード・バランサーを作成するときに指定することができます。

## 既存のロード・バランサー用の暗号の選択
{: #choosing-ciphers-for-an-existing-load-balancer}

既存のロード・バランサー用の暗号スイート構成を選択するには、カスタマー・ポータルのロード・バランサー画面にナビゲートし、「プロトコル」タブをクリックします。 フロントエンド・プロトコルとして HTTPS が選択されていない場合は、暗号スイートのリストは表示されません。

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="描画" style="width: 700px;"/>

フロントエンド・プロトコルに HTTPS を選択してください。そうすると、使用可能な暗号スイートがロード・バランサーの詳細の下に表示されます。

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="描画" style="width: 600px;"/>

暗号テーブルは編集可能であり、SSL ハンドシェークに使用したい暗号スイートを選択することができます。 **「編集」**をクリックし、実装したい暗号を選択してから**「保存」**をクリックします。

サポートされている暗号のリストを確認するには、[SSL オフロード](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)を参照してください。
{: note}

## 新規ロード・バランサー作成時の暗号の選択
{: #choosing-ciphers-when-creating-a-new-load-balancer}

新規ロード・バランサーを作成するときに暗号スイートを選択するには、次のようにします。

1. [ロード・バランサーの作成](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer)の手順に従います。

2. 暗号スイート構成は、フロントエンド・プロトコルが HTTPS の場合にのみ適用可能です。 **「プロトコルの追加 (Add protocol)」**セクションの構成ステップに到達したら、**「HTTPS プロトコル」**を選択してください。

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="描画" style="width: 500px;"/>

3. 構成では暗号のデフォルト・セットが既に選択されていますが、ロード・バランサーの構成を完了した後でないと、それらを編集することはできません。

	トピックに記述されている手順に従って、ロード・バランサー構成を完了してください。 完了したら、**「プロトコル」**タブの**「ロード・バランサーの詳細」**の下にデフォルト暗号リストが表示されます。

	<img src="images/View-CustomCiphers.png" alt="描画" style="width: 600px;"/>

4. 暗号テーブルは編集可能であり、SSL ハンドシェークに使用したい暗号スイートを選択することができます。 **「編集」**をクリックし、実装したい暗号を選択してから**「保存」**をクリックします。

	サポートされている暗号のリストを確認するには、[SSL オフロード](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)を参照してください。
  {: note}
