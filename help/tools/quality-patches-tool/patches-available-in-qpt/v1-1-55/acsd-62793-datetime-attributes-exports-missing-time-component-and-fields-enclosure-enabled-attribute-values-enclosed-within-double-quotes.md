---
title: ACSD-62793：の Datetime 属性は、欠落している時間コンポーネントを書き出します。 さらに、**[!UICONTROL Fields Enclosure]**が有効な場合、属性値は二重引用符で囲まれます
description: ACSD-62793 パッチを適用して、書き出されたデータの datetime 属性に時間コンポーネントが欠落しているAdobe Commerceの問題を修正してください。 さらに、**[!UICONTROL Fields Enclosure]**が有効になっている場合、*additional_attributes*列の属性値は二重引用符で囲まれます。
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-62793：の Datetime 属性は、欠落している時間コンポーネントを書き出します。 さらに、有効 **[!UICONTROL Fields Enclosure]** 場合、属性値を二重引用符で囲みます

ACSD-62793 パッチでは、書き出されたデータの datetime 属性に時間コンポーネントが欠落している問題が修正されています。 さらに、**[!UICONTROL Fields Enclosure]** が有効になっている場合、*additional_attributes* 列の属性値は二重引用符で囲まれます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-62793 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

書き出されたデータの datetime 属性には、時間コンポーネントは含まれていません。 さらに、**[!UICONTROL Fields Enclosure]** が有効になっている場合、*additional_attributes* 列の属性値は二重引用符で囲まれます。

<u> 再現手順 </u>:

1. **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]** を持つ製品属性を作成します。
1. 属性を **[!UICONTROL Default]** 属性セットに割り当てます。
1. 新しい属性の日付と時刻の値を持つシンプルな製品を作成します。
1. **[!UICONTROL System]**/*データ転送*/**[!UICONTROL Export]** から製品を CSV ファイルに書き出します。
1. *additional_attributes* 列の属性値を確認します。 日付の部分のみが含まれ、時間は含まれません。
1. 時刻を使用するように属性値を更新します（例：「08/10/22, 3:20 PM」）。
1. CSV ファイルを読み込みます。
1. *catalog_product_entity_datetime* テーブルを確認します。

<u> 期待される結果 </u>:

日付と時刻が適切にエクスポートされ、インポートされます。

<u> 実際の結果 </u>:

日付部分のみがエクスポートされ、インポートされます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
