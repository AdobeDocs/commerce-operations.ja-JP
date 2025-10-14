---
title: ACSD-55427：管理者が製品ページの**[!UICONTROL Product in Shared Catalogs]**から製品の割り当てを解除できない
description: ACSD-55427 パッチを適用して、**[!UICONTROL Product in Shared Catalogs]**から商品の割り当てを解除できないAdobe Commerceの問題を修正してください。
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427：管理者が製品ページの **[!UICONTROL Product in Shared Catalogs]** から製品の割り当てを解除できない

ACSD-55427 パッチでは、Commerce Admin のカタログ内の製品ページの **[!UICONTROL Product in Shared Catalogs]** から製品の割り当てを解除できない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 がインストールされている場合に使用できます。 パッチ ID は ACSD-55427 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Commerce Admin のカタログにある製品のページで、**[!UICONTROL Product in Shared Catalogs]** から製品の割り当てを解除することはできません。

<u> 再現手順 </u>:

前提条件：B2B と **[!UICONTROL Shared Catalogs]** の両方が有効な状態でAdobe Commerceがインストールされていること。
1. 商品を作成します。
1. 共有カタログダッシュボードに移動し、デフォルトの共有カタログを開きます。
1. 製品をデフォルトのカタログに割り当て、製品価格よりも低い価格を設定します。
1. 共有カタログを保存します。
1. [!UICONTROL CRON] を実行して、コンシューマー/インデクサーを更新します。
1. 製品を開いて、「」セクションの下から製品 **[!UICONTROL Product in Shared Catalogs]** 削除します。

<u> 期待される結果 </u>:

製品は、**[!UICONTROL Product in Shared Catalogs]** のセクションのから削除する必要があります。

<u> 実際の結果 </u>:

製品は、**[!UICONTROL Product in Shared Catalogs]** のセクションに引き続き表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
