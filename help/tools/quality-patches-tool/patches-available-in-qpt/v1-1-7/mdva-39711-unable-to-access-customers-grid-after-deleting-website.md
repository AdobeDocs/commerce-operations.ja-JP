---
title: MDVA-39711:Web サイトを削除した後に顧客グリッドにアクセスできない
description: MDVA-39711 パッチは、管理者ユーザーがweb サイトを削除した後に顧客のグリッドにアクセスできない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.7がインストールされている場合に利用できます。 パッチ IDはMDVA-39711です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: Configuration
role: Admin
exl-id: 7ddca2e7-86f5-4ffd-9c00-ea4c511ab663
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-39711:Web サイトを削除した後に顧客グリッドにアクセスできない

MDVA-39711 パッチは、管理者ユーザーがweb サイトを削除した後に顧客のグリッドにアクセスできない問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.7がインストールされている場合に使用できます。 パッチ IDはMDVA-39711です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7-p2、2.3.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、web サイトを削除した後に顧客のグリッドにアクセスできません。

<u>複製する手順</u>:

1. 新しいweb サイト、ストア、ストアビューを作成する。
1. 管理画面で新しい顧客を作成し、作成したweb サイトに関連付けます。
1. **ストア** > **すべてのストア**&#x200B;に移動し、作成したWeb サイトを削除します。
1. **お客様** > **すべてのお客様**&#x200B;に移動します。

<u>期待される結果</u>:

* エラーメッセージはありません。
* 顧客はすべてグリッドに表示されます。

<u>実際の結果</u>:

* ユーザーはエラーメッセージを受け取ります：*リクエストされたID 2のweb サイトが見つかりませんでした。 Web サイトを確認して、もう一度やり直してください*
* すべての顧客が表示されるわけではありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
