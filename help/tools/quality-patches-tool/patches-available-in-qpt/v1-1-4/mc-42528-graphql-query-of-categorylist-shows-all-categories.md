---
title: 'MC-42528: categoryListのGraphQL クエリにすべてのカテゴリが表示される'
description: MC-42528 パッチでは、特定のカテゴリの「参照カテゴリ」が「拒否」に設定されている場合、「categoryList」のGraphQL クエリで割り当てられたカテゴリと割り当てられていないカテゴリの両方が返される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4がインストールされている場合に利用できます。 パッチ IDはMC-42528です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MC-42528: categoryListのGraphQL クエリにすべてのカテゴリが表示される

MC-42528 パッチは、特定のカテゴリのブラウジングカテゴリが「拒否」に設定されている場合、`categoryList`のGraphQL クエリが割り当てられたカテゴリと割り当てられていないカテゴリの両方を返す問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMC-42528です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`categoryList`のGraphQL クエリは、割り当てられたカテゴリと割り当てられていないカテゴリの両方を返します。

<u>複製する手順</u>:

1. CAT1とCAT2の2つのカテゴリを作成し、各カテゴリに少数の製品を割り当てます。
1. プライベート共有カタログを作成します。
1. 会社ユーザーを作成し、作成した共有カタログに割り当てます。
1. カスタムカタログにCAT1を割り当て、プライベートカタログの顧客グループのカテゴリのアクセスを「許可」に設定します。
1. CAT2のカテゴリ権限を、プライベートカタログの顧客グループのカテゴリの参照を「拒否」に設定します。
1. `categoryList`または`categories` GraphQL クエリを会社ユーザーとして実行します。

<u>期待される結果</u>:

応答にCAT1のみが表示されます。

<u>実際の結果</u>:

カテゴリの閲覧権限に関係なく、すべてのカテゴリが応答に表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
