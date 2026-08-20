---
title: 'ACSD-65331: チェックアウトに戻った後、[!UICONTROL Pick in Store]の選択したストアがクリアされました'
description: ACSD-65331 パッチを適用して、ユーザーがチェックアウトページに繰り返し戻ったときに、[!UICONTROL Pick In Store] オプションの下にある選択したストアがクリアされるAdobe Commerceの問題を修正します。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ACSD-65331: チェックアウトに戻った後、**[!UICONTROL Pick in Store]**&#x200B;の選択したストアがクリアされました

ACSD-65331 パッチは、ユーザーがチェックアウトページに繰り返し戻ったときに&#x200B;**[!UICONTROL Pick In Store]** オプションの下で選択したストアがクリアされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-65331です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーがチェックアウトページに繰り返し戻ると、**[!UICONTROL Pick In Store]** オプションで選択したストアはクリアされます。

<u>複製する手順</u>:

1. **[!UICONTROL In-Store Delivery]**&#x200B;を有効にするには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;に移動します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**&#x200B;に移動して、[!UICONTROL Google Distance Provider]の有効な[!DNL Google] API キーを設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**&#x200B;に移動して、次の詳細を含む新しいソースを追加します。

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *はい*
   * **[!UICONTROL Country]**: *米国*
   * **[!UICONTROL State]**: *イリノイ州*
   * **[!UICONTROL City]**: *キャロル ストリーム*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]**&#x200B;に移動して、新しいストックを作成します。

   新しく作成したソースとメイン web サイトをこの在庫に割り当てます。
1. 商品を編集し、以下を行います。

   1. 新しく作成したソースに割り当てます。
   1. ステータスを&#x200B;*[!UICONTROL In Stock]*&#x200B;に、数量を0より大きく設定します。

1. リインデクサーを実行します。
1. ストアフロントで、新しい顧客を作成し、デフォルトの請求先住所と配送先住所としてカリフォルニアの住所を設定します。
1. 同じ顧客に追加のイリノイ州の住所を追加します（デフォルト以外）。
1. 構成済みの製品をカートに追加し、**[!UICONTROL Checkout]**&#x200B;に進みます。
1. イリノイ州の住所を選択し、配送方法として&#x200B;**[!UICONTROL Pick In Store]**&#x200B;を選択し、**[!UICONTROL Next]**&#x200B;をクリックします。
1. ソースが読み込まれるのを待って、**[!UICONTROL Next]**&#x200B;をクリックします。
1. ホームページに戻ります。
1. **[!UICONTROL Checkout]** ページを再表示します。

<u>期待される結果</u>:

選択したストアは&#x200B;**[!UICONTROL Pick In Store]**&#x200B;の下で引き続き利用できます。

<u>実際の結果</u>:

配送ステップが読み込みを開始し、**[!UICONTROL Pick In Store]**&#x200B;にリダイレクトされますが、ストアは表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
