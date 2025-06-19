---
title: ACSD-51036:REST API の同時呼び出し時の競合状態によって、出荷ステータスが上書きされます
description: ACSD-51036 パッチを適用すると、同時に REST API が呼び出され、注文された商品テーブルの配送ステータスが上書きされる際に競合状態が発生するAdobe Commerceの問題を修正できます。
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036:REST API の同時呼び出し時の競合状態により、順序付き項目テーブルで出荷ステータスが上書きされます

ACSD-51036 パッチでは、REST API の同時呼び出し時の競合状態によって、順序付き項目テーブルの出荷ステータスが上書きされる問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.31 がインストールされている場合に使用できます。 パッチ ID は ACSD-51036 です。 この問題はAdobe Commerce 2.4.5 で修正されていることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API の同時呼び出し時の競合状態により、順序付き項目テーブルの出荷ステータスが上書きされます。

<u> 再現手順 </u>:

1. 2 つの項目で注文を作成します。
1. 請求書項目 A.
1. REST API を介して品目 A の払い戻しリクエストを同時に送信すると同時に、品目 B の出荷リクエストを送信します。
1. **[!UICONTROL Admin Panel]** の注文に移動します。

<u> 期待される結果 </u>

*[!UICONTROL Items]* の注文テーブルの品目 B に対して、*[!UICONTROL Shipped 1]* のステータスが存在する必要があります。

<u> 実績 </u>

*[!UICONTROL Items]* 注文テーブルの品目 B に *[!UICONTROL Shipped 1]* のステータスがありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
