---
title: ACSD-56280：ギフトレジストリの購入が完了しない
description: ACSD-56280 パッチを適用して、ギフトレジストリの購入が完了しないAdobe Commerceの問題を修正します
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56280：ギフトレジストリの購入が完了しない

>[!NOTE]
>
>このパッチは[ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md)に置き換えられます。

ACSD-56280 パッチは、ギフトレジストリの購入が完了しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-56280です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ギフトレジストリの購入は完了していません。

<u>複製する手順</u>:

1. お客様としてログインし、ギフトレジストリに&#x200B;**[!UICONTROL product]**&#x200B;を追加します。
1. ギフトレジストリリンクを共有します。
1. 別のブラウザー/シークレットウィンドウでギフトレジストリリンクを開きます。
1. 数量を追加し、商品をカートに追加します。
1. **[!UICONTROL Checkout Page]**&#x200B;に移動し、**[!UICONTROL shipping method]**&#x200B;を選択します（登録者から提供された配送先住所が既に選択されているため）。
1. 支払い方法を選択します。
1. 「Place Order」ボタンをクリックします。

<u>期待される結果</u>:

注文する必要があります。

<u>実際の結果</u>:

注文は行われず、表示されるエラーは`Call to a member function getUpdatedQty() on null`です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
