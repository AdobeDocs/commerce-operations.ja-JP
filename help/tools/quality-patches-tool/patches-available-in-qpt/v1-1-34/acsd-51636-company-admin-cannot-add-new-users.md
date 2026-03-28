---
title: ACSD-51636：会社管理者が「顧客アカウント」セクションから新規ユーザーを追加できない
description: ACSD-51636 パッチを適用して、会社管理者が必要な役割と権限を持っていてもカスタマーアカウントセクションから新規ユーザーを追加できないAdobe Commerceの問題を修正します。
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636：会社管理者が「顧客アカウント」セクションから新規ユーザーを追加できない

ACSD-51636 パッチでは、必要な役割と権限がすべて付与されているにもかかわらず、会社管理者が顧客アカウントセクションから新規ユーザーを追加できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-51636です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

会社管理者は、必要な役割と権限をすべて持っているにもかかわらず、顧客アカウントセクションから新しいユーザーを追加することはできません。

前提条件：

* B2B モジュールがインストールされています。
* 会社の機能が有効になっています。

<u>複製する手順</u>:

1. 新しい会社を作る。
1. **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;に移動します。
1. **[!UICONTROL Company Admin]** タイプを&#x200B;*顧客*&#x200B;に編集します。
1. 顧客としてログインします。
1. **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]**&#x200B;に移動し、ユーザーの詳細を追加してアクティブにします。
1. 新規ユーザーを保存します。

<u>期待される結果</u>

管理者ユーザーは新しいユーザーを追加できます。

<u>実際の結果</u>

* 管理者ユーザーは、次のエラーメッセージを受け取ります：*問題が発生しました*。
* 管理者ユーザーは新しい顧客を作成できません。
* ログに次のエラーが含まれています。

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [ [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
