---
title: MDVA-43824：注文キャンセル操作が失敗し、「項目をキャンセルしていません」というエラーが表示される
description: MDVA-43824 パッチは、次のエラーで注文取り消しアクションが失敗した問題を解決します。*商品をキャンセルしていません*。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-43824です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# MDVA-43824：注文キャンセル操作が失敗し、「項目をキャンセルしていません」というエラーが表示される

MDVA-43824 パッチは、次のエラーで注文取り消しアクションが失敗した問題を解決します。*アイテムをキャンセルしていません*。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-43824です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.6 - 2.3.7-p3、2.4.1 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ログインしたお客様による注文はキャンセルできません。 次のエラーが発生したため、注文キャンセル処理に失敗しました：

```text
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>複製する手順</u>:

1. セールスルールを作成します（クーポンタイプは「特定のクーポン」または「クーポンなし」です）。
1. ストアフロントに移動し、顧客としてログインして、商品をカートに追加します。
1. カートに移動し、カート価格ルールに「特定クーポン」というクーポンがある場合は、カート価格ルールを適用します。 カート価格ルールを正常に適用する必要があります。
1. チェックアウトに移動し、任意の支払い方法で注文します。
1. Commerce Admin > **Sales** > **Orders**&#x200B;に移動します。
1. 手順4で配置した注文を開きます。
1. 「**キャンセル**」ボタンをクリックします。

<u>期待される結果</u>:

注文はエラーなしで正常にキャンセルされました。

<u>実際の結果</u>:

次のエラーが発生したため、注文取り消しアクションに失敗しました：*アイテムを取り消していません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
