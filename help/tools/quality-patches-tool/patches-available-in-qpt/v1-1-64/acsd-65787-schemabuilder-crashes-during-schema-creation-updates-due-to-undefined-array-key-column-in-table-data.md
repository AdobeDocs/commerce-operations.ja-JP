---
title: ACSD-65787：テーブルデータの配列キー「column」が未定義であるため、スキーマの作成中または更新中にSchemaBuilderがクラッシュする
description: ACSD-65787 パッチを適用して、テーブルデータを処理する際に未定義の配列キー「column」が原因でスキーマの作成中または更新中にSchemaBuilder クラスがクラッシュするAdobe Commerceの問題を修正します。
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 93bf12af83dbaf37c51a9730f2d2a6089000b3f0
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-65787: テーブル データ内の配列キー「列」が未定義のため、スキーマの作成中または更新中に`SchemaBuilder`がクラッシュする

ACSD-65787 パッチは、テーブルデータの処理中に未定義の配列キー「column」が原因で、`SchemaBuilder` クラスがスキーマの作成中または更新中にクラッシュする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65787です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

テーブル データの処理中に未定義の配列キー「列」が原因で、スキーマの作成中または更新中に`SchemaBuilder` クラスがクラッシュします。

<u>複製する手順</u>:

1. 次のコマンドを実行します。

```shell
bin/magento setup:upgrade
```

<u>期待される結果</u>:

エラーがありません。

<u>実際の結果</u>:

```text
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
