---
title: 'ACSD-51884: 「サイズ変更」コマンドで製品イメージのキャッシュパスが正しくない'
description: 「サイズ変更」コマンドを実行した後にproduct image cache pathが正しくなくなるというAdobe Commerceの問題を修正するには、ACSD-51884 パッチを適用します。
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-51884: 「サイズ変更」コマンドで製品イメージのキャッシュパスが正しくない

ACSD-51884 パッチでは、resize コマンドの実行後に製品イメージのキャッシュパスが正しくないという内部エラーが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-51884です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「サイズ変更」コマンドで、製品イメージのキャッシュパスが正しくなくなる。

<u>複製する手順</u>:

1. 新しいweb サイト/ストア/ストアビューを作成。
1. 商品を作成し、両方のweb サイトに割り当てて、商品画像をアップロードします。
1. 新しいテーマを作成します（添付のAdobe.zipを参照）。
1. `app/design/Adobe/theme/etc/view.xml`変更時：

```xml
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

へ

```xml
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. 以前に作成したストアビューにテーマを適用します。
1. 2nd サイトの商品ページをご覧ください。 製品画像が正しく表示されます。
1. フラッシュキャッシュを使用：
   `bin/magento cache:flush`
1. 2nd サイトの商品ページをご覧ください。

<u>期待される結果</u>:

製品画像が正しく表示されます。

<u>実際の結果</u>:

製品画像が存在しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
