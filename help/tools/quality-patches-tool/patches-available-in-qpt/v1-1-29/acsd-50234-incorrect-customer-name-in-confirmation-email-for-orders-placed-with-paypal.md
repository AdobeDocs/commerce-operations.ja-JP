---
title: 'ACSD-50234: [!DNL PayPal]を使用して行われた注文の確認メールに含まれる顧客名が正しくありません'
description: ACSD-50234 パッチを適用して、 [!DNL PayPal]を使用して行われた注文の確認メールに顧客名が誤って表示されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-50234: [!DNL PayPal]を使用して行われた注文の確認メールに含まれる顧客名が正しくありません

ACSD-50234 パッチは、[!DNL PayPal]を使用して行われた注文の確認メールに顧客名が正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-50234です。 この問題はAdobe Commerce 2.4.5で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL PayPal]を使用して発注された注文の確認メールに、間違った顧客名が表示されています。

<u>複製する手順</u>

1. **[!UICONTROL PayPal Express Checkout]**&#x200B;を有効にします。
1. ゲストとしてフロントエンドに移動します。
1. 商品をカートに追加する：
1. **[!UICONTROL PayPal Express Checkout]**&#x200B;を支払い方法として使用してチェックアウトします。
1. 注文確認メールをご確認ください。

<u>期待される結果</u>

注文確認メール、請求書メール、および出荷関連のすべてのメールは、お客様の名前に宛てられます。

<u>実際の結果</u>

注文確認メール、請求書メール、および出荷関連のすべてのメールは、*ゲスト*&#x200B;宛てに送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
