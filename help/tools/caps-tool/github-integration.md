---
title: ' [!DNL Adobe Commerce Patching Automation]のGitHub統合の設定'
description: GitHubに接続しているAdobe Commerce Cloud プロジェクトのパッチ操作を有効にするために [!DNL Adobe Commerce Patching Automation] GitHub アプリをインストールする方法について説明します。
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# [!DNL Patching Automation]のGitHub統合を設定します

Adobe Commerce Cloud プロジェクトがGitHub リポジトリに接続されている場合は、サービスを使用してパッチを適用または元に戻す前に、[!DNL Patching Automation] GitHub アプリをインストールする必要があります。 アプリは、リポジトリに変更を加えるために必要なアクセス権をサービスに付与します。

## 前提条件

* Adobe Commerce Cloudのアクティブなサブスクリプション
* [GitHub統合](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)は既にAdobe Commerce Cloud プロジェクト用に設定されており、[`fetch-branches` オプションが有効になっています](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL Patching Automation]は一時的な統合環境ブランチを作成およびプッシュするので、このオプションが無効になっている場合、パッチ操作で環境を作成できません。
* [!DNL github.com]でホストされているリポジトリ。 カスタムドメインで設定されたGitHub統合はサポートされていません。
* GitHub組織またはリポジトリへの所有者または管理者アクセス

## [!DNL Patching Automation] GitHub アプリのインストール

UIの&#x200B;**[!UICONTROL Install GitHub App]**&#x200B;をクリックしてインストールページに移動するか、インストールページに直接移動することで、[!DNL Patching Automation]からインストールを開始できます。

1. [自動処理GitHub アプリのインストール ページ ](https://github.com/apps/adobe-commerce-patching-automation)を開きます。
1. **[!UICONTROL Install]**&#x200B;をクリックします。
1. Adobe Commerce リポジトリを所有するGitHub組織を選択します。
1. **[!UICONTROL Repository access]**&#x200B;で「**[!UICONTROL Only select repositories]**」を選択し、Adobe Commerce プロジェクトのリポジトリを選択します。
1. 「**[!UICONTROL Install]**」をクリックして確定します。

インストールすると、サービスは自動的にGitHub接続を検出し、すべてのパッチ操作にアプリを使用します。 これ以上の設定は必要ありません。

## 接続ステータスの確認と管理

[!DNL Patching Automation] UIには、GitHub接続の現在のステータスが表示され、そのステータスに応じてアクションを利用できます。

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** – 変更を加えずに接続ステータスを再確認します。
* **[!UICONTROL Reinstall]** - インストールが無効になった場合（例えば、インストールが中断された場合、またはCloud プロジェクトに接続されているリポジトリが変更された場合）に表示されます。 上記と同じインストールフローを開始します。
* **[!UICONTROL Unlink GitHub App]** - [!DNL Patching Automation]の保存されたGitHub アプリへの接続を削除します。 これにより、**not**&#x200B;はGitHub リポジトリからアプリをアンインストールします。アクセスを完全に削除するには、以下の「アンインストール」セクションを参照してください。

## [!DNL Patching Automation] GitHub アプリのアンインストール

サービスにリポジトリにアクセスする必要がなくなった場合：

1. GitHubで、インストールを所有するアカウントの設定を開きます。
   * **組織所有** リポジトリの場合：**[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * **personal** リポジトリの場合：**[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. `adobe-commerce-patching-automation`を検索して、**[!UICONTROL Configure]**&#x200B;をクリックします。
1. 「**[!UICONTROL Uninstall]**」をクリックして確認します。

>[!WARNING]
>
>GitHub アプリをアンインストールしても「適用」または「元に戻す」操作が進行中の場合、その操作が失敗する可能性があります。 アプリをアンインストールした後、アクションボタンが非アクティブになるため、ユーザーは新しい操作を開始できません。

## 関連トピック

* [パッチ自動処理の概要](intro.md)
* [アクセス方法](access.md)
* [ワークフローの概要](workflow.md)
* [ベストプラクティス](best-practices.md)
* [トラブルシューティング](troubleshooting.md)
