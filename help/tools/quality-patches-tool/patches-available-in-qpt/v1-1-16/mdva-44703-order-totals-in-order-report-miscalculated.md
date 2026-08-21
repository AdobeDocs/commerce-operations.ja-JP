---
title: MDVA-44703：注文レポートの注文合計が誤計算される
description: MDVA-44703 パッチは、制限された管理者ユーザーに対して注文レポートの注文合計が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16がインストールされている場合に利用できます。 パッチ IDはMDVA-44703です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-44703：注文レポートの注文合計が誤計算される

MDVA-44703 パッチは、制限された管理者ユーザーに対して注文レポートの注文合計が誤って計算される問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16がインストールされている場合に使用できます。 パッチ IDはMDVA-44703です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文レポートの注文合計は、制限付き管理者ユーザーに対して計算が誤っています。

<u>複製する手順</u>:

1. 2つのストアを持つ追加のweb サイトを作成します。
1. 新しいweb サイトのみにアクセスできる制限付き管理者ユーザーを作成します。
1. 制限付き管理者ユーザーとしてログインします。
1. 合計が異なる2つの注文（新しい店舗ごとに1つ）を作成します。
1. 注文の請求書を作成します。
1. **Reports** > **Sales**&#x200B;に移動し、**Orders レポート**&#x200B;を開きます。
1. 統計を更新します。
1. 各店舗のレポートをご覧ください。

<u>期待される結果</u>:

売上合計は各店舗の注文額に対応します。

<u>実際の結果</u>:

各ストアには、web サイト全体の総売上合計が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
