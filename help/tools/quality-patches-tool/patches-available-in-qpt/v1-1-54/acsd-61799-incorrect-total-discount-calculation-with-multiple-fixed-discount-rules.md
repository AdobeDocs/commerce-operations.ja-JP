---
title: ACSD-61799：見積に適用された複数の固定割引カート ルールの合計割引の計算が正しくありません
description: ACSD-61799 パッチを適用して、Adobe Commerceの問題を修正します。この問題では、固定割引を含む複数の買い物かごのルールが見積もりに適用される場合、合計割引が誤って計算されます。
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-61799：見積に適用された複数の固定割引カート ルールの合計割引の計算が正しくありません

ACSD-61799 パッチは、固定割引を含む複数のカートルールが見積もりに適用される場合に、合計割引が誤って計算される問題を解決または修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61799です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Fixed amount discount for the whole cart]*&#x200B;を含む複数の買い物かごに適用すると、合計割引が誤って計算されます。

<u>複製する手順</u>:

1. 1000 ドルの価格で4つの商品を作成します。
1. 買い物かご全体に100 ドルの割引を提供する条件を設けずに、3つの買い物かご価格ルールを作成します。
1. 別のカート価格ルールを作成して、カート全体に100 ドルの割引を提供し、ルールの適用を妨げる条件を指定します。
1. ルールを無効にします。
1. ショッピングカートに3つの商品を追加し、カート内の割引を観察します。
1. カートに商品を追加し、カート内の割引を観察します。
1. 無効なカート価格ルールを有効にします。
1. ショッピングカートページを更新し、カート内の割引を観察します。

<u>期待される結果</u>:

1. カートに商品を追加しても、割引の額は変わりません。
1. 適用されない条件でカート価格ルールを有効にしても、割引額は変更されません。

<u>実際の結果</u>:

1. カートに商品を追加すると、割引の額が変更されます。
1. 適用されない条件でカート価格ルールを有効にすると、割引額が変更されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
