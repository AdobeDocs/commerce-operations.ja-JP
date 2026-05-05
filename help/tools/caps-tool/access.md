---
title: ' [!DNL Cloud Automation Patching Service (CAPS)]へのアクセス方法'
description: ' [!DNL Cloud Automation Patching Service (CAPS)]へのアクセス方法と使用方法を説明します'
hide: true
hidefromtoc: true
source-git-commit: f6f690af56df3de737a9f72c2e727b1752bc94b3
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# [!DNL Cloud Automation Patching Service (CAPS)]へのアクセス方法

## 前提条件

[!DNL CAPS]は、Adobe Commerce Cloudの役割ベースのアクセス制御を使用します。 Cloud Consoleのアクセス レベルによって、[!DNL CAPS]で実行できる処理が決まります。

### [!DNL CAPS]を使用できるユーザー

* **プロジェクト管理者** – すべての環境でパッチを適用または元に戻すことができます
* **Contributor** – 割り当てられた環境にパッチを適用または元に戻すことができます
* **Viewer** - プロジェクトと環境のみを表示できます。アクションは許可されていません

### プロジェクトへのアクセスをリクエストする方法

[!DNL CAPS] ユーザーインターフェイスにプロジェクトが表示されない場合は、適切なユーザーにアクセス権をリクエストする必要があります。

* プロジェクトのアカウントオーナーまたはプロジェクト管理者に連絡する
* Cloud Consoleを通じて適切な役割が付与されます
* アクセスを許可したら、Cloud Consoleにログインして[!DNL CAPS]を使用できます

>[!NOTE]
>
>[!DNL CAPS]はAdobe Commerce Cloudと同じ権限モデルに従うため、Cloud Consoleのアクセスレベルによって[!DNL CAPS]で何ができるかが決まります。

## [!DNL CAPS]へのアクセス

CAPS ツールは、[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)のサイト全体の分析ツール ダッシュボードから使用できます。 「パッチの自動処理」タブで、プロジェクトと環境を選択できます。

1. [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)のサイト全体の分析ツールに移動します。
1. インターフェイスの「[!UICONTROL Patching Automation]」タブをクリックします。
1. パッチを適用するプロジェクトと環境を選択します。
1. 利用可能なパッチとその互換性ステータスを確認します。
1. 適用または元に戻すパッチを選択します。

## 本番環境へのアクセス

実稼動環境には、追加のセーフガードが適用されます。

* **メンテナンスモード** – 有効にする必要があります
* **Cron ジョブ** – 無効にする必要があります
* **確認ダイアログ** – 続行する前に完了する必要があります

>[!IMPORTANT]
>
>実稼動環境のパッチを適用するには、誤って中断を防ぐために適切な準備と保護対策が必要です。

## 関連トピック

* [キャップの概要](intro.md)
* [ワークフロー](workflow.md)
* [ベストプラクティス](best-practices.md)
* [トラブルシューティング](troubleshooting.md)
