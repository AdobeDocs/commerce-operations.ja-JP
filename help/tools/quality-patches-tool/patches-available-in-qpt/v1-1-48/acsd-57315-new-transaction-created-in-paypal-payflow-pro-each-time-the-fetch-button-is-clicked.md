---
title: ACSD-57315:「取得」ボタンをクリックするたびに、新しいトランザクショ  [!DNL PayPal Payflow Pro]  が作成されます
description: ACSD-57315 パッチを適用すると、 [!DNL PayPal Payflow Pro]  ールバーのトランザクションを表示画面で「取得」ボタンをクリックするたびに新しいトランザクションが作成されるAdobe Commerceの問題が修正されます。[!UICONTROL Admin] の例を以下に示します。
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315:「取得」ボタンをクリックするたびに、[!DNL PayPal Payflow Pro] に新しいトランザクションが作成されます

ACSD-57315 パッチでは、[!DNL PayPal Payflow Pro] ージのトランザクションの表示画面で「取得」ボタンをクリックするたびに [!UICONTROL Admin] に新しいトランザクションが作成される問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-57315 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL PayPal Payflow Pro] ージのトランザクションを表示画面で「取得」ボタンをクリックするたびに、[!UICONTROL Admin] に新しいトランザクションが作成されます。

<u> 再現手順 </u>:

1. [!DNL PayPal Payflow Pro] の設定
1. トランザクションメソッドを *[!UICONTROL Sale]* に設定します。
1. *クレジットカード* を使用して注文します。
1. [!UICONTROL Admin] からトランザクションを開きます。
1. 「**[!UICONTROL Fetch]**」ボタンをクリックします。
1. 注文 [!DNL PayPal] 関連するトランザクションの勘定を確認します。

<u> 期待される結果 </u>:

新しい支払トランザクションは作成されません。

<u> 実際の結果 </u>:

既に支払いが行われた注文に対して、新しい支払いトランザクションが作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
