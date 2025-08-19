---
title: ACSD-65938：請求書の作成に失敗した場合でも送信されるギフトカードメール
description: ACSD-65938 パッチを適用すると、請求書が正常に保存およびコミットされる前にギフトカードの E メールが送信されるAdobe Commerceの問題を修正し、請求書が適切に保存された後に E メールがトリガーされるようにします。
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938：請求書の作成に失敗した場合でも送信されるギフトカードメール

ACSD-65938 パッチを適用すると、請求書が正常に保存およびコミットされる前にギフトカードの E メールが送信されていた問題が解決されます。 この修正により、請求書が正常に保存された後にのみメールがトリガーされるようになりました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-65938 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ギフトカードの E メールは、請求書が正常に作成および保存されたことを確認する前に送信され、請求書の作成に失敗した場合でも E メールが送信されていました。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]** パネルにログインします。
2. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Gift Cards]**/**[!UICONTROL Gift Card General Settings]** に移動し、「**[!UICONTROL Generate Gift Card Account when Order Item is]**」を「*請求済み*」に設定します。
3. 新しいギフトカード製品を作成します。
4. ギフトカート製品をカートに追加して、**[!UICONTROL checkout]** に進みます。 支払い方法として **[!UICONTROL Check/Money Order]** を使用できます。
5. 注文します。
6. 受注時の例外をシミュレートするために、`OrderRepository` を変更します。
7. 次のペイロードで POST リクエストを `rest/default/V1/order/<ORDER_ID>/invoice` に送信します。

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u> 期待される結果 </u>:

請求書の作成に失敗した場合は、ギフト カードの E メールを送信しないでください。

<u> 実際の結果 </u>:

ギフト カードの電子メールは、請求書の作成に失敗した場合でも送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
