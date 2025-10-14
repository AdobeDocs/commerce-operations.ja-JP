---
title: ACSD-63992：管理 UI のクーポンおよび発送方法の条件に関するエラーの [!UICONTROL Cart Price Rule]
description: ACSD-63992 パッチを適用すると、管理 UI からクーポンの [!UICONTROL Cart Price Rule] と発送方法に基づく条件を正しく適用できないAdobe Commerceの問題を修正できます。
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-63992：管理 UI のクーポンおよび発送方法の条件に関するエラーの [!UICONTROL Cart Price Rule]

ACSD-63992 パッチは、クーポンの [!UICONTROL Cart Price Rule] と発送方法に基づく条件を、管理 UI から正しく適用できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 がインストールされている場合に使用できます。 パッチ ID は ACSD-63992 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

買い物かごルールの「**[!UICONTROL Conditions]**」セクションに発送方法の条件が含まれている場合、管理パネルを使用して注文を作成する際、関連するクーポンコードは適用されません。 代わりに、次のエラーが表示されます。

_&lt;> クーポン コードが無効です。 コードを確認して、もう一度試してください。_

<u> 再現手順 </u>:

1. 買い物かご価格ルールを作成し、その条件を説明します。
   * *[!UICONTROL Conditions]* の下：発送方法を含めるための条件（例：*[!UICONTROL Flat Rate]*）を追加します。
   * *[!UICONTROL Rule Information]* の下で、**[!UICONTROL Coupon]** を *[!UICONTROL Specific Coupon]* に設定し、**[!UICONTROL Coupon Code]** TEST *として* と入力します。
1. Admin Panel から新しい注文を作成し、「*」フィールドにクーポンコード* TEST **[!UICONTROL Apply Coupon]** を入力します。

<u> 期待される結果 </u>:

クーポンが正常に適用されました。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
