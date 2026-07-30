---
title: 'ACSD-54989: [!UICONTROL Enable Purchase Orders]が「はい」に、[!UICONTROL Purchase Order]が「いいえ」に設定されている場合、会社管理者は注文できません'
description: ACSD-54989 パッチを適用して、[!UICONTROL Enable Purchase Orders]が「はい」に、[!UICONTROL Purchase Order]が「いいえ」に設定されている場合に会社管理者が注文を行うことができないAdobe Commerceの問題を修正します。
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-54989: *[!UICONTROL Enable Purchase Orders]*&#x200B;が&#x200B;*Yes*&#x200B;に設定され、*[!UICONTROL Purchase Order]*&#x200B;が&#x200B;*No*&#x200B;に設定されている場合、会社管理者は注文できません

ACSD-54989 パッチは、**[!UICONTROL Enable Purchase Orders]**&#x200B;が&#x200B;*Yes*&#x200B;に、**[!UICONTROL Purchase Order]**&#x200B;が&#x200B;*No*&#x200B;に設定されている場合に注文を配置できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-54989です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Enable Purchase Orders]**&#x200B;が&#x200B;*Yes*&#x200B;に設定され、**Purchase Order**&#x200B;が&#x200B;*No*&#x200B;に設定されている場合、会社の管理者は注文を行うことはできません。

<u>前提条件</u>:

[!DNL B2B] モジュールをインストールします。

<u>複製する手順</u>:

1. 会社を有効にし、[!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *No*のままにします。
1. 100の価格でシンプルな商品を作成します。
1. 管理者を通じて新しい会社を作成します。
1. [!UICONTROL **発注を有効にする**]&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. ストアフロントの会社管理者としてログインします。
1. 作成したシンプルな商品をカートに追加します。
1. チェックアウトページに進み、**[!UICONTROL Place Order]**&#x200B;をクリックして購入を完了します。

<u>期待される結果</u>:

正常に注文できます。

<u>実際の結果</u>:

**[!UICONTROL My Account]** ページが開き、注文は行われません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
