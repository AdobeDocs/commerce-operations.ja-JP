---
title: ACSD-48210：ストアビュー固有のスコープ属性がグローバル値を上書きする
description: ACSD-48210 パッチを適用して、特定のストアビューで*[!UICONTROL Website Scope]*属性を更新するAdobe Commerceの問題を修正し、グローバルスコープの属性値を上書きします。
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '433'
ht-degree: 0%
---
# ACSD-48210：ストアビュー固有のスコープ属性がグローバル値を上書きする

ACSD-48210 パッチでは、特定のストアビュー内の&#x200B;*[!UICONTROL Website Scope]*&#x200B;属性を更新すると、グローバルスコープ内の属性値が上書きされる問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-48210です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定のストアビュー内の&#x200B;*[!UICONTROL Website Scope]*&#x200B;属性を更新すると、グローバルスコープの属性値が上書きされます。

同じ`SKU`と`store_view_code`を共有する複数の行を持つ製品価格を読み込むと、*[!UICONTROL All Store View]*&#x200B;および&#x200B;*[!UICONTROL Default Store]*&#x200B;の範囲の価格が誤って更新される原因が生じました。 特定のストアビューでweb サイトスコープ属性を変更しても、グローバルスコープ内の属性の値が上書きされなくなりました。
<u>複製する手順</u>:

1. *[!UICONTROL Catalog Price Scope]*&#x200B;を&#x200B;*[!UICONTROL Website]*&#x200B;に設定します。
1. *SP01*&#x200B;という名前のシンプルな製品を作成し、価格を&#x200B;*$84.50*&#x200B;に設定します。
1. 以下のCSVを使用して製品を読み込みます。

   ```text
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. *[!UICONTROL All Store View]*&#x200B;および&#x200B;*[!UICONTROL Default Store]*&#x200B;の範囲で製品価格を確認してください。

<u>期待される結果</u>:

* 最初の空でない値は、*[!UICONTROL Default Store]* スコープに使用されます。
* *[!UICONTROL All Store View]*&#x200B;の範囲は変更されません。

<u>実際の結果</u>:

* *[!UICONTROL All Store View]*&#x200B;のスコープ価格が&#x200B;*$86.59*&#x200B;に変更されます。
* *[!UICONTROL Default Store]*&#x200B;のスコープ価格が&#x200B;*$86.59*&#x200B;に変更されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
