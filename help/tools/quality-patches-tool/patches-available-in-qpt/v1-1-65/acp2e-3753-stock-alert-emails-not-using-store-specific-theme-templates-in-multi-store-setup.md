---
title: ACP2E-3753：複数店舗設定で店舗固有のテーマテンプレートを使用しないストックアラートメール
description: ACP2E-3753 パッチを適用して、マルチストア設定の商品アラートメールが、ストアまたはテーマ設定に関係なく、常にデフォルトのテーマを使用して送信されるAdobe Commerceの問題を修正します。
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACP2E-3753：複数店舗設定で店舗固有のテーマテンプレートを使用しないストックアラートメール

ACP2E-3753 パッチでは、マルチストア設定の製品アラートメールが、ストアやテーマ設定に関係なく、常にデフォルトのテーマを使用して送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACP2E-3753です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

マルチストア設定の商品アラートメールは、ストアやテーマの設定に関係なく、常にデフォルトのテーマを使用して送信されます。

<u>複製する手順</u>:

1. Web サイト、実店舗、ストアビューを2つ作成する。
1. 2つの個別のテーマを作成し、それらを別のストアに割り当てます。
1. 製品アラート設定は、毎分実行されるデフォルトのスコープです。
1. 両方のテーマの`stock.phtml` ファイルに一部のコンテンツを上書きまたは追加します。 ファイルの場所の例：

   ```text
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. 各店舗のユーザーを作成し、商品在庫アラートを購読します。
1. 商品の在庫アラートをトリガーして、メールを送信します。

<u>期待される結果</u>:

メールには、テーマレベルの変更を含める必要があります。

<u>実際の結果</u>:

メールには、各web サイト/ストアで設定されたテンプレートが含まれていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
