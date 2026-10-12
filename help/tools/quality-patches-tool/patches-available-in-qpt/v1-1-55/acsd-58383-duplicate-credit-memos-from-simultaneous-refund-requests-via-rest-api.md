---
title: 'ACSD-58383: [!DNL REST API]を介した同時払い戻し要求からクレジットメモを複製する'
description: ACSD-58383 パッチを適用して、[!DNL REST API]を介して払い戻しを行い、同時に実行される2つの同じリクエストを使用すると、重複したクレジットメモが作成されるAdobe Commerceの問題を修正します。
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '357'
ht-degree: 0%
---
# ACSD-58383: [!DNL REST API]を介した同時払い戻し要求からクレジットメモを複製する

ACSD-58383 パッチでは、2つの同じリクエストを同時に実行して[!DNL REST API]を介して払い戻しを発行すると、クレジットメモが重複する問題が修正されました。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58383です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

重複したクレジットメモは、同時に作成された2つの返金から作成されます。

<u>複製する手順</u>:

1. Commerce [!UICONTROL Admin]で[!DNL Paypal Express]を設定します。
1. 支払いアクションを&#x200B;*Sale*&#x200B;に設定します。
1. [!DNL PayPal] サンドボックス Web サイトで[!DNL PayPal] IPN （即時支払い通知）を設定します。
1. [!DNL PayPal] サンドボックス Web サイトで払い戻しを行います。
1. 開発者ツールを使用して[!DNL PayPal]からIPN メッセージをエミュレーションします。 IPNはクレジットメモを作成する必要があります。
1. [!DNL API]呼び出しを使用して2番目のクレジットメモを作成します。

<u>期待される結果</u>:

同じ項目に対して作成されるクレジットメモは1つだけです。


<u>実際の結果</u>:

同じ項目に対して2つのクレジットメモが作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
