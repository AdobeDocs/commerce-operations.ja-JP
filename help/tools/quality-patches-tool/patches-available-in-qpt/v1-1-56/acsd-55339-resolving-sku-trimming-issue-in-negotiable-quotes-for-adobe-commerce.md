---
title: ACSD-55339:Adobe Commerceの交渉可能な引用符のSKU トリミングの問題を解決する
description: 先頭にゼロが付いた商品SKUがトリミングされ、ネゴシエーション エラーが発生するAdobe Commerceの問題を修正するには、ACSD-55339 パッチを適用します。
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
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
source-wordcount: '396'
ht-degree: 0%
---
# ACSD-55339:Adobe Commerceの交渉可能な引用符のSKU トリミングの問題を解決する

ACSD-55339 パッチでは、先頭にゼロが付いた製品SKUがトリミングされ、ネゴシエーション処理中にエラーが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-55339です。 この問題は、Adobe Commerce B2B 1.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

先頭にゼロが付いた数値の製品SKUは、交渉可能な引用符で使用するとトリミングされ、数量の更新や価格の設定を妨げるエラーが発生します。

<u>複製する手順</u>:

1. 管理パネルの「製品作成」セクションに移動します。
1. 製品の[!UICONTROL SKU]を01910として設定します。
1. ストアフロントにログインし、次の操作を実行します。
   1. 商品をカートに入れる。
   1. カートの表示と編集。
   1. 見積もりを依頼。
1. [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View]および[!UICONTROL Add Products by SKU] - 01910に移動します。

**注：** SKUは&#x200B;*01910*&#x200B;ではなく&#x200B;*1910*&#x200B;と表示されます。 この不一致は、SKU 1910の商品がカタログに存在しないため、数量の更新や価格の設定をユーザーが行うことを妨げます。

<u>期待される結果</u>:

交渉可能な見積もりは、エラーなしで正常に更新されます。

<u>実際の結果</u>:

製品が存在しないことを示す警告メッセージが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
