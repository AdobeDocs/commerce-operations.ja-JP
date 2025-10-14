---
title: ACP2E-3753：マルチストア設定でストア固有のテーマテンプレートが使用されないストックアラートメール
description: ACP2E-3753 パッチを適用すると、ストアやテーマの設定に関係なく、マルチストア設定の商品アラートメールが常にデフォルトのテーマを使用して送信されるAdobe Commerceの問題が修正されます。
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 2089fed83a207f9d0211273652ea320d2590f8d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACP2E-3753：マルチストア設定でストア固有のテーマテンプレートが使用されないストックアラートメール

ACP2E-3753 パッチは、ストアやテーマの設定に関係なく、マルチストア設定の製品アラートメールが常にデフォルトのテーマを使用して送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3753 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

マルチストア設定での製品アラートメールは、ストアやテーマの設定に関係なく、常にデフォルトのテーマを使用して送信されます。

<u> 再現手順 </u>:

1. 2 つの web サイト、ストア、ストア表示を作成します。
1. 2 つの個別のテーマを作成して、別々のストアに割り当てます。
1. 製品のアラート設定は、1 分ごとに実行されるデフォルトのスコープです。
1. 両方のテーマについて、`stock.phtml` ファイルのコンテンツの一部を上書きまたは追加します。 ファイルの場所の例：

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. 各ストアに対してユーザーを作成し、製品 Stock アラートを購読します。
1. Product stock アラートをトリガーしてメールを送信します。

<u> 期待される結果 </u>:

メールには、テーマレベルの変更を含める必要があります。

<u> 実際の結果 </u>:

メールには、それぞれの web サイトやストアで設定されたテンプレートは含まれていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
