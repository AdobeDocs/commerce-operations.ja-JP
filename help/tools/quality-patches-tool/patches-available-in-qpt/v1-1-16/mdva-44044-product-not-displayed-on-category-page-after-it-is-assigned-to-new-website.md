---
title: MDVA-44044：新しいweb サイトに割り当てられた製品がカテゴリーページに表示されない
description: MDVA-44044 パッチは、製品が新しいweb サイトに割り当てられた後、カテゴリーページに製品が表示されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16がインストールされている場合に利用できます。 パッチ IDはMDVA-44044です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-44044：新しいweb サイトに割り当てられた製品がカテゴリーページに表示されない

MDVA-44044 パッチは、製品が新しいweb サイトに割り当てられた後、カテゴリーページに製品が表示されない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16がインストールされている場合に使用できます。 パッチ IDはMDVA-44044です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

新しいweb サイトに割り当てられた製品は、カテゴリーページに表示されません。

<u>複製する手順</u>:

1. インデクサーモードをスケジュールに設定します。
1. ふたつ目のweb サイト、実店舗ビューの作成。
1. セカンダリストアコードを`index.php`に追加します。

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. 新しいカテゴリを作成します。
1. 新しく作成したカテゴリに割り当てられた新しい製品を作成します。 プライマリ web サイトにのみ割り当てるようにしましょう。
1. cronを実行します。
1. ストアフロントからカテゴリを開きます。
1. 商品をセカンダリ web サイトに割り当てます。
1. cronをもう一度実行します。

<u>期待される結果</u>:

スケジュールされたインデクサーの後に、製品がカテゴリーページに表示されます。

<u>実際の結果</u>:

完全な再インデックスが作成されるまで、製品はカテゴリーページに表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
