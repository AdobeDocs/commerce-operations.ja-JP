---
title: ACSD-63242:10,000 個を超えるカタログ製品を追加すると読み込みが遅くなる
description: ACSD-63242 パッチを適用すると、10,000 を超えるエントリを含むカタログ商品が追加された場合に、読み込みが遅くなるAdobe Commerceの問題を修正できます。
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 5fe00c9341414a0a2ba6b535d992d6c64e1c3b3a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242:10,000 個を超えるカタログ製品を追加すると読み込みが遅くなる

ACSD-63242 パッチは、エントリ数が 10,000 を超えるカタログ製品を追加すると、読み込みが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-63242 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 ～ 2.4.6-p8 および 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

エントリ数が 10,000 を超えるカタログ製品を追加すると、製品の読み込みが遅くなる。

<u> 再現手順 </u>:

1. **[!UICONTROL System]**/**[!UICONTROL Import]**/**[!UICONTROL Products]**/**[!UICONTROL Add/Update]** に移動します。
1. 10,000 個を超えるエントリを含むファイルをインポートします。

<u> 期待される結果 </u>:

カタログ製品のインポートは想定した時間内に実行されます。

<u> 実際の結果 </u>:

製品の読み込みが遅い。 `var/log/exception.log` には、次が含まれます。

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
