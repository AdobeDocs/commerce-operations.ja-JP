---
title: MDVA-43601：完全なインデックス再作成後、「catalogrule_product_price」テーブルからトリガーが削除される
description: MDVA-43601 パッチは、「catalogrule_rule」または「catalogrule_product」の完全な再インデックスの後に「catalogrule_product_price」テーブルからトリガーが削除される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-43601です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43601：完全なインデックス再作成後、「catalogrule_product_price」テーブルからトリガーが削除される

MDVA-43601 パッチは、`catalogrule_rule`または`catalogrule_product`の完全な再インデックス後に`catalogrule_product_price` テーブルからトリガーが削除される問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-43601です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

トリガーは、`catalogrule_rule`または`catalogrule_product`の完全な再インデックスの後に`catalogrule_product_price` テーブルから削除されます。

<u>複製する手順</u>:

1. すべてのインデクサーを&#x200B;*スケジュール別に更新*&#x200B;に設定します。
1. 次のSQL リクエストを実行して、`catalogrule_product_price` テーブル用に作成されたトリガーを確認します。

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. 次のコマンドを実行して、手動で`catalogrule_rule`または`catalogrule_product`のインデックスを再作成します：`bin/magento indexer:reindex catalogrule_rule`
1. `catalogrule_product_price` テーブルのトリガーをもう一度確認してください。

<u>期待される結果</u>:

`catalogrule_product_price` テーブルのトリガーは、完全なインデックス再作成後も保持されます。

<u>実際の結果</u>:

`catalogrule_product_price` テーブルのトリガーが見つかりません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
