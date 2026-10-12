---
title: 'ACSD-61522: *名*フィールドと姓*フィールドのメールアドレスが無効な注文確認を送信する'
description: ACSD-61522 パッチを適用して、ゲスト顧客の*[!UICONTROL First Name]*および*[!UICONTROL Last Name]*フィールドに電子メールアドレスを入力できるので、無効な注文確認メールが送信される可能性があるAdobe Commerceの問題を修正します。
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-61522: *名と姓* フィールドの電子メールアドレスで、無効な注文確認が送信される

ACSD-61522 パッチでは、ゲスト顧客の&#x200B;*[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]*&#x200B;のフィールドに電子メールアドレスを入力できるので、無効な注文確認メールが送信される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61522です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p9

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

このシステムでは、ゲスト顧客の&#x200B;*[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]*&#x200B;のフィールドに電子メールアドレスを入力できるので、無効な注文確認メールが送信されます。

<u>複製する手順</u>:

1. 任意の商品をゲスト顧客としてカートに追加します。
1. **[!UICONTROL Checkout]**&#x200B;に移動します。
1. *[!UICONTROL Email Address]* フィールドに&#x200B;*test1@example.com*&#x200B;を入力します。
1. *[!UICONTROL First Name]* フィールドに&#x200B;*<test2@example.com>*&#x200B;を入力します。
1. *[!UICONTROL Last Name]*&#x200B;に&#x200B;*<test3@example.com>*&#x200B;を入力します。
1. その他の必須フィールドに入力します。
1. 注文する。

<u>期待される結果</u>:

*[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]* フィールドでは電子メールアドレスを使用できません。

<u>実際の結果</u>:

1. 注文が行われます。
1. *[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]*&#x200B;個のフィールドが入力済みとして保存されます。
1. 注文確認メールは、3通のメールすべてに送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
