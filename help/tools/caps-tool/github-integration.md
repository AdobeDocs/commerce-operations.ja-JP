---
title: ' [!DNL CAPS]のGitHub統合の設定'
description: GitHubに接続しているAdobe Commerce Cloud プロジェクトのパッチ操作を有効にするために [!DNL Cloud Automation Patching Service (CAPS)] GitHub アプリをインストールする方法について説明します。
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# [!DNL CAPS]のGitHub統合を設定します

Adobe Commerce Cloud プロジェクトがGitHub リポジトリに接続されている場合は、[!DNL Cloud Automation Patching Service] （[!DNL CAPS]）を使用してパッチを適用または元に戻す前に、[!DNL CAPS] GitHub アプリをインストールする必要があります。 このアプリは、リポジトリに変更を加えるために必要なアクセス権を[!DNL CAPS]に付与します。

## 前提条件

* Adobe Commerce Cloudのアクティブなサブスクリプション
* [GitHub統合](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)は既にAdobe Commerce Cloud プロジェクト用に設定されており、[`fetch-branches` オプションが有効になっています](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL CAPS]は一時的な統合環境ブランチを作成およびプッシュするので、このオプションが無効になっている場合、パッチ操作で環境を作成できません。
* [!DNL github.com]でホストされているリポジトリ。 カスタムドメインで設定されたGitHub統合はサポートされていません。
* GitHub組織またはリポジトリへの所有者または管理者アクセス

## [!DNL CAPS] GitHub アプリのインストール

1. [CAPS GitHub アプリのインストール ページ ](https://github.com/apps/adobe-commerce-patching-automation)を開きます。
1. **[!UICONTROL Install]**&#x200B;をクリックします。
1. Adobe Commerce リポジトリを所有するGitHub組織を選択します。
1. **[!UICONTROL Repository access]**&#x200B;で「**[!UICONTROL Only select repositories]**」を選択し、Adobe Commerce プロジェクトのリポジトリを選択します。
1. 「**[!UICONTROL Install]**」をクリックして確定します。

インストールが完了すると、[!DNL CAPS]は自動的にGitHub接続を検出し、すべてのパッチ操作にアプリを使用します。 これ以上の設定は必要ありません。

## [!DNL CAPS] GitHub アプリのアンインストール

[!DNL CAPS]にリポジトリへのアクセスを停止する場合：

1. GitHubで、インストールを所有するアカウントの設定を開きます。
   * **組織所有** リポジトリの場合：**[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * **personal** リポジトリの場合：**[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. `adobe-commerce-patching-automation`を検索して、**[!UICONTROL Configure]**&#x200B;をクリックします。
1. 「**[!UICONTROL Uninstall]**」をクリックして確認します。

>[!WARNING]
>
>GitHub アプリをアンインストールしてもCAPSの適用または復元操作がまだ進行中の場合、これらの操作が失敗する可能性があります。 アプリをアンインストールした後、アクションボタンが非アクティブになるため、ユーザーは新しい操作を開始できません。

## 関連トピック

* [キャップの概要](intro.md)
* [アクセス方法](access.md)
* [ワークフローの概要](workflow.md)
* [ベストプラクティス](best-practices.md)
* [トラブルシューティング](troubleshooting.md)
