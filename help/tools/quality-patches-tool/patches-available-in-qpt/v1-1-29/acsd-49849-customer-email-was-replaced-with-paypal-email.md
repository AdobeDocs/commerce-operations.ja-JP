---
title: ACSD-49849：顧客の電子メールが PayPal の電子メールに置き換えられました
description: GraphQL経由で PayPal Express で注文する際に、お客様のメールが PayPal メールに置き換わっていたAdobe Commerceの問題を修正するために、ACSD-49849 パッチを適用します。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849：顧客の電子メールが [!DNL PayPal] の電子メールに置き換えられる

ACSD-49849 パッチは、GraphQL経由で [!DNL PayPal Express] に注文する際に、顧客のメールが [!DNL PayPal's] のメールに置き換わる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49849 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL経由で顧客に注文すると、顧客のメールが [!DNL PayPal's] のメールに置き換 [!DNL PayPal Express] られます。

<u> 再現手順 </u>:

1. **[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Payments]** に移動します。
1. [!DNL PayPal Express] を有効にして設定し、**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** に設定します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動して、シンプルな製品を作成します。
1. GraphQLを使用してゲストのチェックアウトを完了します。 詳しくは、Adobe Commerce開発者向けドキュメントの [GraphQLのチェックアウトチュートリアル ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) を参照してください。
1. 支払方法として [!DNL PayPal Express] を使用します。
1. Adobe Commerce開発者ドキュメントの [ 買い物かごへのメールの設定 ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) 手順で使用したメールに注意してください。
1. 注文したら、Adobe Commerce管理者に移動し、作成した注文のメールを確認します。

<u> 期待される結果 </u>:

メールは、チェックアウト時に設定されたものと同じです。

<u> 実際の結果 </u>:

チェックアウト中のメールセットは、[!DNL PayPal] アカウントのメールセットによって上書きされます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
