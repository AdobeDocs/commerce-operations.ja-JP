---
title: MDVA-37592：価格がゼロの製品では価格によるソートが機能しない
description: MDVA-37592 Adobe Commerce パッチは、価格によるソートが、共有カタログに価格ゼロが割り当てられている商品に対して正しく機能しない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0がインストールされている場合に利用できます。 パッチ IDはMDVA-37592です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-37592：価格がゼロの製品では価格によるソートが機能しない

MDVA-37592 Adobe Commerce パッチは、価格によるソートが、共有カタログに価格ゼロが割り当てられている商品に対して正しく機能しない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0がインストールされている場合に使用できます。 パッチ IDはMDVA-37592です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce on our cloud architecture 2.4.0-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメントタイプ） 2.3.6-2.4.2-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

共有カタログに価格ゼロが割り当てられている製品では、価格による並べ替えが正しく機能しません。

<u>前提条件</u>:

B2Bがインストールされます。

<u>複製する手順</u>:

1. 共有カタログを有効にします。
1. 次の価格の4つの商品を作成し、それを50 ドル、60 ドル、70 ドル、80 ドルのカテゴリに割り当てます。
1. 上記の製品で共有カタログを作成します。
1. 製品のカスタム価格を70 ドルの価格でゼロに設定します。
1. 次に、会社ユーザーを作成し、作成したばかりの共有カタログに割り当てます。
1. 会社アカウントを使用してログインし、製品が割り当てられているカテゴリを参照します。
1. 価格でソートしてみてください。

<u>期待される結果</u>:

価格ゼロの商品が正しくソートされます。

<u>実際の結果</u>:

価格がゼロの商品は正しくソートされていません。 その代わりに、元の価格に従ってソートされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!DNL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
