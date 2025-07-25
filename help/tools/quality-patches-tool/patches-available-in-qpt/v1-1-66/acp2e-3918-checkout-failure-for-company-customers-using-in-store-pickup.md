---
title: ACP2E-3918：店舗での受け取りを使用している会社の顧客のチェックアウト エラー
description: デフォルトの請求先住所がない状態で店舗での受け取りを使用していて、ログインしている会社のお客様のチェックアウトが失敗するAdobe Commerceの問題を修正するために、ACP2E-3918 パッチを適用します。
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1295af44422ffbd67a3666f1a96a75af0a4e3c81
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACP2E-3918：店舗での受け取りを使用している会社の顧客のチェックアウト エラー

ACP2E-3918 パッチは、デフォルトの請求先住所なしで店舗での受け取りを使用しているログインした会社の顧客のチェックアウトが失敗する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3918 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デフォルトの住所を持たないログイン済みの会社の顧客が、店舗での受け取りを使用して発注書を送信しようとすると、チェックアウトが失敗します。

<u> 再現手順 </u>:

1. **[!UICONTROL Purchase Orders]** を有効にします。
1. **[!UICONTROL Company]** を作成し、**[!UICONTROL Purchase Orders]** を有効にします。
1. アドレスを保存せずに **[!UICONTROL Company User]** を作成します。
1. **[!UICONTROL In-Store Delivery]** 発送方法を有効にします。
1. 在庫ソースを追加します。
1. 在庫在庫を追加します。
1. 在庫を製品に割り当てます。
1. フロントエンドで、会社ユーザーとしてログインします。
1. **[!UICONTROL Cart]** に製品を追加します。
1. チェックアウトに進みます。
1. 出荷手順で「**[!UICONTROL In-Store Pick Up]**」を選択します。
1. 支払いに進みます。

<u> 期待される結果 </u>:

チェックアウト時に支払い手順が正常に読み込まれ、ブラウザーコンソールにエラーが表示されなくなります。

<u> 実際の結果 </u>:

支払いステップが読み込まれず、ブラウザーコンソールに次のJavaScript エラーが表示されます。

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
