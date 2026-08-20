---
title: MDVA-42509：クイックオーダー用にCSVをアップロードできませんでした。その結果、「Cookieを送信できません」エラーが発生する
description: MDVA-42509 パッチは、CSVを迅速な注文のためにアップロードできなかった場合、「Cookieを送信できません」エラーが発生する問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16がインストールされている場合に利用できます。 パッチ IDはMDVA-42509です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# MDVA-42509：クイックオーダー用にCSVをアップロードできませんでした。その結果、「Cookieを送信できません」エラーが発生する

MDVA-42509 パッチは、CSVを迅速な注文のためにアップロードできなかったため、*Cookieを送信できない* エラーが発生する問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16がインストールされている場合に使用できます。 パッチ IDはMDVA-42509です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

CSVを使用して多数の製品を含むクイックオーダーを作成すると、Cookie エラーが表示されます。*Cookieを送信できません*

<u>複製する手順</u>:

1. **ストア** > **設定** > **設定** > **一般** > **B2B機能**&#x200B;に移動して、クイックオーダーを有効にします。
1. 顧客アカウントを作成し、上部リンクの&#x200B;**クイックオーダー**&#x200B;に移動します。
1. 100以上のSKUを持つCSVを使用して、クイック注文を作成してみてください。

<u>期待される結果</u>:

大量のSKUを使用してクイック注文を作成できます。

<u>実際の結果</u>:

Cookie サイズに関連するエラーメッセージが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
