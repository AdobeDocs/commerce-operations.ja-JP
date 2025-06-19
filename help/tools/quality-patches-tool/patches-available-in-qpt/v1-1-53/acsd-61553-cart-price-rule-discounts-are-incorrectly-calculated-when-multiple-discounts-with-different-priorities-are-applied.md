---
title: ACSD-61553：優先度の異なる複数の割引が適用されている場合、[!UICONTROL Cart Price Rule] が正しく計算されません
description: 優先度が異なる複数のディスカウントが適用される場合に [!UICONTROL Cart Price Rule] が正しく計算されないAdobe Commerceの問題を解決するには、ACSD-61553 パッチを適用してください。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553：優先度の異なる複数の割引が適用されている場合、[!UICONTROL Cart Price Rule] が正しく計算されません

ACSD-61553 パッチは、優先度が異なる複数のディスカウントが適用された場合に、[!UICONTROL Cart Price Rule] が正しく計算されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-61553 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

異なる優先度の複数の割引が適用されている場合、[!UICONTROL Cart Price Rule] が正しく計算されません。

<u> 再現手順 </u>:

1. 9,000 ドルの価格でシンプルな製品を作成します。
1. 条件を指定せずに、後続のルールを破棄せずに、$700 の固定値引を持つ [!UICONTROL Cart Price Rule]：ルール A を作成します。
1. 別のルー [!UICONTROL Cart Price Rule] を作成します。条件を指定せず、後続のルールを破棄せずに、$1000 の固定値引を持つルール B を作成します。
1. 数量 13 の製品を買い物かごに追加します。
1. 次のいずれかのシナリオでルールを更新します。

   シナリオ 01

        ルール A
        優先度：1
        最大数量割引が適用される対象：1
       
        ルール B
        優先度：0
        最大数量割引が適用される対象：0
   
   シナリオ 02

        ルール A
        優先度：0
        最大数量割引が適用される対象：0
       
        ルール B
        優先度：1
        最大数量割引が適用される対象：1
   
   シナリオ 03

        ルール A
        優先度：0
        最大数量割引が適用される対象：0
       
        ルール B
        優先度：0
        最大数量割引が適用される対象：1
   
1. 「**[!UICONTROL Update Shopping Cart]**」ボタンをクリックして、割引を再計算します。

<u> 期待される結果 </u>:

様々なシナリオで次の割引合計が表示されます。

     シナリオ 01: $13,700
     シナリオ 02: $10,100
     シナリオ 03: $10,100

<u> 実際の結果 </u>:

3 つのシナリオすべてで、合計割引額は 9,000 ドルです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
