---
title: 'ACSD-66179: [!UICONTROL Not Capture]支払いタイプの請求書をキャンセルすると、404 エラーページが表示される'
description: ACSD-66179 パッチを適用して、[!UICONTROL Not Capture]支払いタイプの請求書をキャンセルすると404 エラーページが表示されるAdobe Commerceの問題を修正します。
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-66179: [!UICONTROL Not Capture]支払いタイプの請求書をキャンセルすると、404 エラーページが表示される

ACSD-66179 パッチは、*[!UICONTROL Not Capture]*&#x200B;支払いタイプで作成された請求書をキャンセルすると、404 エラーページが表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66179です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p11 - 2.4.4-p14、2.4.5-p10 - 2.4.5-p13、2.4.6-p8 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Not Capture]*&#x200B;支払いタイプで作成された請求書をキャンセルすると、404 エラーページが表示されます。

<u>複製する手順</u>:

1. PayPal Express Checkoutなどの支払い方法を使用して注文を作成します。
1. 請求書を作成します。 **[!UICONTROL Amount]**&#x200B;を&#x200B;*[!UICONTROL Not Capture]*&#x200B;に設定し、請求書を送信します。
1. 作成した請求書を開き、**[!UICONTROL Cancel]**&#x200B;を選択します。

<u>期待される結果</u>:

1. 請求書は正常にキャンセルされました。
1. 成功メッセージが表示されます：*請求書をキャンセルしました。*

<u>実際の結果</u>:

404 エラーページが表示されます：*ページが見つかりません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
