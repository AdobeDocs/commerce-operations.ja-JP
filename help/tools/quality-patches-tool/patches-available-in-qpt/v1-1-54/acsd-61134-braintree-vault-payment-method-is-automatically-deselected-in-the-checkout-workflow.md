---
title: 'ACSD-61134: [!UICONTROL Braintree Vault]支払い方法がチェックアウトワークフローで自動的に選択解除される'
description: 「*[!UICONTROL My billing and shipping address are the same]*」チェックボックスの選択を解除して買い物客が請求先住所を更新すると、チェックアウトワークフローで*[!UICONTROL Braintree Vault]*支払い方法が自動的に選択解除されるAdobe Commerceの問題を解決するには、ACSD-61134 パッチを適用します。
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]*&#x200B;支払い方法がチェックアウトワークフローで自動的に選択解除される

ACSD-61134 パッチは、買い物客が&#x200B;*[!UICONTROL My billing and shipping address are the same]* チェックボックスの選択を解除して請求先住所を更新すると、チェックアウトワークフローで&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;支払い方法が自動的に選択解除される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61134です。 この問題は、Adobe Commerce 2.4.7-beta1で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Braintree Vault]*&#x200B;支払い方法は、チェックアウトワークフローで自動的に選択解除されます。

<u>複製する手順</u>:

1. *[!UICONTROL Vault]*&#x200B;が有効になっている&#x200B;*[!DNL Braintree]*&#x200B;支払い方法を設定します。
1. チェックアウトして&#x200B;*[!UICONTROL Vault]*&#x200B;にカードを保存します。
1. 別の商品をチェック。
1. *[!UICONTROL Shipping]* ページで、新しい配送先住所を追加して、2つの住所を選択できるようにします。
1. *[!UICONTROL Payment]* ページで、支払い方法を選択し、**[!UICONTROL My billing and shipping addresses are the same]**&#x200B;をクリックします。

<u>期待される結果</u>:

選択した支払い方法は選択されたままです。

<u>実際の結果</u>:

選択した支払い方法はオフになっています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
