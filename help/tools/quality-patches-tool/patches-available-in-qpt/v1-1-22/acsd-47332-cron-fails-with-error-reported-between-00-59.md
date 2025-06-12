---
title: ACSD-47332:UTC で 00:00～00:59 の間にのみ報告されたエラーで cron が失敗する
description: ACSD-47332 パッチを適用すると、cron が 00:00～00:59 UTC に実行中の場合にのみ報告されるエラーで失敗するAdobe Commerceの問題が修正されます。
feature: Configuration
role: Admin
exl-id: ffe6c8f7-0e4c-4a22-853a-45d708bf8164
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-47332:UTC が 00:00～00:59 の間で実行している場合にのみ、cron が失敗し、エラーが報告されます

ACSD-47332 パッチは、cron が 00:00 ～ 00:59 UTC に実行されている場合にのみ報告されるエラーで失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22 がインストールされている場合に使用できます。 パッチ ID は ACSD-47332 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Cron が失敗し、00:00～00:59 UTC で実行している場合にのみ報告されるエラーが表示されます。

<u> 再現手順 </u>:

1. 00:00 ～ 00:59 UTC に `catalog_index_refresh_price` CRON を実行します。

<u> 期待される結果 </u>:

Cron にエラーは表示されません。

<u> 実際の結果 </u>:

Cron は次のエラーで失敗します。

```SQL
SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens, query was: SELECT `cat`.`entity_id` FROM `c
  atalog_product_entity_datetime` AS `attr`
   LEFT JOIN `catalog_product_entity` AS `cat` ON cat.row_id= attr.row_id AND (cat.created_in <= 1 AND cat.updated_in > 1) WHERE (attr.attribute_id
   = '79') AND (attr.store_id = '0') AND (attr.value = DATE_FORMAT('2022-10-02', '%Y-%m-%d %H:%i:%s'))
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
