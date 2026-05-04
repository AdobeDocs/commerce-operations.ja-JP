---
title: 'ACSD-60816: [!DNL New Relic] APM エージェントによって挿入されたブラウザー監視スクリプトがCSPに準拠していません'
description: ACSD-60816 パッチを適用して、APM エージェントによって挿入された [!DNL New Relic]  ブラウザーモニタリングスクリプトがContent Security Policy （CSP）に準拠しておらず、実行が妨げられるAdobe Commerceの問題を修正します。
feature: Tools and External Services, Checkout
role: Admin, Developer
exl-id: d03c25e0-ed25-4877-8470-737d3499473f
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-60816: APM エージェントによって挿入された[!DNL New Relic] ブラウザー監視スクリプトがCSPに準拠していません

ACSD-60816 パッチは、APM エージェントによって挿入された[!DNL New Relic] ブラウザー監視スクリプトがコンテンツセキュリティポリシー（CSP）に準拠していない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-60816です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

APM エージェントによって挿入された[!DNL New Relic] ブラウザー監視スクリプトは、CSPに準拠していません。

<u>複製する手順</u>:

1. 商品をカートに入れる。
1. 決済プロセスを見る。

<u>期待される結果</u>:

開発者コンソールにCSP エラーがありません。

<u>実際の結果</u>:

次のエラーが表示されます。

```text
Content-Security-Policy: The page's settings blocked an inline script (script-src-elem) from being executed because it violates the following directive: "script-src 
...
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
