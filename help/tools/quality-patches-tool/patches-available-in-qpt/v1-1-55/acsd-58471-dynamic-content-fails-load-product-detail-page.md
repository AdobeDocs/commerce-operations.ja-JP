---
title: ACSD-58471：関連するカタログ価格ルールがスケジュールされている場合、動的コンテンツを商品詳細ページに読み込めない
description: 関連するカタログ価格ルールがスケジュールされた場合に、動的コンテンツが商品詳細ページに読み込まれないAdobe Commerceの問題を修正するには、ACSD-58471 パッチを適用します。
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-58471：関連するカタログ価格ルールがスケジュールされている場合、動的コンテンツを商品詳細ページに読み込めない

ACSD-58471 パッチは、関連するカタログ価格ルールがスケジュールされたときに、動的コンテンツが製品詳細ページに読み込まれない問題を解決します。 スケジュールされたカタログ価格ルールに関連付けられた動的コンテンツが、製品詳細ページに正しく表示されるようになりました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58471です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カタログ価格ルールがスケジュールされている場合、製品詳細ページに動的コンテンツが読み込まれない。

<u>複製する手順</u>:

1. Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**&#x200B;に動的ブロックを作成します。
1. [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;に静的ブロックを作成します。 ウィジェットを使用してコンテンツを追加します。
1. 商品を作成し、説明にCMS ブロックを追加します。
1. スケジュールされた更新でカタログルールを作成し、製品と作成した動的ブロックを&#x200B;**[!UICONTROL Marketing]**/プロモーション/**[!UICONTROL Catalog Products Rules]**&#x200B;に割り当てます。
1. cronを実行し、スケジュールされた開始時刻の後に製品詳細ページに動的コンテンツが表示されていることを確認します。
1. スケジュールされた更新なしでカタログルールを作成し、製品と作成した動的ブロックを&#x200B;**[!UICONTROL Marketing]** > プロモーション > **[!UICONTROL Catalog Products Rules]**&#x200B;に割り当てます。
1. cronを実行し、スケジュールされた時間の後に製品詳細ページに動的コンテンツが表示されるかどうかを確認します。


<u>期待される結果</u>:

動的コンテンツは、スケジュールされた開始時刻の後に読み込まれます。

<u>実際の結果</u>:

動的コンテンツが読み込まれない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
