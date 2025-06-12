---
title: ACSD-45255：制限付き管理者ユーザーに対する低在庫レポートページの例外
description: ACSD-45255 パッチを使用すると、制限付き管理者ユーザーの低在庫のレポート ページで例外がスローされる問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18 がインストールされている場合に利用できます。 パッチ ID は ACSD-45255 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Admin Workspace, Orders
role: Admin
exl-id: bf7e0893-e4a7-4184-a223-02ceef7a30d9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-45255：制限付き管理者ユーザーに対する低在庫レポートページの例外

ACSD-45255 パッチを使用すると、制限付き管理者ユーザーの低在庫のレポート ページで例外がスローされる問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.18 がインストールされている場合に使用できます。 パッチ ID は ACSD-45255 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.5

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付き管理者ユーザーに対して、低在庫のレポート ページで例外がスローされる。

<u> 前提条件 </u>:

* インベントリモジュールが有効になります。
* 追加の web サイト、ストア、ストア表示があります。
* 追加の web サイトにのみアクセスできる制限付き管理者ユーザーが存在します。

<u> 再現手順 </u>:

1. Commerce Admin を制限付き管理者ユーザーとして開きます。
1. **レポート**/**製品**/**低在庫** に移動します。

<u> 期待される結果 </u>:

制限付き管理者ユーザーについて、低在庫レポートが表示されます。

<u> 実際の結果 </u>:

例外がスローされます。

```bash
TypeError: Argument 1 passed to Magento\InventoryLowQuantityNotification\Model\ResourceModel\LowQuantityCollection\Interceptor::addStoreFilter() must be of the type int, array given, called in ../app/code/Magento/AdminGws/Plugin/CollectionFilter.php on line 101 and defined in ../generated/code/Magento/InventoryLowQuantityNotification/Model/ResourceModel/LowQuantityCollection/Interceptor.php:20
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
