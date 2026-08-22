---
title: 'ACSD-66865: [!UICONTROL Catalog Price Rule]を保存すると、インデクサーが無効になり、影響を受ける製品のみを再インデックスする代わりに使用できます'
description: ACSD-66865 パッチを適用して、[!UICONTROL Catalog Price Rules]を保存するとインデクサーが無効になり、影響を受ける商品のみを再インデックス化する代わりに使用できるAdobe Commerceの問題を修正します。
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
exl-id: 68baf176-ee6e-4ba8-8a34-8adb8d1e16fe
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-66865: **[!UICONTROL Catalog Price Rule]**&#x200B;を保存すると、インデクサーが無効になり、影響を受ける製品のみを再インデックスする代わりに使用できます

ACSD-66865 パッチは、**[!UICONTROL Catalog Price Rule]**&#x200B;を保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代わりに使用できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66865です。 この問題は、Adobe Commerce 2.4.8で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Catalog Price Rule]**&#x200B;を保存すると、すべてのインデックスが無効になり、影響を受ける製品のみをインデックス再作成するのではなく、完全なインデックス再作成がトリガーされます。

<u>複製する手順</u>:

1. cronが実行されておらず、すべてのインデクサーがスケジュールに従って更新されるように設定されていることを確認します（保存時に更新できる`customer_grid`を除く）。
2. 次のコマンドを使用して、完全な手動インデックス再作成を実行します：`php bin/magento indexer:reindex`。
3. バックログに&#x200B;*0*&#x200B;個のアイテムを含むすべてのインデックスにステータス *[!UICONTROL Ready]*&#x200B;が表示されていることを確認します。
4. 管理者サイドバーで、**[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**&#x200B;に移動します。 1つの製品に対してアクティブなカタログ価格ルールを作成します（例：*SKU*&#x200B;条件を使用）。
5. 次のコマンドを実行します：`php bin/magento indexer:status` インデクサーのステータスを確認します。
6. 1つの製品のみが影響を受けるにもかかわらず、複数のインデックスが&#x200B;**[!UICONTROL Reindex Required]**&#x200B;としてマークされていることに注意してください。

<u>期待される結果</u>:

影響を受ける製品データのみが識別され、すべてのインデックスで完全なインデックスを作成する代わりに、部分的なインデックス作成がトリガーされます。

<u>実際の結果</u>:

1つの製品のみが&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;の影響を受ける場合でも、すべてのインデクサーに対して完全な再インデックスがトリガーされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
