---
title: アクセス方法 [!DNL Site-Wide Analysis Tool]
description: アクセス方法 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# アクセス方法 [!DNL Site-Wide Analysis Tool]

次の 2 つの方法で [!DNL Site-Wide Analysis Tool Dashboard].

次にアクセス： [!DNL dashboard] 次のいずれかから [[!DNL Site-Wide Analysis Tool] Web サイト](https://supportinsights.adobe.com/commerce) 直接 **( クラウドインフラストラクチャ上のAdobe Commerceのみ )** Adobe IDにログインするか、 [!DNL dashboard] 店の [!DNL Admin Panel].

この [!DNL Site-Wide Analysis Tool] サービスは、 [実稼動モード](https://docs.magento.com/user-guide/magento/installation-modes.html) 対象 [!DNL Admin] ユーザーにアクセスする権限を持つユーザー [役割リソース](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>オンプレミスでのAdobe Commerceのインストールがある場合は、 [エージェント](../site-wide-analysis-tool/installation.md) ツールを使用するためのインフラストラクチャ上で。

![サイト全体の分析ダッシュボード](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]ダッシュボード*

## オプション 1:へのログイン [!DNL Site-Wide Analysis Tool Dashboard] 直接 [!DNL Site-Wide Analysis Tool] ドメイン ( クラウドインフラストラクチャ上のAdobe Commerceのみ )

An **[!DNL Adobe ID]必須** にアクセスする [!DNL Commerce] アカウント
既に [!DNL Commerce] アカウントを持っていますが、持っていません [!DNL Adobe ID]を使用すると、ログインプロセス中に作成できます。

1. に移動します。 [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. 次をクリック： **[!UICONTROL Sign in with Adobe ID]** ボタンをクリックし、プロンプトに従います。

   ![サイト全体の分析ダッシュボード](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]ログイン画面*

1. 利用条件に同意します。

1. **<u>注意</u>:** お使いのアカウントには、次の権限が付与されています。 **[!DNL Support Permissions]** ～にアクセスするために [!DNL Site-Wide Analysis Tool Dashboard].
詳しくは、 [共有： [!DNL Commerce] アカウント](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) 」を参照してください。

## オプション 2:へのログイン [!DNL Site-Wide Analysis Tool Dashboard] 店の [!DNL Admin Panel]

### 手順 1:権限の検証

を確認します。 [!DNL Admin] ユーザーアカウントには、 [!DNL Site-Wide Analysis Tool] 彼らの [割り当てられたユーザーロール](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>この [!DNL Site-Wide Analysis Tool] ロールリソース（権限）: **not** 自動割り当て済み。 ユーザーの役割と、内の各ユーザーアカウントに個別に割り当てられた役割に対して、有効化する必要があります。 [!UICONTROL Admin].

必要なカスタムロール [!DNL Site-Wide Analysis Tool] にアクセスするには、以下の手順を実行します。

1. を選択します。 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 役割のリソース。

   ![サイト全体の分析ダッシュボード](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]ロール用に選択された権限*

1. クリック **[!UICONTROL Save Role]**.

1. その役割を割り当てられたすべてのユーザーに対して、のサインアウトを通知します [!DNL Admin]をクリックし、もう一度ログインします。

>[!NOTE]
>
>ユーザーアカウントが [!DNL Site-Wide Analysis Tool] ユーザーが [!DNL Admin]を使用すると、クラウドインフラストラクチャ上のAdobe Commerceのインスタンスで HTTP アクセス制御を有効にできます。 この [!DNL Site-Wide Analysis Tool] HTTP Auth が有効になっている場合、ダッシュボードはサポートされません。 この問題の解決方法について詳しくは、 [サポート記事](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### 手順 2:アクセス [!DNL Site-Wide Analysis Tool]

1. の *[!UICONTROL Admin]* サイドバー、移動 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![サイト全体の分析ダッシュボード](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]場所 [!DNL Admin Panel] Adobe Commerce*

1. 詳しくは、 *利用条件* の [!DNL Site-Wide Analysis Tool] をクリックし、 **[!UICONTROL Accept]** をクリックして続行します。

   各ユーザーは、セッションの利用条件に同意する必要があります。 この手順は、ログインしたセッションごとに繰り返されます。


1. ダッシュボードの上部で、表示するタブをクリックします。

   ![サイト全体の分析ダッシュボード](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]情報*

## からレポートを生成 [!DNL Site-Wide Analysis Tool Dashboard]

1. ダッシュボードの右上隅で、 **[!UICONTROL Generate Report]**.

1. 各 **[!UICONTROL Type]** および **[!UICONTROL Priority]** を設定します。

1. クリック **[!UICONTROL Generate Report]**.

   ![サイト全体の分析ダッシュボード](../../assets/tools/swat-report-settings.png)
   *レポート設定*

| TAB | 説明 |
| --- | --- |
| ダッシュボード | 現在の通知と推奨事項を優先してシステムの正常性を表示します。 |
| 情報 | お客様の連絡先情報および現在のチケットの概要と、インストールされている各Adobe Commerce製品の詳細情報を提供します。 |
| Recommendations | サイトで検出された問題に対処するためのベストプラクティスに基づくレコメンデーションのリストを示します。 |
| 例外 | エラーハンドラーを使用しない場合に、異常な状態が原因でアプリケーションがスローしたエラーを一覧表示します。 |
| 拡張機能 | すべてのサードパーティの拡張機能とサードパーティのライブラリを一覧表示します。 |

>[!NOTE]
>
>レコメンデーションを適用した後、で更新されるまで数日かかる場合があります [!DNL Site-Wide Analysis Tool Dashboard] または生成されたレポート。
