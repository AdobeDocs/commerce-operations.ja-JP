---
title: ACSD-59952：別の共有カタログと同じグループ IDを持つ共有カタログを削除するとエラーが発生する
description: ACSD-59952 パッチを適用して、別の共有カタログと同じ「customer_group_id」を持つ共有カタログを削除する際にエラーがスローされるAdobe Commerceの問題を修正します。
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-59952：別の共有カタログと同じグループ IDを持つ共有カタログを削除するとエラーが発生する

ACSD-59952 パッチは、同じ`customer_group_id`の共有カタログを別の共有カタログとして削除する際に発生するエラーを修正します。 ユーザーがこのような共有カタログを作成するのをさらに妨げます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-59952です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

別の共有カタログと同じ`customer_group_id`を持つ新しい共有カタログを作成できません。 ただし、同じ`customer_group_id`の共有カタログを削除しようとすると、エラーがスローされます。

<u>前提条件</u>:

Adobe Commerce B2B モジュールの取り付け。

<u>複製する手順</u>:

1. 次のREST API呼び出しを使用して、同じ`customer_group_id`に割り当てられた複数の共有カタログを作成します。

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. 次のREST API呼び出しを使用して、共有カタログのいずれかを削除してみてください。

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>期待される結果</u>:

* 同じ`customer_group_id`に割り当てられた複数の共有カタログを作成することはできません。
* 上記の場合の共有カタログは正常に削除されます。

<u>実際の結果</u>:

* 同じ`customer_group_id`に割り当てられた複数の共有カタログを作成できます。
* 同じ`customer_group_id`の共有カタログを削除しようとすると、次のエラーが返されます。*共有カタログを削除できません*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [&#x200B; サポートナレッジベースの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対するパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
