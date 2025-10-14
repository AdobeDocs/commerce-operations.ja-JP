---
title: MDVA-37897：最近表示された項目から製品を追加すると、リダイレクトが正しく表示されない
description: MDVA-37897 パッチを使用すると、最近表示された項目ウィジェットからオプションを含む製品を追加しようとすると、誤ったリダイレクトの問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.1 がインストールされている場合に利用できます。 パッチ ID は MDVA-37897。 この問題はAdobe Commerce バージョン 2.4.4 で修正される予定であることに注意してください。
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897：最近表示された項目から製品を追加すると、リダイレクトが正しく表示されない

MDVA-37897 パッチを使用すると、最近表示された項目ウィジェットからオプションを含む製品を追加しようとすると、誤ったリダイレクトの問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.1 がインストールされている場合に使用できます。 パッチ ID は MDVA-37897。 この問題はAdobe Commerce バージョン 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドインフラストラクチャ 2.4.1 のAdobe Commerce

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.2-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーが「最近閲覧された項目」セクションから選択の必要なオプションを含む製品を追加しようとすると、ユーザーは製品の詳細ページではなく製品一覧ページにリダイレクトされます。

<u> 再現手順 </u>:

1. カスタマイズ可能なオプション（タイプ：ラジオボタン）を使用して、シンプルな製品を作成します。
1. 最近表示された項目ウィジェットを設定して、製品を表示します。
1. 最近表示されたウィジェットに表示されるように、カスタマイズ可能なオプションを持つ製品を訪問します。
1. 最近表示されたウィジェットのいずれかの製品で、「**買い物かごに追加**」をクリックします。

<u> 期待される結果 </u>:

製品の詳細ページにリダイレクトされて、オプションを選択できます。

<u> 実際の結果 </u>:

製品一覧ページにリダイレクトされます。

## パッチの適用

個々のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe Commerce オンプレミス：開発者向けドキュメントの [&#x200B; ソフトウェアアップデートガイド/パッチを適用する &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/usage)。
* アドビのクラウドインフラストラクチャでのAdobe Commerce：開発者向けドキュメントの [&#x200B; アップグレードとパッチ/パッチを適用 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 関連資料

Adobe Commerce用の高品質パッチの詳細については、次を参照してください。

* [&#x200B; 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) の節を参照してください。
