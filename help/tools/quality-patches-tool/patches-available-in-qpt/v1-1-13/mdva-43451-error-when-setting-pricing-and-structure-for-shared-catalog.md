---
title: MDVA-43451：共有カタログの価格と構造を設定する際にエラーが発生する
description: MDVA-43451 パッチは、共有カタログの価格と構造を設定できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13 がインストールされている場合に利用できます。 パッチ ID は MDVA-43451。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Catalog Management
role: Admin
exl-id: 2cddfca2-ee32-4e73-9ef6-78125fbaa13d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-43451：共有カタログの価格と構造を設定する際にエラーが発生する

MDVA-43451 パッチは、共有カタログの価格と構造を設定できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.13 がインストールされている場合に使用できます。 パッチ ID は MDVA-43451。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーは、共有カタログの価格と構造を設定できません。 *リクエストされたストアが見つかりませんでした。 ストアを確認して、もう一度試してください。*

<u> 再現手順 </u>:

1. カスタム web サイトを作成します。 Web サイトの id は、0、1、2 にする必要があります。
1. 上記の web サイトの下に 1 つのストアを作成します。 ストアの ID は、0,1,2 にする必要があります。
1. 上記のストアに対して 3 つのストア表示を作成します。 ストアビューの ID は、0、1、2、3、4 にする必要があります。
1. ID 2 のストア表示を削除します。 これで、ストアテーブルは次のテーブルのようになります。

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. 新しい共有カタログを作成します。
1. 価格と構造を設定する場合は、手順 2 で作成したストアを選択します。
1. 共有カタログを保存します。

<u> 期待される結果 </u>:

共有カタログは問題なく保存されます。

<u> 実際の結果 </u>:

共有カタログを保存できません。 次のエラーが表示されます。
*リクエストされたストアが見つかりませんでした。 ストアを確認して、もう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
