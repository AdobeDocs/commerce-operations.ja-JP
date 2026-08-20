---
title: MDVA-42584：設定可能な製品の在庫ステータスが自動的に更新されない
description: MDVA-42584 パッチは、コンフィグ可能な製品の在庫状況が、シンプルな製品の更新時に自動的に更新されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10がインストールされている場合に利用できます。 パッチ IDはMDVA-42584です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# MDVA-42584：設定可能な製品の在庫ステータスが自動的に更新されない

MDVA-42584 パッチは、コンフィグ可能な製品の在庫状況が、シンプルな製品の更新時に自動的に更新されない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10がインストールされている場合に使用できます。 パッチ IDはMDVA-42584です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バックエンドの設定可能な製品の在庫ステータスは、APIまたはインポートを通じて&#x200B;**In Stock**&#x200B;に設定されている場合、自動的に更新されません。

<u>前提条件</u>:

MSIをインストールしました。

<u>複製する手順</u>:

1. 設定可能な製品&#x200B;**InvCheck001**&#x200B;を作成し、2つのオプションを指定します：**InvCheck001-M**&#x200B;と&#x200B;**InvCheck001-L**。
1. シンプルな商品の両方に数量があり、設定可能な商品がバックエンドの&#x200B;**In Stock**&#x200B;になるように、**In Stock**&#x200B;である必要があります。
1. 次に、シンプルな商品の両方を更新し、数量を&#x200B;**0**&#x200B;に、在庫ステータスを&#x200B;**在庫切れ**&#x200B;に設定します。
1. 設定可能な製品を更新し、在庫状況が&#x200B;**在庫切れ**&#x200B;に更新されていることを確認します。
1. 次のAPI エンドポイントを使用し、数量が0を超える単純な製品&#x200B;**InvCheck001-M**&#x200B;を&#x200B;**In Stock**&#x200B;に設定します。

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. バックエンドに移動し、シンプルな製品&#x200B;**InvCheck001-M**&#x200B;の数量と在庫ステータスを確認します。**在庫**&#x200B;に更新されます。
1. 設定可能な商品を更新して、在庫状況を確認します。

<u>期待される結果</u>:

バックエンドの設定可能な製品&#x200B;**InvCheck001**&#x200B;の在庫ステータスは、自動的に&#x200B;**In Stock**&#x200B;に更新されます。

<u>実際の結果</u>:

設定可能な製品の在庫ステータスはまだ&#x200B;**在庫切れ**&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
