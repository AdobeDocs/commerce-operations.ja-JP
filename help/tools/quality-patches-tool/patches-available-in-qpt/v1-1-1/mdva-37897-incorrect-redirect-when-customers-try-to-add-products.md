---
title: MDVA-37897：最近表示した商品を追加する際にリダイレクトが正しくない
description: MDVA-37897 パッチは、ユーザーが最近表示されたウィジェットからオプションを持つ製品を追加しようとすると、誤ったリダイレクトの問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.1がインストールされている場合に利用できます。 パッチ IDはMDVA-37897です。 この問題は、Adobe Commerce バージョン 2.4.4で修正される予定です。
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%
---
# MDVA-37897：最近表示した商品を追加する際にリダイレクトが正しくない

MDVA-37897 パッチは、ユーザーが最近表示されたウィジェットからオプションを持つ製品を追加しようとすると、誤ったリダイレクトの問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.1がインストールされている場合に使用できます。 パッチ IDはMDVA-37897です。 この問題は、Adobe Commerce バージョン 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce on our cloud infrastructure 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

選択する必要のあるオプションを持つ「最近閲覧した製品」セクションから製品を追加しようとすると、製品の詳細ページではなく、製品リストページにリダイレクトされます。

<u>複製する手順</u>:

1. カスタマイズ可能なオプション（タイプ：ラジオボタン）を使用してシンプルな製品を作成します。
1. 最近表示したウィジェットを設定して、製品を表示します。
1. カスタマイズ可能なオプションを備えた製品を、最近表示したウィジェットに表示します。
1. 最近閲覧したウィジェットの商品の1つに対して、**カートに追加**&#x200B;をクリックします。

<u>期待される結果</u>:

製品の詳細ページにリダイレクトされ、オプションを選択します。

<u>実際の結果</u>:

製品リストページにリダイレクトされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe Commerce オンプレミス：[&#x200B; ソフトウェア更新ガイド > パッチの適用](/help/tools/quality-patches-tool/usage.md)を開発者向けドキュメントでご覧ください。
* クラウドインフラストラクチャ上のAdobe Commerce: [&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)開発者向けドキュメントをご覧ください。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な パッチ」セクションを参照してください。
