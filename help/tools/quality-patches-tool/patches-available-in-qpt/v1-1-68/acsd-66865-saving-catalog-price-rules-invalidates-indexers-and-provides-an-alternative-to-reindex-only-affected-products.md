---
title: ACSD-66865:[!UICONTROL Catalog Price Rule] を保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供される
description: Adobe Commerceの問題を修正するために ACSD-66865 パッチを適用してください。この問題の場所は次のとおりです。  [!UICONTROL Catalog Price Rules] を保存すると、インデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供されます。
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865:**[!UICONTROL Catalog Price Rule]** を保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供される

ACSD-66865 パッチは、**[!UICONTROL Catalog Price Rule]** を保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供される問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66865 です。 この問題はAdobe Commerce 2.4.8 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Catalog Price Rule]** を保存すると、すべてのインデクサーが無効化され、影響を受ける製品のみを再インデックス化する代わりに、完全な再インデックスがトリガーされます。

<u> 再現手順 </u>:

1. cron が実行されておらず、すべてのインデクサーがスケジュールに従って更新するように設定されていることを確認します（保存時に更新できる `customer_grid` を除く）。
2. 次のコマンドを使用して、手動による完全なインデックス再作成を実行します。`php bin/magento indexer:reindex`
3. すべてのインデックスがステータス *[!UICONTROL Ready]* を示し、バックログに *0* 項目が含まれていることを確認します。
4. 管理者サイドバーで、**[!UICONTROL Marketing]**/*[!UICONTROL Promotions]*/**[!UICONTROL Catalog Price Rule]** に移動します。 1 つの製品に対してアクティブなカタログ価格ルールを作成します（例えば、*SKU* 条件を使用）。
5. コマンド `php bin/magento indexer:status` を実行して、インデクサーのステータスを確認します。
6. 影響を受ける製品が 1 つだけの場合でも、複数のインデックスが **[!UICONTROL Reindex Required]** としてマークされていることに注意してください。

<u> 期待される結果 </u>:

影響を受ける製品データのみが識別され、すべてのインデクサーにわたる完全な再インデックスではなく、部分的な再インデックスがトリガーされます。

<u> 実際の結果 </u>:

**[!UICONTROL Catalog Price Rule]** の影響を受ける製品が 1 つだけの場合でも、すべてのインデクサーに対して完全な再インデックスがトリガーされます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
