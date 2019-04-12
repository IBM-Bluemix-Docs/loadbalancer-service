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


# IBM Cloud Load Balancer の使用開始
{: #getting-started-with-ibm-cloud-load-balancer}

IBM© Cloud Load Balancer の使用を開始するには、主に次の 2 つの項目が必要です。

* IBM のアカウント: [IBMid ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM サーバー ([ベア・メタル](/docs/bare-metal?topic=bare-metal-about)または[仮想サーバー・インスタンス (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

**IBMid** アカウントの取得について支援が必要な場合は、[IBM 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} にお問い合わせください。

既存の IBM Cloud Infrastructure (SoftLayer) アカウントをお持ちの場合は、IBMid と[アカウントをリンク](/docs/account?topic=account-unifyingaccounts)できます。

## ロード・バランサーを注文する

IBM Cloud Load Balancer サービスを注文するには、[IBM Cloud カタログ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group){:new_window} から**「ネットワーク」>「ロード・バランサー」>「IBM Cloud Load Balancer」**を選択します。 ログインするか新規アカウントを作成してから、以下の手順を実行してください。

1. データ・センターを選択し、サービス・プランを検討します。 **「次へ」**をクリックします。
2. ロード・バランサーをデプロイするサブネットを選択します。 ロード・バランサー・サービス・インスタンスは、このサブネット上にいずれかのネットワーク・インターフェースを持ちます。 アプリケーション・サーバーがこのサブネット上にあるか、またはこのサブネットから到達できることを確認してください。 必要な場合は、VLAN スパンニングを有効にします。 **「次へ」**をクリックします。
3. 名前、説明、フロントエンド・アプリケーションとバックエンド・アプリケーションのプロトコルとポート、およびロード・バランシング方式など、基本的なサービス・パラメーターを定義します。

	初期サービス作成中は、最大 2 つのプロトコルを定義できます。 サービスの作成後は、最大 10 個のプロトコルを定義できます。 さらに、固有のフロントエンド・ポートを使用する必要があります。

	完了したら、**「次へ」**をクリックします。

4. 必要な場合は、ヘルス・チェック・パラメーターを調整してください。そうでない場合、デフォルト設定を使用します。 **「次へ」**をクリックします。
5. ロード・バランサーの後ろにある 1 つ以上のサーバー・インスタンスを関連付けます。 表示されるサーバー・インスタンスは、ご使用のデータ・センターからローカルとなるサーバー・インスタンスのみです。 **「次へ」**をクリックします。
6. サマリー・ページを確認し、**「作成」**をクリックします。

	サマリー・ページには、作成したばかりのロード・バランサー・サービス・インスタンスが表示されます。 **「状況」**フィールドに注目してください。 `「オフライン」`の状況は、ロード・バランサーがサービス中でないことを暗黙に示しています。 状況が`「オンライン」`に変わるまでは、新しい構成を作成したり、ロード・バランシング・サービスを提供したりすることはできません。 現在の状況を表示するには、画面を最新表示する必要がある場合があります。

	このページにあるサービス名をクリックすると、そのサービスの概要ページが表示されます。 **「プロトコル」**タブ、**「ヘルス・チェック」**タブ、および**「サーバー・インスタンス」**タブにナビゲートして、構成をさらに編集することができます。

ステップバイステップの構成手順については、[柔軟なサーバー・ロード・バランシングのための IBM Cloud Load Balancer の作成および使用法](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)を参照してください。
