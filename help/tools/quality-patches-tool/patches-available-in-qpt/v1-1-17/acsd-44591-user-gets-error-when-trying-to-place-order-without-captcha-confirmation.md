---
title: ACSD-44591:CAPTCHA確認なしで注文するとエラーが発生する
description: ACSD-44591 パッチは、CAPTCHA確認なしで注文を行おうとしたときにユーザーがエラーを受け取る問題を解決します。
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-44591:CAPTCHA確認なしで注文するとエラーが発生する

ACSD-44591 パッチは、CAPTCHA確認なしで注文を行おうとしたときにユーザーがエラーを受け取る問題を解決します。
このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17がインストールされている場合に使用できます。パッチ IDはACSD-44591です。この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

CAPTCHA確認なしで注文しようとすると、ユーザーにエラーが発生します。

<u>複製する手順</u>:

1. Google ReCaptcha v2を設定します（私はロボットではありません）。
1. チェックアウト用にReCaptchaを有効にします。
1. ReCaptchaをクリックせずに注文してみてください。
1. ReCaptchaが見つからないというエラーメッセージ（*ReCaptchaの検証に失敗しました、*）が表示されたら、**ReCaptcha**&#x200B;をクリックして、注文を試してください。

<u>期待される結果</u>:

誤ったReCaptchaで注文することはありません。

<u>実際の結果</u>:

次のエラーが表示されます。

* *ReCaptchaの検証に失敗しました。もう一度やり直してください*
* *ID = 1*&#x200B;のそのような買い物かごはありません

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
