---
title: ACSD-59952：別の共有カタログと同じグループ IDを持つ共有カタログを削除するとエラーが発生する
description: ACSD-59952 パッチを適用して、別の共有カタログと同じ「customer_group_id」を持つ共有カタログを削除する際にエラーがスローされるAdobe Commerceの問題を修正します。
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [ サポートナレッジベースの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対するパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
