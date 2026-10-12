---
title: 'ACSD-48318: ''system.log''の環境エミュレーションネストエラー'
description: 請求書メールが送信されるたびに「system.log」にエラーメッセージ *main.ERROR:Environment emulation nesting is not allowed*が表示されるAdobe Commerceの問題を修正するには、ACSD-48318 パッチを適用します。
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '329'
ht-degree: 0%
---
# ACSD-48318: `system.log`の環境エミュレーションのネスト エラー

ACSD-48318 パッチは、請求書の電子メールが送信されるたびに`system.log`にエラーメッセージ *main.ERROR:Environment エミュレーションネストが許可されない*&#x200B;が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-48318です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

請求書の電子メールが送信されるたびに、*環境エミュレーションのネストは許可されていません*&#x200B;というエラーメッセージが`system.log`に表示されます。

<u>複製する手順</u>:

1. 注文して請求書を生成します。
1. 管理者から請求書を開き、**[!UICONTROL Send Email]**&#x200B;をクリックします。
1. **[!UICONTROL Send Email]**&#x200B;をクリックして、*クレジットメモ*&#x200B;と&#x200B;*配送*&#x200B;に対して同じ手順を実行します。

<u>期待される結果</u>:

`system.log`にエラーはありません。

<u>実際の結果</u>:

`system.log`は&#x200B;*main.ERRORでフラッディングされています：環境エミュレーションのネストは許可されていません* エラー。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
