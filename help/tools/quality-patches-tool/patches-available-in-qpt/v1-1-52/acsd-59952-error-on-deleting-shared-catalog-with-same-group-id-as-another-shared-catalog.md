---
title: ACSD-59952：別の共有カタログと同じグループ ID を持つ共有カタログの削除中にエラーが発生しました
description: ACSD-59952 パッチを適用すると、別の共有カタログと同じ「customer_group_id」を持つ共有カタログを削除するとエラーがスローされるAdobe Commerceの問題を修正できます。
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952：別の共有カタログと同じグループ ID を持つ共有カタログの削除中にエラーが発生しました

ACSD-59952 パッチは、別の共有カタログと同じ `customer_group_id` を持つ共有カタログを削除する際にスローされるエラーを修正します。 また、ユーザーがそのような共有カタログを作成することもできません。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-59952 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

別の共有カタログと同じ `customer_group_id` を持つ新しい共有カタログを作成できません。 ただし、その際、同じ `customer_group_id` を持つ共有カタログを削除しようとするとエラーがスローされる。

<u> 前提条件 </u>:

Adobe Commerce B2B モジュールをインストールします。

<u> 再現手順 </u>:

1. 次の REST API 呼び出しを使用して、同じ `customer_group_id` に割り当てられた複数の共有カタログを作成します。

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

1. 次の REST API 呼び出しを使用して、共有カタログのいずれかを削除してみてください。

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u> 期待される結果 </u>:

* 同じ `customer_group_id` に割り当てられた複数の共有カタログを作成することはできません。
* 上記の場合、共有カタログは正常に削除されました。

<u> 実際の結果 </u>:

* 同じ `customer_group_id` ーザーに割り当てられた複数の共有カタログを作成できます。
* 同じ `customer_group_id` を持つ共有カタログを削除しようとすると、次のエラーが返されます。*共有カタログを削除できません*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) アドビのサポートナレッジベースに含まれています。
* [ を使用して、Adobe Commerceの問題にパッチが使用できるかどうかを  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) サポートナレッジベースで確認します。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
