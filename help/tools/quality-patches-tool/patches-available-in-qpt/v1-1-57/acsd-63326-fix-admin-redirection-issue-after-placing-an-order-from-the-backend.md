---
title: ACSD-63326：バックエンドから注文した後の管理リダイレクトの問題を修正しました
description: ACSD-63326 パッチを適用すると、バックエンドから注文した後、管理者が壊れたページにリダイレクトされるAdobe Commerceの問題を修正できます。
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 47603deecdf5ac3e6be18efeef38cba52ec936ec
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326：バックエンドから注文した後の管理リダイレクトの問題を修正しました

ACSD-63326 パッチは、バックエンドから注文した後、管理者が壊れたページにリダイレクトされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-63326 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者は、バックエンドから顧客への注文が成功した後、レイアウトが壊れたページにリダイレクトされます。

<u> 再現手順 </u>:

1. 管理パネルの「**[!UICONTROL Customers]**」セクションに移動します。
1. 任意の顧客を選択し、「**[!UICONTROL Edit]**」をクリックします。
1. 顧客の詳細ページで、トップメニューの「**[!UICONTROL Create Order]**」をクリックします。
1. [!UICONTROL FR French] ストアを選択し、利用可能な製品を注文に追加します。
1. チェックアウト時に必要な詳細を入力し、「**[!UICONTROL Get shipping methods and rates]**」をクリックします。
1. **[注文を送信]** をクリックして注文します。

<u> 期待される結果 </u>:

管理者は、正しいレイアウトを使用して、注文確認ページまたはありがとうページにリダイレクトされます。

<u> 実際の結果 </u>:

管理者は、レイアウトが壊れたページにリダイレクトされます。 レイアウトは、ページを更新した後にのみ修正されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
