---
title: ACSD-58471：関連するカタログ価格ルールがスケジュールされている場合、製品の詳細ページに動的コンテンツが読み込まれない
description: 関連するカタログ価格ルールがスケジュールされていると、動的コンテンツが商品の詳細ページに読み込めないAdobe Commerceの問題を修正するために、ACSD-58471 パッチを適用してください。
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471：関連するカタログ価格ルールがスケジュールされている場合、製品の詳細ページに動的コンテンツが読み込まれない

ACSD-58471 パッチは、関連するカタログ価格ルールがスケジュールされている場合に、動的コンテンツが製品の詳細ページに読み込まれない問題を解決します。 スケジュールされたカタログ価格ルールに関連付けられた動的コンテンツが、製品の詳細ページに正しく表示されるようになりました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58471 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カタログ価格ルールがスケジュールされている場合、製品の詳細ページに動的コンテンツが読み込まれない。

<u> 再現手順 </u>:

1. Commerce [!UICONTROL Admin] / **[!UICONTROL Content]** / **[!UICONTROL Dynamic Blocks]** で動的ブロックを作成します。
1. [!UICONTROL Admin]/**[!UICONTROL Content]**/**[!UICONTROL Blocks]** で静的ブロックを作成します。 ウィジェットを使用してコンテンツを追加します。
1. 商品を作成し、説明にCMS ブロックを追加します。
1. スケジュールされた更新を含むカタログルールを作成し、**[!UICONTROL Marketing]** / プロモーション / **[!UICONTROL Catalog Products Rules]** で製品と作成した動的ブロックを割り当てます。
1. Cron を実行し、スケジュールされた開始時間の後に、製品の詳細ページに動的コンテンツが表示されることを確認します。
1. スケジュールされた更新を行わずにカタログルールを作成し、**[!UICONTROL Marketing]** / プロモーション / **[!UICONTROL Catalog Products Rules]** で製品と作成した動的ブロックを割り当てます。
1. Cron を実行し、スケジュール設定した時刻以降に製品の詳細ページに動的コンテンツが表示されるかどうかを確認します。


<u> 期待される結果 </u>:

スケジュールされた開始時間の後に動的コンテンツが読み込まれます。

<u> 実際の結果 </u>:

動的コンテンツが読み込まれない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
