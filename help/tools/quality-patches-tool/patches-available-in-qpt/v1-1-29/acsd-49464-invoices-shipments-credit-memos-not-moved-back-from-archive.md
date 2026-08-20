---
title: ACSD-49464：請求書、発送、クレジットメモがアーカイブから移動されない
description: 請求書、発送、クレジットメモがorderIdが異なる場合にアーカイブから戻されないAdobe Commerceの問題を修正するには、ACSD-49464 パッチを適用します。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-49464：請求書、発送、クレジットメモがアーカイブから移動されない

ACSD-49464 パッチは、orderIdが異なる場合に、請求書、出荷、およびクレジットメモがアーカイブから移動されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49464です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

orderIdが異なる場合、請求書、出荷、およびクレジットメモはアーカイブから戻されません。

<u>複製する手順</u>:

1. 注文、請求書、出荷、クレジットメモのアーカイブを有効にします。
1. 配送、請求書、クレジットメモなど、注文を作成して完了します。
1. 配送、請求書、およびクレジットメモのIDが注文番号と同じでないことを確認します。
1. オーダーをアーカイブに移動します。
1. アーカイブされた注文を注文管理に復元します。
1. それぞれの[!UICONTROL Invoice]、[!UICONTROL Shipping]、および[!UICONTROL Credit Memo] グリッドページの下の請求書、送料、およびクレジットメモの詳細を確認してください。

<u>期待される結果</u>:

元の関連レコードは、注文がアーカイブリストから注文管理に移動されたときに復元されます。

<u>実際の結果</u>:

* すべてのIDが異なる場合、送料、請求書、およびクレジットメモのレコードはありません。
* 注文レコードと関連レコードが同じIDを持つ場合、レコードが返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
