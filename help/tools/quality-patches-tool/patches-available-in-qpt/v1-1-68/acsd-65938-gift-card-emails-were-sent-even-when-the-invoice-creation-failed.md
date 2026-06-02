---
title: ACSD-65938：請求書の作成に失敗した場合でも、ギフトカードの電子メールが送信される
description: ACSD-65938 パッチを適用して、請求書が正常に保存され、コミットされる前にギフトカードの電子メールが送信されたAdobe Commerceの問題を修正し、請求書が適切に保存された後に電子メールがトリガーされるようにします。
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: a6e85c9a-cbf6-4b4a-927b-43ec2ce827fc
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-65938：請求書の作成に失敗した場合でも、ギフトカードの電子メールが送信される

ACSD-65938 パッチは、請求書が正常に保存され、コミットされる前にギフトカードの電子メールが送信された問題を解決します。 この修正により、請求書が正常に保存された後にのみ電子メールがトリガーされるようになりました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-65938です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

請求書が正常に作成され保存されたことを確認する前に、ギフトカードの電子メールが送信され、請求書の作成が失敗した場合でも電子メールが送信されます。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** パネルにログインします。
2. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**&#x200B;に移動し、**[!UICONTROL Generate Gift Card Account when Order Item is]**&#x200B;を&#x200B;*請求済み*&#x200B;に設定します。
3. 新しいギフトカード商品を作成する。
4. ギフトカート商品をカートに追加して&#x200B;**[!UICONTROL checkout]**&#x200B;に進みます。 支払い方法として&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;を使用できます。
5. 注文する。
6. 注文処理中に例外をシミュレートするように`OrderRepository`を変更します。
7. 次のペイロードを使用して`rest/default/V1/order/<ORDER_ID>/invoice`にPOST リクエストを送信します。

   ```json
   {
     "capture": true,
     "notify": true
   }
   ```


<u>期待される結果</u>:

請求書の作成に失敗した場合、ギフトカードの電子メールを送信しないでください。

<u>実際の結果</u>:

請求書の作成に失敗した場合でも、ギフトカードの電子メールが送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
