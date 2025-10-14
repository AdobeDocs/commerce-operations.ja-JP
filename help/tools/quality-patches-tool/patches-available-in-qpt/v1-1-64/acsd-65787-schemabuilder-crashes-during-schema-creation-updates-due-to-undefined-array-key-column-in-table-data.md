---
title: ACSD-65787：テーブルデータ内の未定義の配列キー「列」が原因で、スキーマの作成または更新中に SchemaBuilder がクラッシュする
description: ACSD-65787 パッチを適用すると、スキーマの作成中に SchemaBuilder クラスがクラッシュしたり、テーブルデータを処理する際に未定義の配列キー「列」が原因で更新されたりするAdobe Commerceの問題を修正できます。
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787：テーブルデータ内の未定義の配列キー「列」が原因で、スキーマの作成または更新中に `SchemaBuilder` がクラッシュする

ACSD-65787 パッチは、スキーマの作成中にクラスがクラッシュしたり、テーブルデータ `SchemaBuilder` 処理するときに未定義の配列キー「列」が原因で更新されたりする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-65787 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

スキーマの作成中、またはテーブルデータを処理する際に未定義の配列キー「column」が原因で更新される際に、`SchemaBuilder` クラスがクラッシュする。

<u> 再現手順 </u>:

1. 次のコマンドを実行します。

```
bin/magento setup:upgrade
```

<u> 期待される結果 </u>:

エラーはありません。

<u> 実際の結果 </u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
