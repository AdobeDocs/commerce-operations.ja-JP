---
title: ' [!DNL Adobe Commerce Patching Automation]へのアクセス方法'
description: ' [!DNL Adobe Commerce Patching Automation]へのアクセス方法と使用方法を説明します'
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# [!DNL Adobe Commerce Patching Automation]へのアクセス方法

## 前提条件

[!DNL Patching Automation]は、Adobe Commerce Cloudの役割ベースのアクセス制御を使用します。 Cloud Consoleのアクセスレベルによって、サービスで何ができるかが決まります。

### [!DNL Patching Automation]を使用できるユーザー

* **プロジェクト管理者** – すべての環境でパッチを適用または元に戻すことができます
* **Contributor** – 割り当てられた環境にパッチを適用または元に戻すことができます
* **Viewer** - プロジェクトと環境のみを表示できます。アクションは許可されていません

### プロジェクトへのアクセスをリクエストする方法

[!DNL Patching Automation] ユーザーインターフェイスにプロジェクトが表示されない場合は、適切なユーザーにアクセスをリクエストしてください。

* プロジェクトのアカウントオーナーまたはプロジェクト管理者に連絡する
* Cloud Consoleを通じて適切な役割が付与されます
* アクセスを許可したら、Cloud Consoleにログインしてサービスを使用できます

>[!NOTE]
>
>[!DNL Patching Automation]はAdobe Commerce Cloudと同じ権限モデルに従うため、Cloud Consoleのアクセスレベルによってサービスで何ができるかが決まります。

## [!DNL Patching Automation]へのアクセス

[!DNL Patching Automation]は、[!DNL Site-Wide Analysis Tool] ダッシュボード内のタブとして利用できます。 管理者パネルからアクセスするには、管理者サイドバーの&#x200B;**レポート** > **システムインサイト** > **サイト全体の分析ツール**&#x200B;に移動します。 前提条件と権限の設定については、[&#x200B; サイト全体の分析ツールにアクセスする方法](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access)を参照してください。

ダッシュボードにアクセスすると、次のことが可能になります。

1. インターフェイスの「[!UICONTROL Patching Automation]」タブをクリックします。
1. パッチを適用するプロジェクトと環境を選択します。
1. 利用可能なパッチとその互換性ステータスを確認します。
1. 適用または元に戻すパッチを選択します。

## 本番環境へのアクセス

実稼動環境の場合、追加のセーフガードがデフォルトで適用されます。

* **メンテナンスモード** – 有効にする必要があります
* **Cron ジョブ** – 無効にする必要があります
* **確認ダイアログ** – 続行する前に完了する必要があります

>[!IMPORTANT]
>
>実稼動環境のパッチを適用するには、誤って中断を防ぐために適切な準備と保護対策が必要です。

>[!NOTE]
>
>UI （*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*）で「上書き」チェックボックスを選択すると、メンテナンスモードとcron ジョブのチェックをスキップできます。 これらの保護措置を講じずに本番環境にパッチを適用するリスクを把握した場合にのみ、これを使用してください。

## 関連トピック

* [パッチ自動処理の概要](intro.md)
* [ワークフローの概要](workflow.md)
* [GitHubとの統合](github-integration.md)
* [ベストプラクティス](best-practices.md)
* [トラブルシューティング](troubleshooting.md)
