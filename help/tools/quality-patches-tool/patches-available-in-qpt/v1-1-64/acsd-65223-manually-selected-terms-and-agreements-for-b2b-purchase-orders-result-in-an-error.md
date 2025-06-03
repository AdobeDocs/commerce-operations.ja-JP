---
title: 'ACSD-65223: B2B 発注書に対して手動で選択した条件と契約を実行すると、エラーが発生します'
description: ACSD-65223 パッチを適用すると、[!UICONTROL Purchase Orders] を使用して作成された注文が、チェックアウトに利用条件が必要な場合に、クレジットカードなどのオンライン支払い方法で完了できないAdobe Commerceの問題を修正できます。
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 57c0cb63f1e2c7b12d11b759eddf0d21b5db78b2
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ACSD-65223: B2B 発注書に対して手動で選択した条件と契約を実行すると、エラーが発生します

ACSD-65223 パッチは、**[!UICONTROL Purchase Orders]** を使用して作成された注文が、チェックアウトに利用条件が必要な場合に、クレジットカードなどのオンライン支払い方法で完了できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-65223 です。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） B2B 1.5.1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） B2B 1.5.1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文に利用条件が必要な場合に、[!UICONTROL Purchase Orders] を使用して作成した注文を確定しようとすると、クレジットカードなどのオンライン支払い方法を使用して注文することはできません。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]** に移動し、「**[!UICONTROL B2B Features]**」を選択します。
1. **[!UICONTROL Enable Company]** と **[!UICONTROL Enable Purchase Orders]** を *はい* に設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Terms and Conditions]** に移動し、新しい条件を作成します。 **[!UICONTROL Applied]** を *[!UICONTROL Manually]* に設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Checkout]** に移動し、**[!UICONTROL Enable Terms and Conditions]** を *はい* に設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Payment Methods]** に移動し、[!DNL Braintree] を設定します。
1. ストアフロントで、会社を作成します。
1. 管理者で、**[!UICONTROL Customers]**/**[!UICONTROL Companies]** に移動します。
1. 会社を承認し、**[!UICONTROL Purchase Orders]** を許可します。
1. フロントエンドで、アカウントにログインします。
1. 買い物かごに商品を追加します。
1. **[!UICONTROL Purchase Order]** を使用して注文します。
1. 顧客ダッシュボードで、「**[!UICONTROL Purchase Orders]**」タブをクリックします。
1. 新しい発注書から注文を作成します。 次に、支払い方法としてクレジットカードを選択します。
1. 条件に同意します。
1. 注文します。

<u> 期待される結果 </u>:

チェックアウトに利用条件が必要な場合、承認済発注に対してオンライン支払い方法を使用して注文を行うことができます。

<u> 実際の結果 </u>:

チェックアウトに利用条件が必要な場合、承認済み発注書に対してオンライン支払い方法を使用して注文することはできません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
