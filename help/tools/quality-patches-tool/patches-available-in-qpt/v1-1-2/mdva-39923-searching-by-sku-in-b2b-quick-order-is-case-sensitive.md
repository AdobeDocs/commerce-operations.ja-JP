---
title: MDVA-39923:B2B クイック注文機能のSKUによる検索では、大文字と小文字が区別されます
description: MDVA-39923 パッチでは、名前が保存されているケースとは異なるケースで、B2B クイック注文機能でSKUで注文を検索すると、エラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-39923です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# MDVA-39923:B2B クイック注文機能のSKUによる検索では、大文字と小文字が区別されます

MDVA-39923 パッチでは、名前が保存されているケースとは異なるケースで、B2B クイック注文機能でSKUで注文を検索すると、エラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-39923です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

B2B クイック注文機能でSKUで検索する場合、大文字と小文字が区別され、SKUが保存されている場合とは異なる大文字と小文字が区別され、エラーが表示されます。

<u>前提条件</u>:

B2B モジュールがインストールされている。

<u>複製する手順</u>:

1. 管理者にログインし、**Stores** > **Configuration** > **B2B**&#x200B;に移動します。
1. **共有カタログ**&#x200B;と&#x200B;**クイックオーダー**&#x200B;を有効にします。
1. TEST20-1234など、大文字のSKUを使用した製品の作成
1. 作成した製品を&#x200B;**共有カタログ**&#x200B;に割り当てます。
1. 顧客としてログインし、**クイックオーダー**&#x200B;をクリックします。
1. test20-1234など、SKUを小文字で入力します。

<u>期待される結果</u>:

使用するケースに関係なく、製品を見つける必要があります。

<u>実際の結果</u>:

次のエラーメッセージを受信しました：*1個の製品には注意が必要です*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
