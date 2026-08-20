---
title: ACSD-59229：古いX-Magento-Vary値による顧客グループ データの割り当て間違い
description: ACSD-59229 パッチを適用して、リクエストの古いX-Magento-Vary値が原因でカスタマーグループ関連の情報が間違ったセグメントに保存されるAdobe Commerceの問題を修正します。
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# ACSD-59229：古いX-Magento-Vary値による顧客グループ データの割り当て間違い

ACSD-59229 パッチは、リクエストの古いX-Magento-Vary値が原因で、カスタマーグループに関連する情報が間違ったセグメントに保存される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-59229です。 この問題は2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

リクエスト内の古いX-Magento-Vary値が原因で、カスタマーグループに関連する情報が間違ったセグメントに保存されます。

<u>前提条件</u>:

サンプルデータを含むAdobe Commerce B2Bがインストールされ、[!DNL Varnish]が設定されていることを確認します。

<u>複製する手順</u>:

1. [!DNL SKU 24-MB01]の高度な価格設定を行います：
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *卸売* = *$200*
      * *Retailer* = *$30*

1. 2つの顧客アカウントを作成する。
1. 両方の顧客を&#x200B;**Wholesale** グループに割り当てます。
1. 2つの異なるブラウザーセッションを開き、各顧客にログインします。
1. 各顧客の&#x200B;**[!UICONTROL 24-MB01]**&#x200B;製品ページに移動し、表示される価格が&#x200B;*$200*&#x200B;であることを確認します。
1. いずれかの顧客の顧客グループを&#x200B;**小売**&#x200B;に変更します。
1. 次のコマンドを使用してキャッシュをクリアします：`bin/magento cache:flush full_page`。
1. 各顧客の製品ページを更新します。

<u>期待される結果</u>:

1. 小売のお客様は、商品の&#x200B;*$30*&#x200B;の正しい価格を確認できます。
1. 卸売顧客は、製品の&#x200B;*$200*&#x200B;の正しい価格を確認できます。

<u>実際の結果</u>:

1. 小売のお客様は、商品の&#x200B;*$30*&#x200B;の正しい価格を確認できます。
1. 卸売顧客に、製品の&#x200B;*$30* （小売価格）の誤った価格が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
