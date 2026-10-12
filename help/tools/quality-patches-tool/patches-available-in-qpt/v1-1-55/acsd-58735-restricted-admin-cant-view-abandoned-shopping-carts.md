---
title: ACSD-58735：制限付き管理者が、関連するweb サイトの顧客アカウントで放棄されたショッピングカートを表示できない
description: ACSD-58735 パッチを適用して、制限付き管理者が関連するweb サイトのCommerce管理者のお客様アカウントページで放棄されたショッピングカートを表示できないAdobe Commerceの問題を修正します。
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '408'
ht-degree: 0%
---
# ACSD-58735：制限付き管理者が、関連するweb サイトの顧客アカウントで放棄されたショッピングカートを表示できない

ACSD-58735 パッチでは、ロールが制限された管理者ユーザーがCommerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** タブから放棄された顧客のショッピングカートを表示できない問題を修正します。

この問題は、複数のweb サイトのグリッドビューを表示する際に、放棄されたカートがデフォルトで管理パネルに読み込まれている場合、関連付けられたストア IDを表示できないために発生します。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58735です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者は、管理者パネルの顧客アカウントページで放棄されたショッピングカートを表示できません。

<u>複製する手順</u>:

1. いずれかのweb サイトのみにアクセスできる管理者役割を作成します。
1. 放棄されたカートの作成。
1. フル権限を持つ管理者ユーザーとしてログインします。 **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;を確認し、買い物かごが表示されることを確認します。
1. **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;を制限付き管理者ユーザーとして確認してください。

<u>期待される結果</u>:

制限付き管理者は、関連するweb サイトの放棄されたショッピングカートを表示できます。

<u>実際の結果</u>:

制限付き管理者には、関連するweb サイトの放棄されたショッピングカートは表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
