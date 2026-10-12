---
title: 'ACSD-61133: ''sales_clean_quotes'' cronが未承認の発注から見積を削除する'
description: ACSD-61133 パッチを適用して、「sales_clean_quotes」 cronが未承認の発注から引用符を削除するAdobe Commerceの問題を修正します。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-61133: `sales_clean_quotes` cronが未承認の発注から見積を削除します

ACSD-61133 パッチは、`sales_clean_quotes` cronが未承認の発注から見積を削除する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-61133です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p5 - 2.4.4-p11、2.4.5-p4 - 2.4.5-p10、および2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`sales_clean_quotes` cronは、未承認の発注から見積を削除します。 *[B2B発注]*&#x200B;は、cronによって削除されるので、購入した注文に関連付けられている見積もりの順序に変換できません。

<u>前提条件</u>:

Adobe Commerce [!UICONTROL B2B] モジュールがインストールされ、有効になっています。

<u>複製する手順</u>:

1. *[!UICONTROL B2B Purchase Order]*&#x200B;機能を有効にします。
1. 会社を作成する。
1. *[!UICONTROL Purchase Order]*&#x200B;を作成します。
1. 見積もりが期限切れになり、cronによって削除されるまで待ちます。 見積もりの有効期限は、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**&#x200B;で設定できます。
1. *[!UICONTROL Purchase Order]*&#x200B;を&#x200B;*[!UICONTROL My Purchase Order in Customer Dashboard]*&#x200B;または[!DNL GraphQL] `placeOrderForPurchaseOrder`の突然変異を使用して注文に変換します。

<u>期待される結果</u>:

アクティブな&#x200B;*[!UICONTROL Purchase Order]*&#x200B;に関連付けられている見積もりは、cronによって期限切れとして削除されません。 注文はストアフロントまたは[!DNL GraphQL]経由で正常に行われました。

<u>実際の結果</u>:

注文は行われず、エラーがストアフロントに表示されるか、[!DNL GraphQL]応答で返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
