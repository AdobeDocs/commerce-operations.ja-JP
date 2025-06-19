---
title: ACSD-61103:API を使用してカスタマーログインが成功した後、失敗数が 0 にリセットされない
description: ACSD-61103 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、ユーザーが API エンドポイントを介して正常にログインした後、「customer_entity」テーブルのエラー数がゼロにリセットされません。
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103:API を使用してカスタマーログインが成功した後、失敗数が 0 にリセットされない

ACSD-61103 パッチを使用すると、API エンドポイントを介してユーザーが正常にログインした後、`customer_entity` テーブルのエラー数がゼロにリセットされない問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61103 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーが API エンドポイントを使用して正常にログインした後でも、`customer_entity` テーブルのエラー数が 0 にリセットされない。

<u> 再現手順 </u>:

1. 顧客アカウントを作成します。
1. 誤った詳細を使用して、API 経由で顧客トークンを生成する。
1. 上記の顧客について、`customer_entity` DB テーブルの `failures_num` 列を確認します。
1. 正しい詳細を使用して、API 経由で顧客トークンを生成します。
1. 上記の顧客について、`customer_entity` DB テーブルの `failures_num` 列を確認します。

<u> 期待される結果 </u>:

正しい資格情報を使用して API 経由で顧客トークンを生成した後、`failures_num` の列を 0 にリセットする必要があります。

<u> 実際の結果 </u>:

正しい資格情報を使用して API を介して顧客トークンを生成した後、`failures_num` 列が 0 にリセットされない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
