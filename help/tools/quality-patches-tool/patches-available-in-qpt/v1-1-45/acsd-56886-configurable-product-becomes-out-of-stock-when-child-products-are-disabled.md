---
title: ACSD-56886：子商品が無効になっている場合、設定可能な商品が在庫切れになる
description: ACSD-56886 パッチを適用して、製品が無効になっている場合に設定可能な製品が在庫切れになるAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-56886：子商品が無効になっている場合、設定可能な商品が在庫切れになる

ACSD-56886 パッチは、子製品が無効になっている場合に設定可能な製品が在庫切れになる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-56886です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

子商品が無効になっている場合、コンフィグ可能な商品は在庫切れになります。

<u>複製する手順</u>:

1. 管理者としてログインします。
1. **[!UICONTROL Update By Schedule]** モードですべてのインデクサーを設定します。
1. 次の設定可能な製品を作成します。

   * 名前= *構成可能なテスト 1*
   * 属性= *color*
   * 値= *赤*&#x200B;と&#x200B;*黒*
   * **red**&#x200B;子商品の価格= *$100*;
   * 「ブラック」子商品の価格= *$200*。

1. 設定可能な製品に対して、次のスケジュールされた更新を作成します。

   * 開始日= *3*&#x200B;分後。
   * 終了日= *開始日から*&#x200B;分後。
   * 製品名= *TEST CONFIGURABLE 1 edited*.
   * **設定可能** セクションの&#x200B;**red**&#x200B;子製品を無効にします。

1. 開始日を待ちます。
1. ストアフロントで設定可能な製品の詳細を開きます。

<u>期待される結果</u>:

設定可能な商品は、**のラベルが200**&#x200B;の低いStock **に**&#x200B;と表示されます。

<u>実際の結果</u>:

設定可能な製品は&#x200B;**在庫切れ**&#x200B;と表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
