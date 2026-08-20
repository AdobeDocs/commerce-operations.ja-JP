---
title: 'ACSD-53239: インベントリインデクサーがすべてのキャッシュを消去する'
description: ACSD-53239 パッチを適用して、インベントリインデクサーが[!UICONTROL Update on Schedule] モードのすべてのキャッシュをクリアするAdobe Commerceの問題を修正します。
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: 69e71e2d-8f26-4200-ad4a-6bd9e45627e4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-53239: インベントリインデクサーが[!UICONTROL Update on Schedule] モードのすべてのキャッシュをクリアする

ACSD-53239 パッチは、インベントリインデクサーが[!UICONTROL Update on Schedule] モードのすべてのキャッシュをクリアする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-53239です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

インベントリインデクサーは、[!UICONTROL Update on Schedule] モードのすべてのキャッシュをクリアします。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]**&#x200B;に移動し、約&#x200B;*1200*&#x200B;製品を選択します。
2. *[!UICONTROL Qty]*&#x200B;を新しい値に更新し、**[!UICONTROL Save]**&#x200B;をクリックします。
3. 保存直後に`bin/magento cron:run`を実行します。
4. 次のGraphQL クエリを実行します。

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>期待される結果</u>

クエリは通常の時間内に処理されます。

<u>実際の結果</u>

クエリの処理が異常に遅くなっています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
