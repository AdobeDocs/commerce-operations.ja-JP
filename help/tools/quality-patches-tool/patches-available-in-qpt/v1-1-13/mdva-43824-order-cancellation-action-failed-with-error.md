---
title: MDVA-43824：注文のキャンセル操作が失敗し、「アイテムがキャンセルされていません」というエラーが表示される
description: MDVA-43824 パッチは、注文のキャンセル操作が次のエラーで失敗した問題を解決します。*アイテムをキャンセルしていません*。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13 がインストールされている場合に利用できます。 パッチ ID は MDVA-43824。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824：注文のキャンセル操作が失敗し、「アイテムがキャンセルされていません」というエラーが表示される

MDVA-43824 パッチは、注文キャンセル アクションが次のエラーで失敗した問題を解決します。*アイテムをキャンセルしていません*。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.13 がインストールされている場合に使用できます。 パッチ ID は MDVA-43824。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.6 ～ 2.3.7-p3、2.4.1 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ログインしている顧客が行った注文をキャンセルすることはできません。 注文のキャンセル操作が次のエラーで失敗しました：

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u> 再現手順 </u>:

1. 販売ルールを作成します（クーポンタイプは「特定クーポン」または「クーポンなし」です）。
1. ストアフロントに移動して、顧客としてログインし、商品を買い物かごに追加します。
1. 買い物かごに移動し、買い物かご価格ルールに「特定のクーポン」というクーポンがある場合は、買い物かご価格ルールを適用します。 買い物かごの価格ルールが正常に適用されます。
1. チェックアウトに移動し、任意の支払い方法で注文します。
1. Commerce管理者/**営業**/**注文** に移動します。
1. 手順 4 で発注した品目を開きます。
1. 「**キャンセル**」ボタンをクリックします。

<u> 期待される結果 </u>:

注文はエラーなしで正常にキャンセルされました。

<u> 実際の結果 </u>:

注文のキャンセル操作が次のエラーで失敗しました：*品目はキャンセルされていません。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
