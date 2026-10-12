---
title: ACSD-63870：会社のステータス変更中に、お客様が適切にログアウトされない
description: アクティブなカスタマーセッション中に会社のステータスが変更されたときに、会社のお客様が適切にログアウトされないAdobe Commerceの問題を修正するには、ACSD-63870 パッチを適用します。
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '395'
ht-degree: 0%
---
# ACSD-63870：会社のステータス変更中に、お客様が適切にログアウトされない

ACSD-63870 パッチは、アクティブな顧客セッション中に会社のステータスが変更されたときに、会社の顧客が適切にログアウトされない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-63870です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アクティブな顧客セッション中に会社のステータスが変更された場合の顧客ログアウトの失敗。

<u>複製する手順</u>:

1. B2B機能の実現：
1. シンプルな商品の作成。
1. 新しい会社を作成し、*アクティブ*&#x200B;としてマークします。
1. 会社ユーザーとしてログインし、商品をカートに追加します。
1. [!UICONTROL Shipping Address] ステップまでチェックアウトに進みます。 アドレスは入力しないでください。
1. 管理者に移動し、会社のステータスを&#x200B;*承認待ち*&#x200B;に変更します。
1. フロントエンドに戻り、配送先住所を入力します。

<u>期待される結果</u>:

お客様がログアウトされました。

<u>実際の結果</u>:

* ユーザーに「*問題が発生しました*」エラーが表示されます。
* `var/log/exception.log`の内容：

  ```yaml
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

（このセクションはオプションです。問題を修正するためにパッチを適用した後に必要な手順がいくつかある場合があります）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
