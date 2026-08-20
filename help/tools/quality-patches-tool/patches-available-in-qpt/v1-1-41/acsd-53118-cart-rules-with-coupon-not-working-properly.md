---
title: 'ACSD-53118: クーポンが正しく機能しない買い物かごのルール'
description: ACSD-53118 パッチを適用して、カート内の商品に一致する属性が空の場合にクーポンコードを使用してカート価格ルールが適用されるAdobe Commerceの問題を修正します。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 8957790e-c22b-4a25-939b-94d7a9fb1cc7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-53118: クーポンが正しく機能しない買い物かごのルール

ACSD-53118 パッチでは、カート内の商品に空のマッチング属性がある場合に、クーポンコードを使用してカート価格ルールが適用される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-53118です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カートの価格ルールは、クーポンコードを使用して適用されますが、カート内の商品には空のマッチング属性があります。

<u>複製する手順</u>:

1. 価格属性を作成し、属性セットに追加します。 プロモーションルール条件で属性を使用できるようにします。
1. 製品を作成し、新しい属性を空のままにします。
1. 特定のクーポンと次の条件を使用して、カート価格ルールを作成します。

   * 買い物かごに商品が見つかった場合、すべての条件がtrueです。属性1は0です。

1. 手順2で作成した商品をカートに追加します。
1. 手順3で作成したカートルールのクーポンコードを使用します。

<u>期待される結果</u>:

ショッピングカートに割引は適用されません。

<u>実際の結果</u>:

ショッピングカートに割引が適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
