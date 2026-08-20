---
title: 'MDVA-39993: APIを介して行われたインベントリの変更がストアフロントに反映されない'
description: MDVA-39993 パッチは、APIを介して行われたインベントリの変更がストアフロントに反映されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-39993です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-39993: APIを介して行われたインベントリの変更がストアフロントに反映されない

MDVA-39993 パッチは、APIを介して行われたインベントリの変更がストアフロントに反映されない問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-39993です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.5 - 2.3.7-p2、および2.4.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

APIを介して行われたインベントリの変更は、ストアフロントの製品ページには反映されません。

<u>前提条件</u>:

インベントリモジュールの取り付け：

<u>複製する手順</u>:

1. キューがcronで実行するように設定され、cronがインストールされて実行されていることを確認します。
1. 2色（黒と赤）と2 サイズ（MとL）の設定可能な製品（COC001）を作成します。
1. 1つのオプションを在庫切れにします（COC001-Red-M）。
1. ストアフロントで設定可能な商品ページを読み込み、各色をクリックしてみてください。 **Red**&#x200B;をクリックすると、サイズ **M**&#x200B;が在庫切れのため除外されます。
1. 次のAPI エンドポイントとペイロードを使用して、COC001-Red-Mの在庫を作成します。

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. バックエンドからこのシンプルな製品を確認し、それがIn Stockに更新されていることを確認します。
1. フロントエンドから設定可能な製品を読み込み、各カラーをクリックします。 **赤**&#x200B;をクリックすると、サイズ **M**&#x200B;に注意します。

<u>期待される結果</u>:

COC001-Red-M オプションは、APIを介してIn Stockに更新されたため、除外されません。

<u>実際の結果</u>:

COC001-Red-M オプションは、在庫があるにもかかわらず、引き続き除外されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
