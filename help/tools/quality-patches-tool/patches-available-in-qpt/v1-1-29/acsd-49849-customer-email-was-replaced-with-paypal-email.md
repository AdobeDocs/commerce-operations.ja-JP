---
title: ACSD-49849：顧客メールがPayPal メールに置き換えられました
description: GraphQL経由でPayPal Expressで注文する際に、お客様の電子メールがPayPalの電子メールに置き換えられたAdobe Commerceの問題を修正するには、ACSD-49849 パッチを適用します。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# ACSD-49849：お客様の電子メールが[!DNL PayPal]個の電子メールに置き換えられました

ACSD-49849 パッチは、GraphQLを介して[!DNL PayPal Express]への注文時に、お客様の電子メールが[!DNL PayPal's]の電子メールに置き換えられる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49849です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLを介して[!DNL PayPal Express]に注文すると、お客様の電子メールは[!DNL PayPal's]の電子メールに置き換えられます。

<u>複製する手順</u>:

1. **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**&#x200B;に移動します。
1. [!DNL PayPal Express]を有効にして設定し、**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;を設定します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、シンプルな製品を作成します。
1. GraphQLを使用して、ゲストチェックアウトを完了します。 詳しくは、Adobe Commerce開発者ドキュメントの[GraphQL チェックアウトチュートリアル &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)を参照してください。
1. 支払い方法として[!DNL PayPal Express]を使用します。
1. カート用の電子メールを[設定した手順で使用した電子メールは、Adobe Commerce開発者向けドキュメントに](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/)記載されています。
1. 注文が完了したら、Adobe Commerce管理者に移動し、作成された注文のメールを確認します。

<u>期待される結果</u>:

このメールは、チェックアウト時に設定したものと同じです。

<u>実際の結果</u>:

チェックアウト時に設定された電子メールは、[!DNL PayPal] アカウントで設定された電子メールによって上書きされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
