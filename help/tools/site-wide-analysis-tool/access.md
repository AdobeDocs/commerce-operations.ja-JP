---
title: アクセス方法  [!DNL Site-Wide Analysis Tool]
description: にアクセスする方法を説明し  [!DNL Site-Wide Analysis Tool] す。
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 2896442432158456698cac2d566cf0f61b5d7847
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool] へのアクセス方法

ストアの [!DNL Site-Wide Analysis Tool] ージから [!UICONTROL Admin Panel] ダッシュボードにアクセスできます。

[!DNL Site-Wide Analysis Tool] サービスは、ユーザー [ 役割リソース ](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/tools/developer-tools#operation-modes) にアクセスする権限を持つ [!UICONTROL Admin] ユーザーが [ 実稼動モード ](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/user-accounts/permissions-user-roles) で使用できます。

>[!NOTE]
>
>2024 年 4 月 23 日（PT）より、[!DNL Site-Wide Analysis Tool] は廃止され、Adobe Commerce オンプレミスのお客様は使用できなくなりました。


![Site-Wide Analysis Dashboard](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

>[!NOTE]
>
>**[!DNL Support Permissions]** にアクセスするには、アカウントに [!DNL Site-Wide Analysis Tool Dashboard] の権限が付与されている必要があります。
>&#x200B;>詳しくは、ユーザーガイドの [ アカウント  [!DNL Commerce]  共有 ](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html?lang=ja) を参照してください。

## ストアの [!DNL Site-Wide Analysis Tool Dashboard] から [!UICONTROL Admin Panel] へのログイン

### 手順 1：権限の確認

[!UICONTROL Admin] ユーザーアカウントに、[!DNL Site-Wide Analysis Tool] 割り当てられたユーザーの役割 [ を通じて ](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/user-accounts/permissions-user-roles) にアクセスする権限があることを確認します。

>[!IMPORTANT]
>
>[!DNL Site-Wide Analysis Tool] 役割のリソース （権限）が自動的に割り当てられて **ません**。 [!UICONTROL Admin] 内の各ユーザーアカウントに個別に割り当てられたユーザーの役割および役割に対してアクティブ化する必要があります。

カスタムの役割に [!DNL Site-Wide Analysis Tool] のアクセス権が必要な場合は、次の操作を行います。

1. **[!UICONTROL Reports]**/*[!UICONTROL System Insights]*/**[!UICONTROL Site-Wide Analysis Tool]** 役割リソースを選択します。

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-role-access.png)
   役割 *[!DNL Site-Wide Analysis Tool]権限が選択されました*

1. 「**[!UICONTROL Save Role]**」をクリックします。

1. その役割を割り当てられているユーザーに [!DNL Admin] ーザーからログアウトして、もう一度ログインするように通知します。

>[!NOTE]
>
>ユーザーアカウントが [!DNL Site-Wide Analysis Tool] にアクセスする権限を持ち、[!UICONTROL Admin] からツールにアクセスしようとすると 403 エラーが発生することを確認した場合、クラウドインフラストラクチャー上のAdobe Commerceのインスタンスで HTTP アクセス制御が有効になっている可能性があります。 HTTP 認証が有効になっている場合、[!DNL Site-Wide Analysis Tool] ダッシュボードはサポートされません。 この問題の解決について詳しくは、[ サポート記事 ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento) を参照してください。

### 手順 2:[!DNL Site-Wide Analysis Tool] へのアクセス

1. *[!UICONTROL Admin]* サイドバーで、**[!UICONTROL Reports]**/*[!UICONTROL System Insights]*/**[!UICONTROL Site-Wide Analysis Tool]** に移動します。

   ![Site-Wide Analysis Dashboard](../../assets/tools/ac-admin-panel-marked.jpg)
   Adobe Commerce内の *[!DNL Site-Wide Analysis Tool]内の [!UICONTROL Admin Panel] の場所*

1. *の* 利用条件 [!DNL Site-Wide Analysis Tool] をお読みになり、「**[!UICONTROL Accept]**」をクリックして続行します。

   各ユーザーは、セッションの利用条件に同意する必要があります。 この手順は、ログインしているセッションごとに繰り返されます。


1. ダッシュボードの上部で、表示するタブをクリックします。

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]情報*

## [!DNL Site-Wide Analysis Tool Dashboard] からのレポートの生成

1. ダッシュボードの右上隅にある「**[!UICONTROL Generate Report]**」をクリックします。

1. レポートに含める各 **[!UICONTROL Type]** と **[!UICONTROL Priority]** 設定のチェックボックスを選択します。

1. 「**[!UICONTROL Generate Report]**」をクリックします。

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-report-settings.png)
   *報告書設定*

| タブ | 説明 |
| --- | --- |
| Dashboard | システムの正常性を、現在の通知および推奨事項と共に優先度別に表示します。 |
| 情報 | お客様の連絡先情報および現在のチケットの概要と、インストールされている各Adobe Commerce製品の詳細情報を提供します。 |
| 推奨事項 | サイトで検出された問題に対処するためのベストプラクティスに基づいた推奨事項の一覧を表示します。 |
| 例外 | エラーハンドラーのない異常な状態によってアプリケーションによってスローされたエラーを一覧表示します。 |
| 拡張機能 | すべてのサードパーティの拡張機能とサードパーティライブラリを一覧表示します。 |

>[!NOTE]
>
>レコメンデーションを適用した後、[!DNL Site-Wide Analysis Tool Dashboard] または生成されたレポートでレコメンデーションが更新されるまで数日かかる場合があります。
