---
title: ACSD-61134：チェックアウトワークフローで [!UICONTROL Braintree Vault] 支払い方法が自動的に選択解除される
description: ACSD-61134 パッチを適用すると、買い物客が「*[!UICONTROL Braintree Vault]*」チェックボックスの選択を解除して請求先住所を更新したときに、チェックアウトワークフローで「*[!UICONTROL My billing and shipping address are the same]*」支払い方法が自動的に選択解除されるAdobe Commerceの問題を解決できます。
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134：チェックアウトワークフローで *[!UICONTROL Braintree Vault]* 支払い方法が自動的に選択解除される

ACSD-61134 パッチは、買い物客が *[!UICONTROL My billing and shipping address are the same]* チェックボックスの選択を解除して請求先住所を更新した際に、チェックアウトワークフローで *[!UICONTROL Braintree Vault]* の支払い方法が自動的に選択解除される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61134 です。 この問題はAdobe Commerce 2.4.7-beta1 で修正される予定です。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チェックアウ *[!UICONTROL Braintree Vault]* ワークフローで、支払い方法の選択が自動的に解除されます。

<u> 再現手順 </u>:

1. *[!UICONTROL Vault]* が有効になっている *[!DNL Braintree]* 支払い方法を設定します。
1. カードをチェックアウトして *[!UICONTROL Vault]* に保存します。
1. 別の商品をチェックアウトします。
1. *[!UICONTROL Shipping]* のページで新しい配送先住所を追加して、2 つの住所を選択できるようにします。
1. *[!UICONTROL Payment]* のページで、お支払い方法を選択し、「**[!UICONTROL My billing and shipping addresses are the same]**」をクリックします。

<u> 期待される結果 </u>:

選択した支払方法は選択されたままになります。

<u> 実際の結果 </u>:

選択した支払方法はオフです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
