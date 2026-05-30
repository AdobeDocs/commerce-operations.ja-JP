---
title: MDVA-37725：デフォルト以外のサイトを介して送信されたメールに、デフォルトのサイトのロゴ URLが含まれる
description: MDVA-37725 パッチは、デフォルトのweb サイトのロゴ URLを含むデフォルト以外のweb サイトを介して非同期注文メールが送信される問題を修正します。
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-37725：デフォルト以外のサイトを介して送信されたメールに、デフォルトのサイトのロゴ URLが含まれる

>[!WARNING]
>
> MDVA-37725 パッチは非推奨です。

MDVA-37725 パッチは、デフォルトのweb サイトのロゴ URLを含むデフォルト以外のweb サイトを介して非同期注文メールが送信される問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMDVA-37725です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

非同期注文メールは、デフォルトのweb サイトのロゴ URLを含むデフォルト以外のweb サイトを介して送信されます。

<u>前提条件</u>:

1. 2つ目のweb サイト/ストア/ストアビューを作成する必要があります。
1. **非同期送信**&#x200B;設定は、**ストア** > **設定** > **設定** > **セールス** > **セールスメール** > **一般設定**&#x200B;から有効にする必要があります。
1. **URLにストアコードを追加**&#x200B;設定が有効になっており、セカンダリ web サイトへのアクセスが&#x200B;**Stores** > **Settings** > **Configuration** > **URL オプション**&#x200B;から簡単になります。

<u>複製する手順</u>:

1. 1号店と2号店の両方から注文します。
1. cronを実行してセールスメールを送信します。
1. 2番目のWeb サイトからのメールを確認します。

<u>期待される結果</u>:

メールのロゴ URLには、2番目のweb サイトのURLが含まれています。

<u>実際の結果</u>:

メールのロゴ URLには、デフォルトのweb サイトのURLが含まれています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な パッチ」セクションを参照してください。
