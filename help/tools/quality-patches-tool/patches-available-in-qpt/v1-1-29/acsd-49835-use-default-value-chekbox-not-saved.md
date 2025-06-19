---
title: ACSD-49835:[!UICONTROL Use Default Value] チェックボックスが保存されない
description: ACSD-49835 パッチを適用すると、複数選択属性のストアレベルで「[!UICONTROL Use Default Value]」チェックボックスが正しく保存されないAdobe Commerceの問題が修正されます。
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835:[!UICONTROL Use Default Value] チェックボックスが保存されない

ACSD-49835 パッチでは、複数選択属性のストアレベルで [!UICONTROL Use Default Value] チェックボックスが正しく保存されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49835 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数選択属性のストアレベルで、「[!UICONTROL Use Default Value]」チェックボックスが正しく保存されない。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** で **[!UICONTROL Multiple-select Attribute]** を作成し、属性セットに追加します。
1. **[!UICONTROL Product]** に移動して、**[!UICONTROL All Store Views (Default Scope)]** で保存 **[!UICONTROL Values]** ます。
1. 特定の **[!UICONTROL Store View Scope]** ージに移動して、製品を保存します。
1. **[!UICONTROL Store View Scope]** に移動して、「**[!UICONTROL Use Default Value]**」チェックボックスをオンにします。

<u> 期待される結果 </u>:

[!UICONTROL Store View Scope] ールバーの「[!UICONTROL Use Default Value]」チェックボックスをオンにすると、複数選択の属性値が適切に保存されます。

<u> 実際の結果 </u>:

[!UICONTROL Store View Scope] ールバーの「[!UICONTROL Use Default Value]」チェックボックスをオンにすると、複数選択の属性値が正しく保存されない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
