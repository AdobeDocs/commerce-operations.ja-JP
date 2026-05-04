---
title: ACP2E-3918：実店舗での受け取りを使用している企業のお客様のチェックアウトの失敗
description: ACP2E-3918 パッチを適用して、デフォルトの請求先住所なしで実店舗で受け取りを使用しているログイン企業のお客様のチェックアウトが失敗するAdobe Commerceの問題を修正します。
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACP2E-3918：実店舗での受け取りを使用している企業のお客様のチェックアウトの失敗

ACP2E-3918 パッチは、デフォルトの請求先住所なしで実店舗での受け取りを使用しているログイン企業のお客様のチェックアウトが失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACP2E-3918です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

デフォルトの住所を持たないログイン企業のお客様が、実店舗での受け取りを使用して注文を行おうとすると、チェックアウトが失敗します。

<u>複製する手順</u>:

1. **[!UICONTROL Purchase Orders]**&#x200B;を有効にします。
1. **[!UICONTROL Company]**&#x200B;を作成し、その&#x200B;**[!UICONTROL Purchase Orders]**&#x200B;を有効にします。
1. アドレスを保存せずに&#x200B;**[!UICONTROL Company User]**&#x200B;を作成します。
1. **[!UICONTROL In-Store Delivery]**&#x200B;の配送方法を有効にします。
1. 在庫ソースを追加。
1. 在庫在庫の追加。
1. 商品に在庫を割り当てる：
1. フロントエンドでは、会社のユーザーとしてログインします。
1. 商品を&#x200B;**[!UICONTROL Cart]**&#x200B;に追加します。
1. チェックアウトに進みます。
1. 発送手順で&#x200B;**[!UICONTROL In-Store Pick Up]**&#x200B;を選択します。
1. お支払いに進みます。

<u>期待される結果</u>:

決済手順はチェックアウト中に正常に読み込まれ、ブラウザーコンソールにエラーは表示されません。

<u>実際の結果</u>:

支払い手順が読み込まれず、ブラウザーコンソールに次のJavaScript エラーが表示されます。

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
