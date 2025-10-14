---
title: ACSD-63870：会社のステータスが変更された際、顧客が適切にログアウトしなかった
description: アクティブなカスタマーセッション中に会社のステータスが変更されると、会社の顧客が適切にログアウトされないAdobe Commerceの問題を修正するために、ACSD-63870 パッチを適用します。
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870：会社のステータスが変更された際、顧客が適切にログアウトしなかった

ACSD-63870 パッチを使用すると、アクティブな顧客セッション中に会社のステータスが変更された場合に、会社の顧客が適切にログアウトされない問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-63870 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

アクティブな顧客セッション中に会社のステータスが変更されると、顧客ログアウトに失敗する。

<u> 再現手順 </u>:

1. B2B 機能を有効にします。
1. シンプルな製品を作成します。
1. 新しい会社を作成し、*アクティブ* としてマークします。
1. 会社ユーザーとしてログインし、商品を買い物かごに追加します。
1. [!UICONTROL Shipping Address] の手順までチェックアウトに進みます。 アドレスを入力しないでください。
1. 管理者に移動し、会社ステータスを *承認待ち* に変更します。
1. フロントエンドに戻り、配送先住所を入力します。

<u> 期待される結果 </u>:

顧客はログアウトされました。

<u> 実際の結果 </u>:

* ユーザーに *エラーが発生しました* というエラーが表示される。
* `var/log/exception.log` には次が含まれます。

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## パッチのインストール後に必要な追加手順

（この節はオプションです。問題を修正するためにパッチを適用した後に必要な手順が含まれる場合があります）。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
