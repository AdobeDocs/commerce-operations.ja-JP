---
title: 'MDVA-42283: フランス語ロケールの日時形式が無効です'
description: MDVA-42283 パッチでは、フランス語ロケールの管理者注文グリッドの日時形式が無効になる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-42283です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: CMS
role: Admin
exl-id: ed99519d-03e2-444b-9cd1-e5c6e6d2ac2d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-42283: フランス語ロケールの日時形式が無効です

MDVA-42283 パッチでは、フランス語ロケールの管理者注文グリッドの日時形式が無効になる問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-42283です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

フランス語ロケールの管理者注文グリッドの日時形式が無効です。

<u>複製する手順</u>:

1. 注文、お客様、CMS ページまたはCMS ブロックを作成します。
1. **管理者** > **アカウント設定**&#x200B;に移動し、管理者のインターフェイスロケールを&#x200B;**Français （Canada）**/**français （Canada）（fr_CA）**&#x200B;または&#x200B;**ブラジルポルトガル語（pt_BR）**&#x200B;に設定します。
1. 注文、出荷、クレジットメモ、お客様、CMS ページまたはCMS ブロックグリッドの日付列の値を確認します。

<u>期待される結果</u>:

日付は、エンティティの実際の編集ページに表示される形式です。

<u>実際の結果</u>:

日時の値が正しくありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
