---
title: ACSD-56546：設定可能なバンドル商品が、ストアフロントに在庫切れとして表示される
description: 「*[!UICONTROL Display Out of Stock Products]*」設定オプションが無効になっている場合に、コンフィギュラブルおよびバンドル製品がストアフロントで在庫切れとして表示されるAdobe Commerceの問題を修正するには、ACSD-56546 パッチを適用します。
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '454'
ht-degree: 0%
---
# ACSD-56546：設定可能なバンドル商品が、ストアフロントに在庫切れとして表示される

ACSD-56546 パッチは、設定可能なバンドル製品がストアフロントで在庫切れとして表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-56546です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Display Out of Stock Products]* オプションが無効になっている場合、コンフィグ可能な商品およびバンドル商品はストアフロントで在庫切れとして表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Display Out of Stock Products]** オプションを&#x200B;*No*&#x200B;に設定します。
1. web サイト、実店舗、ストアビューの作成。
1. ソースと在庫を作成し、それを2番目のweb サイトに割り当てます。
1. 2つの子製品を含む&#x200B;*設定可能な製品*&#x200B;を作成します。 両方のソースと両方のweb サイトに子製品を割り当てます。
1. 両方のソースで&#x200B;*qty=0*&#x200B;を持つように、最初の子製品を更新します。
1. 2番目の子製品を更新し、2番目のweb サイトで無効にします。
1. 完全にインデックス再作成を行います。
1. 2番目のweb サイトの設定可能な製品を含むカテゴリを確認します。

<u>期待される結果</u>:

在庫切れの設定可能な商品は、ストアフロントには表示されません。

<u>実際の結果</u>:

*[!UICONTROL Display Out of Stock Products]* オプションが無効になっている場合でも、在庫切れの設定可能な商品はストアフロントに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
