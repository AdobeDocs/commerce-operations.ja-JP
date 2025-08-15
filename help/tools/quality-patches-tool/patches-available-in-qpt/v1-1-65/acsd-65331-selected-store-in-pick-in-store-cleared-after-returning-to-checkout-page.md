---
title: ACSD-65331：チェックアウトに戻った後、[!UICONTROL Pick in Store] で選択されたストアがクリアされました
description: ユーザーが繰り返しチェックアウトページに戻る際に、「[!UICONTROL Pick In Store]」オプションの下で選択したストアがクリアされるAdobe Commerceの問題を修正するために、ACSD-65331 パッチを適用します。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331：チェックアウトに戻った後、**[!UICONTROL Pick in Store]** で選択されたストアがクリアされました

ACSD-65331 パッチは、ユーザーが繰り返しチェックアウトページに戻ったときに、「**[!UICONTROL Pick In Store]**」オプションの下で選択したストアがクリアされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-65331 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーがチェックアウトページに繰り返し戻ると、「**[!UICONTROL Pick In Store]**」オプションで選択したストアはクリアされます。

<u> 再現手順 </u>:

1. **[!UICONTROL In-Store Delivery]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Delivery Methods]** に移動して、**[!UICONTROL In-Store Delivery]** を有効にします。
1. [!DNL Google]/[!UICONTROL Google Distance Provider]/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]** に移動して、**[!UICONTROL Inventory]** に有効な **[!UICONTROL Google Distance Provider]** API キーを設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Sources]**/**[!UICONTROL Add New Source]** に移動して、次の詳細を含む新しいソースを追加します。

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *はい*
   * **[!UICONTROL Country]**: *米国*
   * **[!UICONTROL State]**: *イリノイ州*
   * **[!UICONTROL City]**: *Carol ストリーム*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. **[!UICONTROL Stores]**/**[!UICONTROL Stocks]**/**[!UICONTROL Add New Stock]** に移動して、新しい在庫を作成します。

   新しく作成したソースとメインの web サイトをこの Stock に割り当てます。
1. 製品を編集し、次の操作を行います。

   1. 新しく作成したソースに割り当てます。
   1. ステータスを *[!UICONTROL In Stock]* に、数量を 0 より大きい値に設定します。

1. あなたのレインデクサーを実行します。
1. ストアフロントで、新しい顧客を作成し、デフォルトの請求先と配送先住所としてカリフォルニア州の住所を設定します。
1. 同じ顧客にイリノイ州の住所を追加します（デフォルト以外）。
1. 設定済みの製品を買い物かごに追加し、**[!UICONTROL Checkout]** に進みます。
1. イリノイ州の住所を選択し、配送方法として **[!UICONTROL Pick In Store]** を選択して、「**[!UICONTROL Next]**」をクリックします。
1. ソースが読み込まれるのを待ち、「**[!UICONTROL Next]**」をクリックします。
1. ホームページに戻ります。
1. **[!UICONTROL Checkout]** ページに再度アクセスします。

<u> 期待される結果 </u>:

選択したストアは、**[!UICONTROL Pick In Store]** の下でも引き続き使用できます。

<u> 実際の結果 </u>:

配送ステップが読み込みを開始し、**[!UICONTROL Pick In Store]** にリダイレクトされますが、ストアは表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
