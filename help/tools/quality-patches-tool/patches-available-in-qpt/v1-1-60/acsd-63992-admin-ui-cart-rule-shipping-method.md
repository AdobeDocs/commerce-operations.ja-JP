---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] （管理UIでクーポンと配送方法の条件エラー）'
description: クーポンと配送方法に基づく条件を含む[!UICONTROL Cart Price Rule]がAdmin UIを通じて正しく適用できないAdobe Commerceの問題を修正するには、ACSD-63992 パッチを適用します。
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63992: [!UICONTROL Cart Price Rule] （管理UIでクーポンと配送方法の条件エラー）

ACSD-63992 パッチでは、Admin UIを使用して、クーポンと配送方法に基づく条件を含む[!UICONTROL Cart Price Rule]を正しく適用できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60がインストールされている場合に利用できます。 パッチ IDはACSD-63992です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カートルールに&#x200B;**[!UICONTROL Conditions]** セクション内の配送方法の条件が含まれている場合、管理パネルで注文を作成する際に、関連するクーポンコードが適用されません。 代わりに、次のエラーが表示されます。

_&lt;> クーポンコードが無効です。 コードを確認して、もう一度やり直してください。_

<u>複製する手順</u>:

1. カート価格ルールを作成し、その条件を記述します。
   * *[!UICONTROL Conditions]*&#x200B;の下：配送方法を含める条件を追加します（例：*[!UICONTROL Flat Rate]*）。
   * *[!UICONTROL Rule Information]*&#x200B;の下：**[!UICONTROL Coupon]**&#x200B;を&#x200B;*[!UICONTROL Specific Coupon]*&#x200B;に設定し、**[!UICONTROL Coupon Code]**&#x200B;を&#x200B;*TEST*&#x200B;として入力します。
1. 管理パネルから新しい注文を作成し、**[!UICONTROL Apply Coupon]** フィールドにクーポンコード *TEST*&#x200B;を入力します。

<u>期待される結果</u>:

クーポンが正常に適用されます。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。

```text
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
