---
title: アクセス方法 [!DNL Site-Wide Analysis Tool]
description: にアクセスする方法を説明します [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# へのアクセス方法 [!DNL Site-Wide Analysis Tool]

にアクセスする方法は 2 つあります [!DNL Site-Wide Analysis Tool Dashboard].

にアクセスできます [!DNL dashboard] 次のいずれかから： [[!DNL Site-Wide Analysis Tool] Web サイト](https://supportinsights.adobe.com/commerce) 直接 **（クラウドインフラストラクチャー上のAdobe Commerceのみ）** Adobe IDでログインするか、 [!DNL dashboard] ストアから [!DNL Admin Panel].

この [!DNL Site-Wide Analysis Tool] サービスは次の場所で利用できます [実稼動モード](https://docs.magento.com/user-guide/magento/installation-modes.html) （用） [!DNL Admin] ユーザーにアクセスする権限を持つユーザー [役割リソース](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Adobe Commerceのオンプレミスインストールがある場合は、 [代理人](../site-wide-analysis-tool/installation.md) インフラストラクチャでツールを使用します。

![Site-Wide Analysis Dashboard](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## オプション 1：にログインする [!DNL Site-Wide Analysis Tool Dashboard] から直接 [!DNL Site-Wide Analysis Tool] ドメイン （クラウドインフラストラクチャー上のAdobe Commerceのみ）

An **[!DNL Adobe ID]は必須です** にアクセスするには [!DNL Commerce] アカウント。
既にがある場合 [!DNL Commerce] アカウントですが、がありません [!DNL Adobe ID]の場合は、ログインプロセス中に作成できます。

1. に移動 [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. 「」をクリックします **[!UICONTROL Sign in with Adobe ID]** ボタンをクリックし、プロンプトに従います。

   ![Site-Wide Analysis Dashboard](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]ログイン画面*

1. 条件に同意します。

1. **<u>注意</u>:** アカウントには次の権限が付与されています **[!DNL Support Permissions]** アクセスするために [!DNL Site-Wide Analysis Tool Dashboard].
詳しくは、を参照してください。 [を共有 [!DNL Commerce] アカウント](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) を参照してください。

## オプション 2：にログインする [!DNL Site-Wide Analysis Tool Dashboard] ストアから [!DNL Admin Panel]

### 手順 1：権限の確認

を確認します [!DNL Admin] ユーザーアカウントには、にアクセスするための権限があります [!DNL Site-Wide Analysis Tool] ユーザーを通して [割り当てられたユーザーロール](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>この [!DNL Site-Wide Analysis Tool] 役割リソース （権限） : **ではない** が自動で割り当てられました。 の各ユーザーアカウントでユーザーの役割と個別に割り当てられた役割に対してアクティブ化する必要があります。 [!UICONTROL Admin].

必要なカスタムの役割に対応 [!DNL Site-Wide Analysis Tool] アクセス、次の操作を行います。

1. 「」を選択します **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 役割リソース。

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]役割に対して選択された権限*

1. クリック **[!UICONTROL Save Role]**.

1. その役割を割り当てられたユーザーが以下からサインアウトするように通知します [!DNL Admin]再度ログインします。

>[!NOTE]
>
>ユーザーアカウントが以下にアクセスする権限を持っていることを確認した場合： [!DNL Site-Wide Analysis Tool] からツールにアクセスしようとすると、ユーザーに 403 エラーが発生する。 [!DNL Admin]を設定する場合、クラウドインフラストラクチャー上のAdobe Commerceのインスタンスで HTTP アクセス制御を有効にすることができます。 この [!DNL Site-Wide Analysis Tool] HTTP Auth が有効になっている場合、ダッシュボードはサポートされません。 この問題の解決について詳しくは、 [サポート記事](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### 手順 2：アクセス [!DNL Site-Wide Analysis Tool]

1. 日 *[!UICONTROL Admin]* サイドバー、に移動 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Site-Wide Analysis Dashboard](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]内の場所 [!DNL Admin Panel] Adobe Commerce内*

1. を読み取る *Terms of Use* の場合 [!DNL Site-Wide Analysis Tool] をクリックして、 **[!UICONTROL Accept]** 続行します。

   各ユーザーは、セッションの利用条件に同意する必要があります。 この手順は、ログインしているセッションごとに繰り返されます。


1. ダッシュボードの上部で、表示するタブをクリックします。

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]情報*

## からのレポートの生成 [!DNL Site-Wide Analysis Tool Dashboard]

1. ダッシュボードの右上隅のをクリックします **[!UICONTROL Generate Report]**.

1. 各のチェックボックスをオンにします **[!UICONTROL Type]** および **[!UICONTROL Priority]** レポートに含める設定。

1. クリック **[!UICONTROL Generate Report]**.

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-report-settings.png)
   *レポート設定*

| タブ | 説明 |
| --- | --- |
| Dashboard | システムの正常性を、現在の通知および推奨事項と共に優先度別に表示します。 |
| 情報 | お客様の連絡先情報および現在のチケットの概要と、インストールされている各Adobe Commerce製品の詳細情報を提供します。 |
| Recommendations | サイトで検出された問題に対処するためのベストプラクティスに基づいた推奨事項の一覧を表示します。 |
| 例外 | エラーハンドラーのない異常な状態によってアプリケーションによってスローされたエラーを一覧表示します。 |
| 拡張機能 | すべてのサードパーティの拡張機能とサードパーティライブラリを一覧表示します。 |

>[!NOTE]
>
>レコメンデーションを適用した後、 [!DNL Site-Wide Analysis Tool Dashboard] または生成されたレポート。
