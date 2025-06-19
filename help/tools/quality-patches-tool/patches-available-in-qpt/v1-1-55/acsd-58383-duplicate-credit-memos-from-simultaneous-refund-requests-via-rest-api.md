---
title: 'ACSD-58383: [!DNL REST API] を介した同時払い戻しリクエストからの複製クレジットメモ'
description: ACSD-58383 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、同時に実行される 2 つの同一のリクエストを使用して  [!DNL REST API]  経由で払い戻しを行うと、重複したクレジットメモが作成されます。
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383:[!DNL REST API] を介した同時払い戻しリクエストからの複製クレジットメモ

ACSD-58383 パッチは、同時に実行される 2 つの同一のリクエストで [!DNL REST API] を介して払い戻しを発行すると、クレジットメモが重複する問題を修正します。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58383 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

クレジット メモの重複は、同時に作成された 2 つの払い戻しによって発生します。

<u> 再現手順 </u>:

1. Commerce [!UICONTROL Admin] で [!DNL Paypal Express] を設定します。
1. 支払いアクションを *販売* に設定します。
1. [!DNL PayPal] サンドボックス web サイトで [!DNL PayPal] IPN （即時支払い通知）を設定します。
1. [!DNL PayPal] Sandbox web サイトで払い戻しを発行します。
1. 開発者ツールを使用して [!DNL PayPal] からの IPN メッセージをエミュレートします。 IPN はクレジット・メモを作成する必要があります。
1. [!DNL API] 呼び出しを使用して 2 番目のクレジットメモを作成します。

<u> 期待される結果 </u>:

同じ品目に対して作成されるクレジット・メモは 1 つのみです。


<u> 実際の結果 </u>:

同じ商品に対して 2 つのクレジットメモが作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
