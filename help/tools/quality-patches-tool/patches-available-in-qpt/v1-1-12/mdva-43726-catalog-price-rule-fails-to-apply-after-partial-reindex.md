---
title: MDVA-43726：部分的なインデックス再作成後にカタログ価格ルールが適用されない
description: MDVA-43726 パッチでは、ストアレベルの属性に基づくカタログ価格ルールの一致が、部分的なインデックス再作成後に適用できない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-43726です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-43726：部分的なインデックス再作成後にカタログ価格ルールが適用されない

MDVA-43726 パッチでは、ストアレベルの属性に基づくカタログ価格ルールの一致が、部分的なインデックス再作成後に適用できない問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-43726です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストア レベルの属性の一致に基づくカタログ価格ルールは、部分的なインデックス再作成後に適用できません。

<u>複製する手順</u>:

1. インデクサーモードをスケジュールどおりに実行するように設定します。
1. 設定可能な2つの製品属性を作成します。 例えば、カラー（ビジュアルスウォッチ）とサイズ（テキストスウォッチ）です。
1. 手順2で作成した両方の属性を使用して、設定可能な製品を作成します。
1. 製品を作成したら、**Yes/No** タイプ属性を作成し、ルール条件に表示させます。
1. この属性をデフォルトの属性セットに追加します。
1. この属性が&#x200B;**Yes**&#x200B;に設定されている場合に適用するカタログ価格ルールを作成します。
1. 設定可能な製品に関連するシンプルな製品の1つを開きます。
1. ストア表示に範囲を変更し、属性値を&#x200B;**Yes**&#x200B;に更新します。
1. `CRON`を実行し、フロントエンドで価格を確認します。
1. 完全なインデックス再作成を実行します。 もう一度、フロントエンドの価格を確認してください。
1. 設定可能な製品カテゴリを更新します。
1. `CRON`を実行し、フロントエンドで価格を再度確認します。

<u>期待される結果</u>:

カタログ規則は、増分インデクサーを使用して完全にインデックスを再作成しなくても正しく適用されます。

<u>実際の結果</u>:

完全なインデックス再作成を実行しないと、カタログのルールは適用されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
