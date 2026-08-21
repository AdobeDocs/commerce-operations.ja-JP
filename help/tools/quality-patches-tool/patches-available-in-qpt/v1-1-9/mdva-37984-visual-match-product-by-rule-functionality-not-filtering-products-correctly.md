---
title: MDVA-37984：ステージングの更新が適用されると、Visual Merchandiserが正しく機能しない
description: MDVA-37984 パッチは、ステージング更新が適用されたときにVisual Merchandiserの「Match product by rule」機能が製品を正しくフィルタリングしない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-37984です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-37984：ステージングの更新が適用されると、Visual Merchandiserが正しく機能しない

MDVA-37984 パッチは、ステージング更新が適用されたときにVisual Merchandiserの「Match product by rule」機能が製品を正しくフィルタリングしない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-37984です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ステージング更新が適用される場合、Visual Merchandiserの「製品別に一致」機能で製品が正しくフィルタリングされない。

<u>複製する手順</u>:

1. 既存製品のスケジュール更新を作成します。
   * `entity_id`と`row_id`に異なる値を設定します。
1. 新しい設定可能な製品を作成し、次にシンプルな製品を作成します（したがって、新製品`entity_id`と`row_ids`も異なります）。
   * 問題のレプリケートを容易にするために、単純な製品（5000など）に識別可能な数量の値を設定します。
1. カテゴリ > **カテゴリ内の製品**&#x200B;に移動し、ルール **で**&#x200B;製品を一致させます。
1. 次に、「数量」を属性として、「大」を演算子として、「4500」を値として選択します。
1. **保存**&#x200B;をクリックします。

<u>期待される結果</u>:

新しく作成された設定可能な製品が一覧表示されます。

<u>実際の結果</u>:

新しく作成された設定可能な製品はリストに表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
