---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* ステータスが*[!UICONTROL Related Product Rules]*に適用されていません'
description: ACSD-54739 パッチを適用して、*[!UICONTROL Product Stock]* ステータスが*[!UICONTROL Related Product Rules]*に適用されていないAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* ステータスが&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;に適用されていません

ACSD-54739 パッチは、*[!UICONTROL Related Product Rules]*&#x200B;に&#x200B;*[!UICONTROL Product stock]* ステータスが適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-54739です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Product stock]*&#x200B;のステータスは&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;に適用されません。

<u>複製する手順</u>:

1. **[!UICONTROL Display Out of Stock Products]**&#x200B;設定を&#x200B;*Yes*&#x200B;に設定します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]**&#x200B;に移動し、プロモーションルール条件に&#x200B;*Yes*&#x200B;を設定します。
1. 関連製品ルールを作成します。 **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** >属性数量を持つ条件を追加に移動します（在庫あり/在庫切れを選択）。
1. フロントエンドの製品を確認してください。

<u>期待される結果</u>:

在庫済み/在庫切れ商品は&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;までに一致します。

<u>実際の結果</u>:

在庫/在庫切れ商品が&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;と一致しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
