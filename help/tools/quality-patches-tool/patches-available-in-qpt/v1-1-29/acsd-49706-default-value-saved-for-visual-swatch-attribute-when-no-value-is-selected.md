---
title: ACSD-49706：値が選択されていない場合にビジュアルスウォッチ属性に対して保存されるデフォルト値
description: 値が選択されていない場合にビジュアルスウォッチ属性のデフォルト値が保存されるAdobe Commerceの問題を修正するために、ACSD-49706 パッチを適用します。
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706：値が選択されていない場合にビジュアルスウォッチ属性に対して保存されるデフォルト値

ACSD-49706 パッチでは、値が選択されていないときに視覚的スウォッチ属性のデフォルト値が保存される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49706 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

値が選択されていない場合、ビジュアルスウォッチ属性のデフォルト値が保存されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** に移動します。
1. 「**[!UICONTROL Add New Attribute]**」をクリックします。
1. フィールドに入力します。

   * 例えば、入力タイプ *[!UICONTROL Visual Swatch]* を選択し、複数のオプション（*赤*、*緑* など）を追加します。 必ず、これらのオプションのいずれかをデフォルトとして選択してください。
   * 「**[!UICONTROL Save Attribute]**」をクリックします。

1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Attribute Set]** に移動します。
1. *[!UICONTROL Default]* 属性セットを編集します。
1. 列 *[!UICONTROL Unassigned Attributes]* の *[!UICONTROL New Attribute]* を中央の列の *[!UICONTROL Product Details]* フォルダーに移動します。

   * 「**[!UICONTROL Save]**」をクリックします。

1. *[!UICONTROL Default]* 属性セットを使用して新しい製品を作成します。

   * *[!UICONTROL New Attribute]* は空のままにして保存します。

1. 保存すると、値が *[!UICONTROL New Attribute]* に表示されます。

<u> 期待される結果 </u>:

デフォルトでは、*[!UICONTROL New Attribute]* に値は割り当てられていません。

<u> 実際の結果 </u>:

製品を保存すると、デフォルト値が属性に適用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
