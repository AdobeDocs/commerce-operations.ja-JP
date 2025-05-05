---
title: 「ACSD-61799：見積もりに複数の固定割引買い物かごルールが適用された、誤った合計割引計算」
description: ACSD-61799 パッチを適用すると、固定割引が適用された複数の買い物かごルールが見積もりに適用された場合に、合計割引が正しく計算されないAdobe Commerceの問題を修正できます。
feature: Price Rules
role: Admin, Developer
source-git-commit: 0b4c46e0db3dbd7ce5914490ae20471709be261d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# ACSD-61799：見積もりに複数の固定割引買い物かごルールが適用された、誤った合計割引計算

ACSD-61799 パッチを適用すると、割引が固定された複数の買い物かごルールが見積もりに適用された際に、合計割引が正しく計算されない問題を解決または修正できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61799 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Fixed amount discount for the whole cart]* を含む複数の買い物かごルールが買い物かごに適用される場合、合計割引率が正しく計算されません。

<u> 再現手順 </u>:

1. 1000 ドルの価格で 4 つの製品を作成します。
1. 条件を設定せずに 3 つの買い物かご価格ルールを作成すると、買い物かご全体に対して$100 の割引が適用されます。
1. ルールが適用されない条件を持つ、買い物かご全体に対して$100 の割引を与える別の買い物かご価格ルールを作成します。
1. ルールを無効にします。
1. 買い物かごに 3 つの製品を追加し、買い物かごでの割引を確認します。
1. 買い物かごに製品を追加し、買い物かごでの割引を確認します。
1. 無効な買い物かご価格ルールを有効にします。
1. 買い物かごページを更新し、買い物かご内の割引を確認します。

<u> 期待される結果 </u>:

1. 買い物かごに製品を追加しても、割引額は変更されません。
1. 適用されない条件で買い物かご価格ルールを有効にしても、割引額は変更されません。

<u> 実際の結果 </u>:

1. 買い物かごに製品を追加すると、割引額が変更されます。
1. 適用されない条件で買い物かご価格ルールを有効にすると、割引額が変更されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。

