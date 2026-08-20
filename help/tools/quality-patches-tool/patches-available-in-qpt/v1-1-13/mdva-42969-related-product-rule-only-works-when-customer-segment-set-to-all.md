---
title: MDVA-42969：関連製品ルールは、顧客セグメントが「すべて」に設定されている場合にのみ機能します
description: MDVA-42969 パッチは、顧客セグメントが「すべて」に設定されている場合にのみ、関連する製品ルールが機能する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-42969です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# MDVA-42969：関連製品ルールは、顧客セグメントが「すべて」に設定されている場合にのみ機能します

MDVA-42969 パッチは、顧客セグメントが「すべて」に設定されている場合にのみ、関連する製品ルールが機能する問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-42969です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

関連製品ルールは、顧客セグメントが「すべて」に設定されている場合にのみ機能します。

<u>複製する手順</u>:

1. **ストア** > **設定** > **カタログ** > **ルールベースの製品リレーション**&#x200B;に移動し、**関連製品の表示** = **ルールベースのみ**&#x200B;を設定します。
1. **顧客** > **セグメント**&#x200B;に移動し、新しいセグメントを作成します：**適用先** = **訪問者と登録済み顧客**。
1. **マーケティング**/**関連製品ルール**&#x200B;に移動し、新しいルールを作成します。

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. ストアフロントで一致する商品を開き、表示する商品が表示されていることを確認します。
1. ステップ 3で作成したルールを変更し、ステップ 2から&#x200B;**顧客セグメント** = **特定** > **セグメント**&#x200B;を設定します。
1. ストアフロントで一致する商品を開きます。

<u>期待される結果</u>:

ルールベースの関連製品は、次の設定で顧客セグメントが作成されるので、製品の訪問者のストアフロントに表示されます。

**申し込み先** = **訪問者と登録済み顧客**

<u>実際の結果</u>:

関連製品は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
