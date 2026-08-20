---
title: ACSD-65164：単一のチェックボックスカスタムオプションを選択した状態で設定可能な製品を並べ替える際にエラーメッセージが表示される
description: 「ACSD-65164 パッチ」を適用して、「1つのチェックボックスカスタムオプションを選択した設定可能な商品を再注文すると、現在選択されている商品オプションの一部が利用できない*」というエラーメッセージが表示されるAdobe Commerceの問題を修正します。
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-65164：単一のチェックボックスカスタムオプションを選択した状態で設定可能な製品を並べ替える際にエラーメッセージが表示される

ACSD-65164 パッチは、選択したチェックボックスのカスタムオプションを1つ選択して設定可能な製品を再注文する際に、エラーメッセージ *選択した項目オプションの一部が現在使用できない*&#x200B;が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62がインストールされている場合に利用できます。 パッチ IDはACSD-65164です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

選択されたチェックボックスのカスタムオプションが1つだけの設定可能な製品を並べ替えると、システムはエラーメッセージを返します：*選択した項目オプションの一部は現在利用できません*。

### レプリケーションの手順：

1. 管理パネルで、**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**&#x200B;に移動します。
1. **[!UICONTROL Customizable Options]**&#x200B;の下に、*チェックボックス* オプションを追加します。
   * チェックボックスオプションを&#x200B;*必須*&#x200B;に設定します。
   * 2つのオプション値を追加します。
1. ストアフロントに移動し、登録済みの顧客としてログインします。
1. 1つのチェックボックスオプションを選択して、商品をカートに追加します。
1. **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**&#x200B;に移動します。
1. **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]**&#x200B;に移動して、同じ製品を追加します。

**期待される結果：**

商品はショッピングカートに正常に追加される必要があります。

**実際の結果：**

エラーメッセージが表示されます。

*SKU 「24-MB01」の商品をショッピングカートに追加できませんでした。選択した商品オプションの一部は現在利用できません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
