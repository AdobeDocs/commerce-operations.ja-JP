---
title: ACSD-63062：複数のルールが重複するカート割引の計算が正しくない
description: 複数の重複ルールが適用される場合にカート割引の計算が間違って発生するAdobe Commerceの問題を修正するには、ACSD-63062 パッチを適用します。
feature: Price Rules
role: Admin, Developer
exl-id: c4a93063-b640-444e-ba0e-552dd8d1895b
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# ACSD-63062：複数のルールが重複するカート割引の計算が正しくない

ACSD-63062 パッチは、複数の重複ルールが適用される場合に誤ったカート割引の計算が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-63062です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数の重複するルールが適用されている場合、誤ったカート割引の計算が発生します。

<u>複製する手順</u>:

1. サンプルデータを使用して新しいインスタンスをインストールします。
1. シンプルな3つの商品を作成する：

   * simple1: $1080
   * simple2:260 ドル
   * simple3:280 ドル

1. 次のように4つの&#x200B;*[!UICONTROL Cart Price Rules]*&#x200B;を作成します。

   * ルール 1:

     * *[!UICONTROL Priority]*: 100
     * *[!UICONTROL Conditions]* タブ：合計数量が3以上の場合は、simple2 （$280）製品を使用します
     * *[!UICONTROL Actions]* タブ：SKUは単純です2
     * *[!UICONTROL Fixed Amount Discount]*: $80

   * ルール 2:

     * *[!UICONTROL Priority]*: 200
     * *[!UICONTROL Actions]* タブ：SKUは単純です2
     * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * ルール 3:

     * *[!UICONTROL Priority]*: 300
     * *[!UICONTROL Conditions]* タブ：小計が$1000以上である
     * 買い物かご全体の&#x200B;*[!UICONTROL Fixed Amount Discount]*: $100

   * ルール 4:

     * *[!UICONTROL Priority]*: 400
     * *[!UICONTROL Conditions]* タブ：合計数量が2より大きい場合は、simple1 （$1080）製品を使用します
     * *[!UICONTROL Actions]* タブ：SKUは単純です1
     * 買い物かご全体の&#x200B;*[!UICONTROL Fixed Amount Discount]*: $960

1. ストアフロントに移動し、特定の数量の次の商品をカートに追加します。

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. 買い物かごをチェック。

<u>期待される結果</u>:

適用される割引は1352 ドルです。

<u>実際の結果</u>:

適用される割引は$1525.33です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
