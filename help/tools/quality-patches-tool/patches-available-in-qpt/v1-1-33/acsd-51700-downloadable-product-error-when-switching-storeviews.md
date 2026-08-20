---
title: ACSD-51700：ダウンロード可能な製品編集ページでストアビューの切り替えエラーが発生する
description: 管理者でダウンロード可能な商品編集ページでストアビューを切り替える際にエラーが発生するAdobe Commerceの問題を修正するには、ACSD-51700 パッチを適用します。
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-51700：ダウンロード可能な製品編集ページでストアビューの切り替えエラーが発生する

ACSD-51700 パッチは、管理者でダウンロード可能な製品編集ページでストアビューを切り替える際にエラーが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51700です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

## イシュー

管理画面でダウンロード可能な製品編集ページのストアビューを切り替えると、エラーが発生します。

<u>複製する手順</u>:

1. 名前、[!DNL SKU]、価格を使用してダウンロード可能な製品を作成します。 リンクを追加せず、商品を保存してください。
1. すべてのストアビューからデフォルトのストアビューに切り替えます。
1. ダウンロード可能な製品のリンクを作成し、保存します。
1. デフォルトのストアビューからすべてのストアビューに切り替えます。

<u>期待される結果</u>:

リンクされた製品が表示されます。

<u>実際の結果</u>:

次のエラーが表示されます。

*非推奨の機能：number_format （）: float タイプのパラメーター#1 （$num）にnullを渡すことは、vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.phpの228*&#x200B;行目で非推奨です

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
