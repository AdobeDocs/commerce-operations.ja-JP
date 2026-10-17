---
title: ACSD-45255：制限付き管理者ユーザーの低在庫報告書ページの例外
description: ACSD-45255 パッチは、制限付き管理者ユーザーのLow Stock レポートページで例外がスローされる問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-45255です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Admin Workspace, Orders
role: Admin
exl-id: bf7e0893-e4a7-4184-a223-02ceef7a30d9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%
---
# ACSD-45255：制限付き管理者ユーザーの低在庫報告書ページの例外

ACSD-45255 パッチは、制限付き管理者ユーザーのLow Stock レポートページで例外がスローされる問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-45255です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.5

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限された管理者ユーザーの場合、低在庫報告書ページに例外がスローされます。

<u>前提条件</u>:

* 在庫モジュールが有効になっています。
* web サイト、実店舗、店舗表示を追加します。
* 追加のweb サイトのみにアクセスできる制限付き管理者ユーザーがあります。

<u>複製する手順</u>:

1. 制限付き管理者ユーザーとしてCommerce管理者を開きます。
1. **レポート** > **製品** > **低在庫**&#x200B;に移動します。

<u>期待される結果</u>:

制限付き管理者ユーザーに対して、低ストックレポートが表示されます。

<u>実際の結果</u>:

例外がスローされます。

```shell
TypeError: Argument 1 passed to Magento\InventoryLowQuantityNotification\Model\ResourceModel\LowQuantityCollection\Interceptor::addStoreFilter() must be of the type int, array given, called in ../app/code/Magento/AdminGws/Plugin/CollectionFilter.php on line 101 and defined in ../generated/code/Magento/InventoryLowQuantityNotification/Model/ResourceModel/LowQuantityCollection/Interceptor.php:20
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
