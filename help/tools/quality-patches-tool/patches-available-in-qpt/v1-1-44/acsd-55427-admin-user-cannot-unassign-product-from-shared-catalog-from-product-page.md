---
title: ACSD-55427：管理者は、製品ページの**[!UICONTROL Product in Shared Catalogs]**から製品の割り当てを解除できません
description: '**[!UICONTROL Product in Shared Catalogs]**から製品を割り当て解除できないAdobe Commerceの問題を修正するには、ACSD-55427 パッチを適用します。'
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55427：管理者は、製品ページの&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;から製品の割り当てを解除できません

ACSD-55427 パッチでは、Commerce管理者のカタログの製品ページで&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;から製品の割り当てを解除できない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-55427です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Commerce Adminのカタログ内の製品ページの&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;から製品の割り当てを解除することはできません。

<u>複製する手順</u>:

前提条件：Adobe Commerceがインストールされていて、B2Bと&#x200B;**[!UICONTROL Shared Catalogs]**&#x200B;の両方が有効になっている。
1. 商品を作成する。
1. 共有カタログダッシュボードに移動し、デフォルトの共有カタログを開きます。
1. 商品をデフォルトのカタログに割り当て、商品価格よりも低い価格を設定します。
1. 共有カタログを保存します。
1. コンシューマー/インデクサーを更新するには、[!UICONTROL CRON]を実行します。
1. 製品を開き、**[!UICONTROL Product in Shared Catalogs]** セクションの下から製品を削除します。

<u>期待される結果</u>:

製品は&#x200B;**[!UICONTROL Product in Shared Catalogs]** セクションの下から削除する必要があります。

<u>実際の結果</u>:

製品は引き続き&#x200B;**[!UICONTROL Product in Shared Catalogs]** セクションに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
