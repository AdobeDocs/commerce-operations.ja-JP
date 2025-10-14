---
title: ACSD-54776:2 つ目の web サイト、ストア、ストア表示で、オフの [!UICONTROL Use Default Value] とデフォルト以外の製品フィールドの値が保存されない
description: ACSD-54776 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、2 番目の web サイト、ストア、ストアの表示に対して、オフの [!UICONTROL Use Default Value] フィールドとデフォルト以外の製品フィールドの値が保存されません。
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776：オフの *[!UICONTROL Use Default Value]* とデフォルト以外の製品フィールド値は保存されない

>[!NOTE]
>
>このパッチは、QPT 1.1.35 でリリースされた [ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) パッチに代わるものです。

ACSD-54776 パッチを使用すると、2 番目の web サイト、ストア、ストアの表示で、オフの **[!UICONTROL Use Default Value]** フィールドとデフォルト以外の製品フィールドの値が保存されない問題を修正できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 がインストールされている場合に使用できます。 パッチ ID は ACSD-54776 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p4、2.4.6 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

オフにした場合 *[!UICONTROL Use Default Value]* デフォルト以外の製品フィールドの値は、2 番目の web サイト、ストア、ストアの表示では保存されません。

<u> 再現手順 </u>:

1. バックエンドに移動し、**[!UICONTROL Stores]**/**[!UICONTROL All Stores]** に移動して、新しい web サイト、ストア、ストア表示を作成します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動してシンプルな製品を作成して保存し、**[!UICONTROL Product in Websites]** から両方の web サイトに製品を割り当てます。
1. 手順 2 で新しく作成したストア表示に範囲を変更します。
1. **[!UICONTROL Search Engine Optimization]** に移動し、**[!UICONTROL Use Default Value]**、[!UICONTROL Meta Title]、[!UICONTROL Meta Keywords] の [!UICONTROL Meta Description] のチェックボックスをオフにします。
1. フィールド（*[!UICONTROL Meta Title]*、*[!UICONTROL Meta Keywords]*、*[!UICONTROL Meta Description]*）からテキストを消去し、「**[!UICONTROL Save]**」をクリックします。
1. もう一度 **[!UICONTROL Search Engine Optimization]** に移動します。

<u> 期待される結果 </u>

フィールドとチェックボックスの値が保存されます。

<u> 実績 </u>

フィールドとチェックボックスの値は保存されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja>): Search for patches[!DNL Quality Patches Tool]」を参照してください。
