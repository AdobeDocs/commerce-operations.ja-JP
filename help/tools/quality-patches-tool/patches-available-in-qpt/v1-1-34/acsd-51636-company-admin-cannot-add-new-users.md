---
title: ACSD-51636：会社管理者が顧客アカウントセクションから新しいユーザーを追加できない
description: ACSD-51636 パッチを適用すると、必要な役割と権限がすべて揃っているにもかかわらず、会社管理者がカスタマーアカウント セクションから新しいユーザーを追加できないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636：会社管理者が顧客アカウントセクションから新しいユーザーを追加できない

ACSD-51636 パッチは、必要な役割と権限がすべて揃っているにもかかわらず、会社の管理者が顧客アカウント セクションから新しいユーザーを追加できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 がインストールされている場合に使用できます。 パッチ ID は ACSD-51636 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

会社管理者は、必要な役割と権限がすべて揃っているにもかかわらず、顧客アカウントセクションから新しいユーザーを追加できません。

前提条件：

* B2B モジュールがインストールされています。
* 会社機能が有効になっています。

<u> 再現手順 </u>:

1. 新しい会社を作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動します。
1. **[!UICONTROL Company Admin]** タイプを *顧客* に編集します。
1. 顧客としてログインします。
1. **[!UICONTROL My Account]**/**[!UICONTROL Company Users]**/**[!UICONTROL Add User]** に移動して、ユーザーの詳細を追加し、アクティブにします。
1. 新規ユーザーを保存します。

<u> 期待される結果 </u>

管理者ユーザーは、新しいユーザーを追加できます。

<u> 実績 </u>

* 管理者ユーザーに「*問題が発生しました*」というエラーメッセージが表示される。
* 管理者ユーザーは、新しい顧客を作成できません。
* ログには、次のエラーが含まれます。

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)」を参照してください。
