---
title: MDVA-42507：買い物かごルールのステージング更新を適用した後、ページ全体のキャッシュがクリーニングされる
description: MDVA-42507 パッチは、カートルールのステージング更新を適用した後にフルページキャッシュがクリーニングされる問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-42507です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
exl-id: 19f61e31-67da-4bd6-bce7-a9250f3946c7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-42507：買い物かごルールのステージング更新を適用した後、ページ全体のキャッシュがクリーニングされる

MDVA-42507 パッチは、カートルールのステージング更新を適用した後にフルページキャッシュがクリーニングされる問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-42507です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カートルールのステージング更新を適用した後、ページ全体のキャッシュがクリーニングされます。

<u>複製する手順</u>:

1. 開発者モードを有効にします。
1. 複数の製品とカテゴリーページを開き、（ヘッダーを介して）キャッシュから読み込まれることを確認します。
1. 買い物かごルールのステージング更新を適用します。
1. カテゴリおよび製品ページがキャッシュから読み込まれるかどうかを確認します。

<u>期待される結果</u>:

カートルールのステージング更新を適用した後、ページ全体のキャッシュがクリーニングされない。

<u>実際の結果</u>:

カートルールのステージング更新を適用した後、フルページキャッシュがクリーニングされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
