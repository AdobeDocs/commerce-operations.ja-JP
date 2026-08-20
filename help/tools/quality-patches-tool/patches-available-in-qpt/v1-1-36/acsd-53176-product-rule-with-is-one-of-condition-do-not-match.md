---
title: 'ACSD-53176: 「次のいずれかである」条件を持つ製品ルールが一致しません'
description: 「一致する製品」に関する関連する製品ルール「の1つ」の条件が正しく機能しないAdobe Commerceの問題を修正するには、ACSD-53176 パッチを適用します。
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-53176: `is one of`条件の製品ルールが一致しません

ACSD-53176 パッチは、**製品が**&#x200B;に一致するために、関連する製品ルール `is one of`条件が正しく機能しない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-53176です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

関連する製品ルール `is one of`の条件は、**製品が**&#x200B;に一致する場合に正しく機能しません。

<u>複製する手順</u>:

1. 3～4個の商品を作成する：
1. 新しい関連製品ルールを作成します。

   2つ以上の製品に一致するようにルールを設定します。
   * `SKU is one of "S1,S2".`

   ルールを設定して、2つ以上の項目を表示します。
   * `Product SKU is one of constant value "S2,S3".`

1. ストアフロントでS1製品を開きます。

<u>期待される結果</u>:

関連商品「S2」と「S3」は、商品ページ「S1」と「S2」の両方に表示されます。

<u>実際の結果</u>:

関連商品は商品ページに表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
