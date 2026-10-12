---
title: ACSD-65822：バンドルおよび設定可能な製品数量がショッピングカートに正しく反映されない
description: ACSD-65822 パッチを適用して、バンドル製品を追加する際に、管理パネルのカスタマーショッピングカートのセクションに数量が0として表示されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-65822: バンドルおよび設定可能な製品数量が[!UICONTROL Shopping Cart]に正しく反映されない

ACSD-65822 パッチは、*[!UICONTROL Customer's Activities]*&#x200B;の&#x200B;**[!UICONTROL Shopping Cart]** セクションにバンドルと設定可能な製品数量が正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-65822です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルと設定可能な製品数量が、*[!UICONTROL Customer's Activities]*&#x200B;の&#x200B;**[!UICONTROL Shopping Cart]** セクションに正しく表示されません。

<u>複製する手順</u>:

1. ストアフロントでユーザーを作成する。
2. 管理パネルで&#x200B;**[!UICONTROL Bundle product]**&#x200B;を作成します。
3. ストアフロントで、ログインユーザーとして、指定した数量のバンドル商品をショッピングカートに追加します。
4. *管理者* パネルで、**[!UICONTROL Customers]**&#x200B;に移動し、手順1で作成した顧客の&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックします。
5. **[!UICONTROL Create Order]**&#x200B;をクリックします。
6. 左側の&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;の下にある「**[!UICONTROL Shopping Cart]**」セクションを確認します。 選択した数量と一緒にバンドル製品が表示されます。

<u>期待される結果</u>:

バンドルアイテムの数量は、ストアフロントに表示されている数量と一致する必要があります。

<u>実際の結果</u>:

バンドル品目数量は0として表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
