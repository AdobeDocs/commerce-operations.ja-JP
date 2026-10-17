---
title: 'MDVA-42410: クーポンレポートにデフォルトの基本通貨のみが表示される'
description: MDVA-42410 パッチは、クーポンレポートで基本通貨のみが表示される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-42410です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Orders
role: Admin
exl-id: 97b4d9cf-12fd-4659-ad71-914c8422da37
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%
---
# MDVA-42410: クーポンレポートにデフォルトの基本通貨のみが表示される

MDVA-42410 パッチは、クーポンレポートで基本通貨のみが表示される問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-42410です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クーポンレポートには、デフォルトの基本通貨のみが表示されます。

<u>複製する手順</u>:

1. 追加のWeb サイト、ストアビュー、ストアビューを作成します。
1. 新しいweb サイトに別の通貨を設定します。 例えば、ユーロ。
1. **店舗** > **通貨レート**&#x200B;に移動し、通貨レートを&#x200B;**ユーロ**&#x200B;に設定します。
1. 特定のクーポンを含む&#x200B;**買い物かご価格ルール**&#x200B;を作成 – **テスト**。
1. フロントエンドに移動し、新しいweb サイトで&#x200B;**Test** クーポンを使用して注文します。
1. **Reports** > **Sales** > **Coupons**&#x200B;に移動します。
1. 範囲ドロップダウンで新しいweb サイトを選択します。
1. 統計を更新してレポートを実行します。

<u>期待される結果</u>:

クーポンレポートでは、新しいweb サイトの通貨がユーロとして表示されます。

<u>実際の結果</u>:

新しいweb サイトのクーポンレポートでは、デフォルトの基本通貨（この場合はUSD）が使用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
