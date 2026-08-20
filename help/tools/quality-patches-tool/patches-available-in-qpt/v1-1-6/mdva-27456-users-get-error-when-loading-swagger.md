---
title: 'MDVA-27456: Swaggerの読み込み中にエラーが発生する'
description: MDVA-27456 パッチは、ユーザーがSwaggerを読み込もうとしたときにエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6がインストールされている場合に利用できます。 パッチ IDはMDVA-27456です。 この問題は、Adobe Commerce 2.3.7で修正されています。
feature: Tools and External Services
role: Admin
exl-id: a7d5dc7d-b916-4a09-9068-646f8474bba4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-27456: Swaggerの読み込み中にエラーが発生する

MDVA-27456 パッチは、ユーザーがSwaggerを読み込もうとしたときにエラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6がインストールされている場合に使用できます。 パッチ IDはMDVA-27456です。 この問題は、Adobe Commerce 2.3.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Swaggerの読み込み中にエラーが発生する。

<u>複製する手順</u>:

`../swagger.`に移動

<u>期待される結果</u>:

Swaggerはエラーなしで読み込まれます。

<u>実際の結果</u>:

ユーザーに次のエラーが表示されます：*API定義を読み込めませんでした*。 エラーログに含まれる内容：

*report.CRITICAL: レポート ID: webapi-5ea9c6da19cb1; メッセージ：「\DateTime」パラメーターのタイプが無効です。 パラメーターを確認して、もう一度やり直してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な[ パッチ」セクションを参照してください。
