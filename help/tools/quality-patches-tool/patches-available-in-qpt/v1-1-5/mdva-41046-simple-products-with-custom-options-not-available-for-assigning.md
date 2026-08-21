---
title: MDVA-41046：割り当てに使用できないカスタムオプションを含むシンプルな製品
description: MDVA-41046 パッチは、カスタムオプションを持つシンプルな製品が、設定可能な製品やグループ化された製品への割り当てに使用できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-41046です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-41046：割り当てに使用できないカスタムオプションを含むシンプルな製品

MDVA-41046 パッチは、カスタムオプションを持つシンプルな製品が、設定可能な製品やグループ化された製品への割り当てに使用できない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-41046です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタムオプションを持つシンプルな製品は、設定可能/グループ化された製品に割り当てることはできません。

<u>複製する手順</u>:

1. カスタマイズ可能なオプションを使用してシンプルな製品を作成し、設定可能な属性の値を設定します。
   * 設定可能な属性として&#x200B;*Color*&#x200B;を使用し、カラー値として&#x200B;*Yellow*&#x200B;を選択します。
1. 単純な製品を保存します。
1. 次に、設定可能な製品の作成ページに移動します。
1. 「設定を作成」ウィザードを開き、属性カラーとして&#x200B;*Yellow*&#x200B;を選択します。
1. 設定可能な製品を保存せずに、「選択」ドロップダウンから「別の製品を選択」オプションを選択します。
1. これにより、カラー属性の黄色でフィルタリングされた商品グリッドが開きます。 次に、以前にカスタマイズ可能なオプションで作成したシンプルな製品を選択します。
1. 設定可能な製品を保存します。

<u>期待される結果</u>:

カスタムオプションを含むシンプルな製品は、手順6で割り当て（グリッドに表示）できます。

<u>実際の結果</u>:

設定セクションが空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
