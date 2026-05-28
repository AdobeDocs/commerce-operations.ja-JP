---
title: ACSD-50336：製品アラートメールが送信されない
description: ACSD-50336 パッチを適用して、商品の再入荷や価格の変更の際に商品アラートメールが送信されないAdobe Commerceの問題を修正します。
feature: Communications, Personalization, Products
role: Admin
exl-id: 45dd12af-a3b2-4cfa-be90-af1c7b5f74b3
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-50336：製品アラートメールが送信されない

ACSD-50336 パッチでは、商品の再入荷や価格の変更の際に商品アラートメールが送信されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-50336です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

商品の再入荷や価格の変更では、商品アラートメールは送信されません。

<u>前提条件</u>:

商品が在庫に戻ったときに商品アラートを設定できます。

<u>複製する手順</u>:

1. ストアフロントに顧客としてログインします。
1. 在庫がない商品を開きます。
1. 製品が&#x200B;*再入荷*&#x200B;した時点で通知を受け取るには、購読します。
1. 商品を[!UICONTROL Admin]から&#x200B;_再入荷_&#x200B;に更新します。

<u>期待される結果</u>:

商品の再入荷&#x200B;*について、お客様にメール通知が送信されます。*

<u>実際の結果</u>:

商品が&#x200B;*再入荷*&#x200B;されたことに関する電子メールのお知らせがお客様に届きません。 ログに次のエラーが表示されます。

```text
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] []
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
