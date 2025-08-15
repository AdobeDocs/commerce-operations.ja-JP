---
title: ACSD-61969：大文字または小文字で設定されたクーポンコードを入力する必要があります
description: ACSD-61969 パッチを適用すると、大文字または小文字で設定されたとおりにクーポンコードを入力する必要があるAdobe Commerceの問題が修正されます。
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969：大文字または小文字で設定されたクーポンコードを入力する必要があります

ACSD-61969 パッチは、ユーザーが大文字または小文字で設定されているとおりにクーポンコードを入力する必要がある問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-61969 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バックエンドから適用する場合は、大文字または小文字で設定されたとおりにクーポンコードを入力する必要があります。 管理注文作成内では大文字と小文字が区別されますが、ストアフロントでは大文字と小文字は区別されません。

<u> 再現手順 </u>:

1. 特定のクーポン *[!UICONTROL Cart Price Rule]* TEST *を持つ* ールを作成します。 クーポンコードが大文字であることを確認してください。
1. 管理者で注文を作成します。
1. *フィールドに* test *[!UICONTROL Apply Coupon Code]* を追加し、フィールドの近くにある矢印をクリックしてクーポンを適用します。
1. 結果を確認します。

<u> 期待される結果 </u>:

クーポンが正常に適用されました。 クーポンフィールドでは大文字と小文字が区別されません。

<u> 実際の結果 </u>:

クーポンは適用されません。 次のエラーが表示されます。

*「test」クーポンコードが無効です。 コードを確認して、もう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
