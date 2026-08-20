---
title: ACSD-50621：共有カタログ内の異なるweb サイトの階層価格が表示されない
description: ACSD-50621 パッチを適用して、複数のweb サイト環境で共有カタログ内の異なるweb サイトの階層の価格が表示されないAdobe Commerceの問題を修正します。
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-50621：共有カタログ内の異なるweb サイトの階層価格が表示されない

ACSD-50621 パッチは、複数のweb サイト環境で共有カタログ内の異なるweb サイトの階層の価格が表示されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-50621です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数のweb サイト環境で共有カタログ内の異なるweb サイトの階層価格を編集する場合、表示されません。

<u>複製する手順</u>:

1. **[!UICONTROL Catalog Price Scope]**&#x200B;を&#x200B;**[!UICONTROL Website]**&#x200B;に設定します。
1. web サイト、実店舗、ストアビューを追加作成する。
1. シンプルな商品を作成し、すべてのweb サイトに割り当てる：
1. カスタム共有カタログの作成。
1. 作成したカスタム共有カタログの&#x200B;**[!UICONTROL Set Pricing and Structure]**&#x200B;に移動します。
1. 手順1：カタログの商品を選択します。 作成したシンプルな商品を追加します。
1. 手順2：カスタム価格を設定し、**[!UICONTROL Configure]**&#x200B;をクリックします。
1. web サイトごとに異なる価格帯を設定する。
1. **[!UICONTROL Done]**&#x200B;を選択して&#x200B;**[!UICONTROL Generate Catalog]**&#x200B;をクリックし、**[!UICONTROL Save]**&#x200B;をクリックします。
1. cronを実行します。
1. **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]**&#x200B;に移動し、価格帯を確認します。

<u>期待される結果</u>:

異なるウェブサイト用に以前に設定されたすべての階層の価格が存在します。

<u>実際の結果</u>:

以前に設定した階層の価格は存在しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
