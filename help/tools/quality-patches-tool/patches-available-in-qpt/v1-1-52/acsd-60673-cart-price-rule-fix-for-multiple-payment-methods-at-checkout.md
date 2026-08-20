---
title: ACSD-60673：チェックアウト時に複数の支払い方法で修正された[!UICONTROL Cart Price Rule]の問題
description: 支払い方法の条件を使用する[!UICONTROL Cart Price Rule]からの割引が必ずしも合計に表示されないAdobe Commerceの問題を修正するには、ACSD-60673 パッチを適用します。
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-60673：チェックアウト時に複数の支払い方法で修正された[!UICONTROL Cart Price Rule]の問題

ACSD-60673 パッチでは、支払い方法の条件を使用する[!UICONTROL Cart Price Rule]からの割引が必ずしも合計に表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-60673です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チェックアウト時の複数の支払い方法の[!UICONTROL Cart Price Rule]が、特定の支払い方法に正しく適用されません。

<u>前提条件</u>

「**[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]**」および「**[!UICONTROL Bank Transfer]**」が有効になっていることを確認します。

<u>複製する手順</u>:

1. **[!UICONTROL Multiple Payment Methods]**&#x200B;を有効にします。
1. *[!UICONTROL Cart Price Rule]*&#x200B;を作成します。
   * **[!UICONTROL Conditions]**&#x200B;を設定：支払い方法を&#x200B;**[!UICONTROL Money Order]** （または銀行振込）に設定
   * 全商品の&#x200B;**[!UICONTROL Actions]** = *25%*&#x200B;割引を選択
1. バーチャルな商品を作成する。
1. 新しい見積もりとゲスト顧客&#x200B;*[!UICONTROL Status]*&#x200B;をコピーするには、ストアフロントに移動してCookieをクリアします。
1. バーチャル商品をカートに追加する。
1. *チェックアウト*&#x200B;に進みます。
1. *[!UICONTROL Cart Price Rule]*&#x200B;で定義された支払い方法をクリックします。
1. *[!UICONTROL Billing Address]*&#x200B;を更新します。
1. 割引が合計金額に表示されていることを確認します。
1. チェックボックスをクリックして、支払い方法を変更します。
1. 割引が表示されていることを確認します。

<u>期待される結果</u>:

割引は、チェックボックスをクリックして該当する支払い方法に切り替えた後、*合計*&#x200B;に表示されます。

<u>実際の結果</u>:

割引は&#x200B;*合計*&#x200B;に表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
