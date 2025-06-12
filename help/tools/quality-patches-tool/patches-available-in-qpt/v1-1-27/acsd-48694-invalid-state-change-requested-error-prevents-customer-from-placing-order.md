---
title: 'ACSD-48694: Invalid state change requested エラーにより、お客様は注文できません'
description: ACSD-48694 パッチを適用すると、「Invalid state change requested （無効なステート変更がリクエストされました）」というエラーによって、お客様の注文が妨げられるAdobe Commerceの問題が修正されます。
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694: *無効な状態変更が要求されました* エラーにより、お客様は注文できません

ACSD-48694 パッチでは、エラー *無効な状態変更がリクエストされました* により、お客様が注文できない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-48694 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.37-p4、2.4.1 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

エラー *無効な状態変更がリクエストされました* により、お客様は注文できません。

<u> 再現手順 </u>:

1. 関数に `sleep()` を含めることで、`/estimate-shipping-methods` リクエストの間にわずかな遅延を加え `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()`、チェックアウト中に配送手順から支払い手順に進む `/shipping-information` の後に `/estimate-shipping-methods` リクエストが完了するようにします。
1. *disable_locking: 1* 設定で [!DNL Redis] を使用するようにセッションを設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]** を開き、*[!UICONTROL Persistent Shopping Cart]* を有効にします。
1. 顧客としてログインし、商品を買い物かごに追加します。
1. カスタマーセッションの有効期限が切れるようにします。 永続的な Cookie と買い物かごは引き続き保存されます。
1. チェックアウトに移動し、配送先住所を追加して、支払いセクションに移動します。
1. ホームページまたはその他のページに戻り、カスタマーアカウントでログインします。
1. セッションの有効期限をもう一度切ります。
1. 次に、チェックアウトページに直接移動し、支払い手順に移動します。
1. 注文してみてください。

<u> 期待される結果 </u>:

* エラーはありません。
* 注文が完了すると、「ありがとうございました *ページが表示され* す。

<u> 実際の結果 </u>:

「*無効な状態変更がリクエストされました*」というエラーが表示されますが、注文は行われます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
