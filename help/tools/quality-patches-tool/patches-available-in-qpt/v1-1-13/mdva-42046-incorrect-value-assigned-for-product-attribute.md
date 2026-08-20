---
title: MDVA-42046：製品属性に割り当てられた値が正しくありません
description: MDVA-42046 パッチは、日付入力フィールドを持つ製品を更新する際に、製品属性に誤った値が割り当てられる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-42046です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# MDVA-42046：製品属性に割り当てられた値が正しくありません

MDVA-42046 パッチは、日付入力フィールドを持つ製品を更新する際に、製品属性に誤った値が割り当てられる問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-42046です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.4 - 2.3.5-p2および2.4.0 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`news_from_date`および/または`news_to_date` フィールドを含む製品を保存すると、それらのフィールドの値はデフォルトにリセットされます。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. 手順1で作成した製品を書き出します。
1. 書き出されたCSV ファイルで、`news_from_date`および`news_to_date` フィールドにいくつかの値を入力します。 例：2021-05-15および2021-06-18
1. 変更したCSV ファイルを使用して製品を読み込みます。
1. 製品グリッドに「製品を日付から新規に設定」および「製品を日付から新規に設定」の追加の列を追加します。
1. 製品の編集ページを開き、変更を加えずに「**保存**」をクリックします。
1. 商品グリッドに戻り、商品のデータを確認します。

<u>期待される結果</u>:

「製品を日付から新規に設定」と「製品を日付から新規に設定」の両方は、保存前と同じです。

<u>実際の結果</u>:

* 「製品を新しい日付に設定」列と「製品を新しい日付に設定」列の値が変更されます。

* 「製品を日付から新しく設定」列には現在の日付が表示され、「製品を日付から新しく設定」列には空の値が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
