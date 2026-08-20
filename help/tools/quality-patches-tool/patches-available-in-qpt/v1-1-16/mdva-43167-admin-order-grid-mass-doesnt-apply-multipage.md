---
title: MDVA-43167：管理者注文グリッドのマス アクションが複数ページに適用されない
description: MDVA-43167 パッチでは、管理者ユーザーがすべての注文を選択した場合に、管理者の注文グリッドの一括処理がマルチページに適用されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16がインストールされている場合に利用できます。 パッチ IDはMDVA-43167です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Admin Workspace, Orders
role: Admin
exl-id: 992f8a90-300e-41aa-b03d-b8a647dddd51
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# MDVA-43167：管理者注文グリッドのマス アクションが複数ページに適用されない

MDVA-43167 パッチでは、管理者ユーザーがすべての注文を選択した場合に、管理者の注文グリッドの一括処理がマルチページに適用されない問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16がインストールされている場合に使用できます。 パッチ IDはMDVA-43167です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーがすべての注文を選択した場合、複数ページの管理者注文グリッドの一括処理は適用されません。

<u>複製する手順</u>:

1. 商品を3回購入すれば、3回の注文につながります。
1. **受注グリッド**&#x200B;に移動します。
1. ページネーションをカスタム値2に変更します。
1. 「すべて」を選択します。
1. 「**一括処理を保持**」を選択します。

<u>期待される結果</u>:

3つの注文はすべて保留になります。

<u>実際の結果</u>:

表示されている2つの注文のみが保留されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
