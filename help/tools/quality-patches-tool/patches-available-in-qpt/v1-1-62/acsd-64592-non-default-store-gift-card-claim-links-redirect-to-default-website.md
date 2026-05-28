---
title: ACSD-64592：デフォルト以外のストアギフトカードの請求リンクがデフォルトのweb サイトにリダイレクトされる
description: ACSD-64592 パッチを適用して、複数のweb サイトの設定で、仮想ギフトカードがセカンダリ（デフォルト以外）のweb サイトから購入された場合、メール内のギフトカードコードリンクにデフォルトのweb サイト URLが含まれている問題を修正します。
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-64592：デフォルト以外のストアギフトカードの請求リンクがデフォルトのweb サイトにリダイレクトされる

ACSD-64592 パッチでは、マルチサイト環境で、仮想ギフトカードがセカンダリ（プライマリ以外）のweb サイトから購入された場合、ギフトカードコードリンクを含むメールがデフォルトのweb サイトのURLにユーザーを誘導する問題を修正します。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数のweb サイトの設定で、仮想ギフトカードがセカンダリ（デフォルト以外）サイトから購入された場合、ギフトカードコードのリンクを含むメールは、ユーザーをデフォルトのweb サイトのURLに誘導します。

<u>複製する手順</u>:

1. ふたつ目のweb サイト、実店舗ビューの作成。
1. ベース Web サイトとセカンダリ Web サイトに対して異なるベース URLを設定します。
1. いくつかの量のオプションを持つ仮想ギフトカードを作成します。
1. 新しいコードプールを&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**&#x200B;に生成します。
1. セカンダリ web サイトのギフトカード製品で注文します。
1. Commerce管理画面で注文を請求書に記入します。
1. 「*」のギフトカードコードリンクのURLを確認してください。「*」のメールからギフトが送信されました。

<u>期待される結果</u>:

ギフトカードコードのリンクには、2つ目のWeb サイトへのリンクが必要です。

<u>実際の結果</u>:

2つ目のweb サイトで注文が行われたとしても、ギフトカードコードのリンクにはデフォルトのweb サイト URLが含まれています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。
* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
