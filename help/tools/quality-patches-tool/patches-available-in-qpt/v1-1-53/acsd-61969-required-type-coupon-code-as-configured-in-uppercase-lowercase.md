---
title: ACSD-61969：大文字または小文字で設定されたクーポンコードを入力する場合に必要です
description: 大文字または小文字で設定されているとおりにクーポンコードを入力する必要があるAdobe Commerceの問題を修正するには、ACSD-61969 パッチを適用します。
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-61969：大文字または小文字で設定されたクーポンコードを入力する場合に必要です

ACSD-61969 パッチでは、ユーザーが大文字または小文字で設定されたとおりにクーポンコードを入力する必要がある問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-61969です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バックエンドから適用する場合は、大文字または小文字で設定されたとおりにクーポンコードを入力する必要があります。 管理者向け注文作成では大文字と小文字が区別されますが、ストアフロントでは大文字と小文字が区別されません。

<u>複製する手順</u>:

1. 特定のクーポン *TEST*&#x200B;を使用して&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;を作成します。 クーポンコードが大文字になっていることを確認します。
1. 管理画面で注文を作成します。
1. *[!UICONTROL Apply Coupon Code]* フィールドに&#x200B;*test*&#x200B;を追加し、フィールドの近くにある矢印をクリックしてクーポンを適用します。
1. 結果の検証：

<u>期待される結果</u>:

クーポンが正常に適用されました。 クーポンフィールドでは、大文字と小文字は区別されません。

<u>実際の結果</u>:

クーポンは適用されません。 次のエラーが表示されます。

*「テスト」クーポンコードが無効です。 コードを確認して、もう一度やり直してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
