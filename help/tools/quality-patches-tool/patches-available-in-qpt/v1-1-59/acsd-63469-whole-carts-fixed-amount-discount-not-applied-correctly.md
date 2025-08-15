---
title: ACSD-63469：複数のルールで固定金額の買い物かごの割引が正しく適用されない
description: 複数のルールが適用されている場合に、買い物かご全体に対する固定金額の割引が適切に適用されないAdobe Commerceの問題を修正するために、ACSD-63469 パッチを適用してください。
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-63469：複数のルールで固定金額の買い物かごの割引が正しく適用されない

ACSD-63469 パッチは、複数のルールが適用されている場合に、買い物かご全体に対する固定金額の割引が適切に適用されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-63469 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数の **[!UICONTROL Fixed amount discount for whole cart]** ルールが同時に適用され、製品に割引または特別価格が設定されている場合、割引値が正しく計算されません。

<u> 再現手順 </u>:

1. 850 ドルと 85 ドルの価格の 2 つの製品を作成し、それぞれ 765 ドルと 68 ドルに特別価格を設定します。
1. 次のように 2 つの **[!UICONTROL Cart Price Rules]** を作成します。
   * ルール 1
      * **[!UICONTROL Conditions]**: $850 製品の場合、*数量* を *等しいか、または 2 より大きい* に設定
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**$153 *中* 件を適用する
   * ルール 2
      * **[!UICONTROL Conditions]**: $85 製品の場合、*数量* を *等しいか、または 2 より大きい* に設定します
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**$14 *中* 件に適用する
1. 両方の商品を買い物かごに追加します。それぞれの商品の数量は 2 です。

<u> 期待される結果 </u>:

買い物かごに適用される割引は 167 ドルです。

<u> 実際の結果 </u>:

買い物かごに適用される割引は 41 ドルです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## パッチのインストール後に必要な追加手順

（この節はオプションです。問題を修正するためにパッチを適用した後に必要な手順が含まれる場合があります）。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
