---
title: ACSD-61522:「名」フィールドと「姓」フィールドのメールアドレスが無効な注文確認を送信する
description: ACSD-61522 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、ゲスト顧客の*[!UICONTROL First Name]*および*[!UICONTROL Last Name]* フィールドにメールアドレスを入力すると、無効な注文確認メールが送信されます。
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522:「名 *フィールドのメールアドレスが無効な注文確認を送信する*

ACSD-61522 パッチでは、ゲスト顧客の *[!UICONTROL First Name]* および *[!UICONTROL Last Name]* フィールドにメールアドレスを入力すると、無効な注文確認メールが送信される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61522 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p9

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

このシステムでは、ゲスト顧客の *[!UICONTROL First Name]* フィールドと *[!UICONTROL Last Name]* フィールドにメールアドレスを入力できるので、無効な注文確認メールが送信されることになります。

<u> 再現手順 </u>:

1. 任意の製品をゲスト顧客として買い物かごに追加します。
1. **[!UICONTROL Checkout]** に移動します。
1. *[!UICONTROL Email Address]* フィールドに *test1@example.com* を入力します。
1. *[!UICONTROL First Name]* フィールドに *<test2@example.com>* を入力します。
1. *[!UICONTROL Last Name]* に *<test3@example.com>* を入れなさい。
1. その他の必須フィールドに入力します。
1. 注文します。

<u> 期待される結果 </u>:

*[!UICONTROL First Name]* フィールドと *[!UICONTROL Last Name]* フィールドにはメールアドレスを使用できません。

<u> 実際の結果 </u>:

1. 注文が完了します。
1. *[!UICONTROL First Name]* および *[!UICONTROL Last Name]* フィールドは入力時に保存されます。
1. 注文確認メールが 3 通のメールすべてに送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
