---
title: 'ACSD-62118: [!UICONTROL Purchase Order] メソッドを使用して行われたB2B注文について、「sales_order_tax_item」テーブルが完全に更新されない'
description: ACSD-62118 パッチを適用して、[!UICONTROL Purchase Order] メソッドを使用してB2B注文を行ったときに「sales_order_tax_item」テーブルが完全に更新されないAdobe Commerceの問題を修正します。
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-62118: [!UICONTROL Purchase Order] メソッドを使用して行われたB2B注文について、`sales_order_tax_item` テーブルが完全に更新されていません

ACSD-62118 パッチは、*[!UICONTROL Purchase Order]* メソッドを使用してB2B注文を行ったときに`sales_order_tax_item` テーブルが完全に更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-62118です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Purchase Order]* メソッドを使用してB2B注文を行うと、`sales_order_tax_item` テーブルが完全に更新されません。 この問題は、税計算と注文処理に影響します。 具体的には、APIを介して注文をクエリする場合、`applied_taxes`配列は空であり、`tax_item_amount`と`tax_item_percent`の両方がNULLです。

<u>複製する手順</u>:

1. **[!UICONTROL Product]**&#x200B;と&#x200B;**[!UICONTROL Shipping]**&#x200B;の両方に税ルールを追加します。
1. 会社の設定で&#x200B;**[!UICONTROL Purchase Order]** メソッドを有効にします。
1. 会社管理者ユーザーとしてログインします。
1. オフラインの支払い方法を使用して&#x200B;**[!UICONTROL Purchase Order]**&#x200B;を配置します。
1. [!UICONTROL Purchase Order]が自動承認され、注文に変換された後、`sales_order_tax_item` テーブルとREST APIで税データを確認します。

<u>期待される結果</u>:

* `sales_order_tax_item` テーブルには`tax_item` データを含める必要があります。
* `applied_taxes`配列は、他の支払い方法（小切手/マネーオーダーなど）と同様に、発注のAPI応答に正しい税情報を表示する必要があります。

<u>実際の結果</u>:

* `sales_order_tax_item` テーブルに`tax_item` データが含まれていません。
* *[!UICONTROL Purchase Order]*&#x200B;のAPI応答で、`applied_taxes`および`item_applied_taxes`配列が空です。
* *[!UICONTROL Purchase Order]*&#x200B;支払い方法を使用する場合、税金データは表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
