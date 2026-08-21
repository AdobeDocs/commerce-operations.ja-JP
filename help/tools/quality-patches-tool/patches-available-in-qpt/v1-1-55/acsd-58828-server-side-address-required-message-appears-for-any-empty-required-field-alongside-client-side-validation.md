---
title: 'ACSD-58828: クライアントサイドの検証と共に、空の必須フィールドに対してサーバーサイドの*address is required* メッセージが表示される'
description: ACSD-58828 パッチを適用して、クライアントサイドの検証メッセージと共に任意の必須フィールドが空のままの場合にサーバーサイド検証メッセージ *address is required*が表示されるAdobe Commerceの問題を修正します。
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-58828: クライアントサイドの検証と共に、空の必須フィールドに対してサーバーサイドの&#x200B;*アドレスが必要です* メッセージが表示されます

ACSD-58828 パッチは、必要なフィールドがクライアント側の検証メッセージと共に空のままになっている場合に、サーバー側の検証メッセージ *address is required*&#x200B;が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58828です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

必要なフィールドが空のままの場合、クライアントサイドの検証メッセージと共に、サーバー側の検証メッセージ *address is required*&#x200B;が表示されます。

再生の手順：

1. 顧客としてログインします。
1. 商品をカートに追加する。
1. チェックアウトに進みます。
1. 配送先住所はそのままにしておきます。
1. **[!UICONTROL Flat rate]**&#x200B;を選択し、**[!UICONTROL Next]**&#x200B;を選択します。
1. **[!UICONTROL My billing and shipping address are the same]**&#x200B;のチェックを外します。
1. ドロップダウンから新しいアドレスを追加します。
1. 任意の必須フィールドを空のままにして、**[!UICONTROL Update]**&#x200B;を選択します。

期待される結果：

エラーメッセージには、チェックアウトに必要な情報が欠落している、または正しくない情報が記載されています。

実際の結果：

エラー&#x200B;*アドレスが必要です。 入力して、もう一度やり直してください。* 表示します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
