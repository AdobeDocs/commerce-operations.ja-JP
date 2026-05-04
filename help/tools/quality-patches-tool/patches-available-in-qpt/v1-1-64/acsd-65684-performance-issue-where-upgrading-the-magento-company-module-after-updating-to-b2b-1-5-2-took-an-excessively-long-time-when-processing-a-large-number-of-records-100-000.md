---
title: 'ACSD-65684: B2B 1.5.2のMagento_Companyのアップグレードは、company_structureの100,000 レコードを超えると遅くなります'
description: B2B 1.5.2のMagento_Company モジュールのアップグレードに時間がかかり、company_structure テーブルで多数のレコード（約100,000以上）を処理する場合にAdobe Commerceの問題を修正するには、ACSD-65684 パッチを適用します。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-65684: [!DNL B2B] 1.5.2の`Magento_Company`のアップグレードに時間がかかり、`company_structure`のレコード数が100,000を超えています

ACSD-65684 パッチは、`company_structure` テーブルの100,000以上のレコードを処理する際に、[!DNL B2B] 1.5.2の`Magento_Company` モジュールのアップグレードに時間がかかりすぎるというパフォーマンスの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65684です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`company_structure` テーブルの100,000以上のレコードを処理する際、[!DNL B2B] 1.5.2の`Magento_Company` モジュールのアップグレードに時間がかかりすぎるパフォーマンスの問題。

<u>複製する手順</u>:

1. Adobe Commerce 2.4.7-p4を[!DNL B2B]にインストールします。
1. `company_structure` テーブルに100,000 レコードを追加します。
1. Adobe Commerce 2.4.7-p5と最新の[!DNL B2B] モジュール （1.5.2）にアップグレードします。
1. パッチ ACSD-65540を適用します。
1. 実行：

```shell
bin/magento setup:upgrade
```

<u>期待される結果</u>:

`setup:upgrade`は妥当な時間で完了しました。

<u>実際の結果</u>:

`setup:upgrade`の完了に非常に長い時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
