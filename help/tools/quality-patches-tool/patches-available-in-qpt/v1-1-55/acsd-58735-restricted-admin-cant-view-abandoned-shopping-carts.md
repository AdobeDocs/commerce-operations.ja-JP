---
title: 「ACSD-58735：制限付き管理者は、関連する web サイトの顧客アカウントで放棄された買い物かごを表示できない」
description: ACSD-58735 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、関連する web サイトのCommerce管理者のカスタマーアカウントページで、制限された管理者が放棄された買い物かごを表示できません。
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735：制限付き管理者は、関連する web サイトの顧客アカウントで放棄された買い物かごを表示できません

ACSD-58735 パッチを使用すると、制限付きのロールを持つ管理者ユーザーが、Commerce **[!UICONTROL Admin]** / **[!UICONTROL Reports]** / **[!UICONTROL Abandoned Carts]** / **[!UICONTROL Select Cart]** / **[!UICONTROL Shopping Cart]** タブから放棄された顧客の買い物かごを表示できない問題を修正できます。

この問題は、複数の web サイトのグリッド表示を表示する際に、管理パネルでデフォルトで放棄された買い物かごが読み込まれる場合、関連するストア ID が表示されないために発生します。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58735 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付き管理者は、管理パネルの顧客アカウントページで、放棄された買い物かごを表示できません。

<u> 再現手順 </u>:

1. いずれかの web サイトにのみアクセスできる管理者の役割を作成します。
1. 放棄された買い物かごを作成します。
1. 完全な権限を持つ管理者ユーザーとしてログインします。 **[!UICONTROL Reports]**/**[!UICONTROL Abandoned Carts]** をチェックして、買い物かごが表示されることを確認します。
1. **[!UICONTROL Reports]**/**[!UICONTROL Abandoned Carts]** を制限付き管理者ユーザーとしてオンにします。

<u> 期待される結果 </u>:

制限付きの管理者は、関連する web サイトの放棄された買い物かごを表示できます。

<u> 実際の結果 </u>:

制限付きの管理者には、関連する web サイトの放棄された買い物かごは表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
