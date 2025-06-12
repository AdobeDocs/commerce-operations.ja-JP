---
title: MC-42528:categoryList のGraphQL クエリにすべてのカテゴリが表示される
description: この MC-42528 パッチは、特定のカテゴリのブラウジングカテゴリが「拒否」に設定されている場合、「categoryList」のGraphQL クエリが、割り当て済みカテゴリと未割り当てカテゴリの両方を返す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4 がインストールされている場合に利用できます。 パッチ ID は MC-42528 です。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528:categoryList のGraphQL クエリにすべてのカテゴリが表示される

この MC-42528 パッチは、特定のカテゴリのブラウジングカテゴリが「拒否」に設定されている場合、`categoryList` のGraphQL クエリが割り当て済みカテゴリと未割り当てカテゴリの両方を返す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.4 がインストールされている場合に使用できます。 パッチ ID は MC-42528 です。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`categoryList` のGraphQL クエリは、割り当て済みカテゴリと未割り当てカテゴリの両方を返します。

<u> 再現手順 </u>:

1. CAT1 と CAT2 の 2 つのカテゴリを作成し、各カテゴリにいくつかの製品を割り当てます。
1. プライベート共有カタログを作成します。
1. 会社ユーザーを作成し、作成した共有カタログに割り当てます。
1. CAT1 をカスタムカタログに割り当て、プライベートカタログの顧客グループに対してカテゴリ権限を「許可」 ブラウジングカテゴリに設定します。
1. プライベートカタログの顧客グループのカテゴリ権限を、CAT2 の閲覧カテゴリを「拒否」に設定します。
1. `categoryList` または `categories` GraphQL クエリを会社ユーザーとして実行します。

<u> 期待される結果 </u>:

応答には CAT1 のみが表示されます。

<u> 実際の結果 </u>:

カテゴリの閲覧権限に関係なく、すべてのカテゴリが応答に表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
