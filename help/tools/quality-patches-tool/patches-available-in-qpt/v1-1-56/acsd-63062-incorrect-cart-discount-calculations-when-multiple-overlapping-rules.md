---
title: ACSD-63062：複数の重複するルールがある、買い物かごの割引計算が正しくない
description: 複数の重複するルールが適用されている場合に、誤った買い物かごの割引計算が発生するAdobe Commerceの問題を修正するために、ACSD-63062 パッチを適用します。
feature: Price Rules
role: Admin, Developer
exl-id: c4a93063-b640-444e-ba0e-552dd8d1895b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062：複数の重複するルールがある、買い物かごの割引計算が正しくない

ACSD-63062 パッチは、複数の重複するルールが適用されている場合に、誤った買い物かご割引計算が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-63062 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数の重複するルールが適用されると、買い物かごの割引計算が正しく行われません。

<u> 再現手順 </u>:

1. サンプルデータを含んだ新しいインスタンスをインストールします。
1. 次の 3 つのシンプルな製品を作成します。

   * simple1: $1080
   * simple2: $260
   * simple3:280 ドル

1. 次のように 4 つの *[!UICONTROL Cart Price Rules]* を作成します。

   * ルール 1:

      * *[!UICONTROL Priority]*: 100
      * *[!UICONTROL Conditions]* タブ：合計数量が 3 以上の場合は、simple2 （$280）製品を使用
      * 「*[!UICONTROL Actions]*」タブ：SKU は simple2 です
      * *[!UICONTROL Fixed Amount Discount]*: 80 ドル

   * ルール 2:

      * *[!UICONTROL Priority]*: 200
      * 「*[!UICONTROL Actions]*」タブ：SKU は simple2 です
      * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * ルール 3:

      * *[!UICONTROL Priority]*: 300
      * *[!UICONTROL Conditions]* タブ：小計が$1000 以上
      * 買い物かご全体の *[!UICONTROL Fixed Amount Discount]* ール：100 ドル

   * ルール 4:

      * *[!UICONTROL Priority]*: 400
      * *[!UICONTROL Conditions]* タブ：合計数量が 2 以上の場合は、simple1 （$1080）製品を使用
      * 「*[!UICONTROL Actions]*」タブ：SKU は simple1
      * 買い物かご全体の *[!UICONTROL Fixed Amount Discount]*: 960 ドル

1. ストアフロントに移動し、指定された数量の次の製品を買い物かごに追加します。

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. 買い物かごを確認します。

<u> 期待される結果 </u>:

適用される割引は$1352 です。

<u> 実際の結果 </u>:

適用される割引は$1525.33 です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
