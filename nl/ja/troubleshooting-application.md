---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, problem, server, application

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

# アプリケーション・サーバーのトラブルシューティング
{: #application-server-troubleshooting}

このトピックでは、ロード・バランサーの使用時に発生する可能性のある一般的な問題について説明します。

## バックエンド・サーバーが正常でない
{: #the-back-end-server-is-unhealthy}
バックエンド・サーバーの正常性が損なわれている場合、以下のリストを検証し、障害の修正を試みてください。

* 構成されたバックエンド・プロトコルのポートは、アプリケーションが listen を行っているポートと一致していますか?
* 構成されたヘルス・チェックには、プロトコル (TCP または HTTP)、ポート、および URL (HTTP の場合) についての正しい情報がありますか? HTTP の場合、構成されたヘルス・チェック URL に対してアプリケーションが `200 OK` で応答することを確認してください。
* バックエンド・サーバーはロード・バランサーとは異なるサブネットにありますか? そうでない場合は、VLAN スパンニングが有効にされていることを確認してください。
* バックエンド・サーバーは、セキュリティー・グループが有効にされている仮想サーバーですか? そうである場合、セキュリティー・グループ・ルールが、ロード・バランサーと仮想サーバーとの間のトラフィックを許可していることを確認してください。
