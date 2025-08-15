---
title: ACSD-65684:B2B 1.5.2 のMagento_Company のアップグレードが遅く、company_structure に 100,000 件を超えるレコードがある
description: ACSD-65684 パッチを適用すると、company_structure テーブルに大量のレコード（～100,000）が処理されるため、B2B 1.5.2 のMagento_Company モジュールのアップグレードに時間がかかりすぎるAdobe Commerceの問題を修正できます。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684:`Magento_Company` 1.5.2 の [!DNL B2B] のアップグレードが遅く、`company_structure` のレコードが 10 万件を超えています

ACSD-65684 パッチは、`Magento_Company` テーブル内の 100,000 件以上のレコードを処理する際に、[!DNL B2B] 1.5.2 の `company_structure` モジュールのアップグレードに時間がかかりすぎるパフォーマンスの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-65684 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce B2B （すべてのデプロイメント方法） 1.5.2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`Magento_Company` 1.5.2 の [!DNL B2B] モジュールのアップグレードで、`company_structure` テーブルの 100,000 件以上のレコードを処理する際に時間がかかりすぎるパフォーマンスの問題。

<u> 再現手順 </u>:

1. Adobe Commerce 2.4.7-p4 と [!DNL B2B] をインストールします。
1. テーブルに 100,000 件のレコード `company_structure` 追加します。
1. Adobe Commerce 2.4.7-p5 および最新の [!DNL B2B] モジュール（1.5.2）にアップグレードします。
1. パッチ ACSD-65540 を適用します。
1. 実行：

```
bin/magento setup:upgrade
```

<u> 期待される結果 </u>:

`setup:upgrade` は妥当な時間内に完了する。

<u> 実際の結果 </u>:

`setup:upgrade` の完了に非常に長い時間がかかる。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
