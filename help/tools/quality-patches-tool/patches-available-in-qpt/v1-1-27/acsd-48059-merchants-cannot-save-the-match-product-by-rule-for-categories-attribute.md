---
title: 'ACSD-48059: マーチャントはカテゴリ属性の [!UICONTROL Match product by rule] を保存できません。'
description: ACSD-48059 パッチを適用すると、マーチャントが Categories 属性の [!UICONTROL Match product by rule] を保存できないAdobe Commerceの問題が修正されます。
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
exl-id: e156a752-81b3-4404-81e2-af7ed29f2b1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059: マーチャントは、categories 属性の *[!UICONTROL Match product by rule]* を保存できません

ACSD-48059 パッチでは、マーチャントが [!DNL Visual Merchandiser] の categories 属性の *[!UICONTROL Match product by rule]* を保存できない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-48059 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

マーチャントは、[!DNL Visual Merchandiser] の categories 属性の *[!UICONTROL Match product by rule]* を保存できません。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Visual Merchandiser]**/**[!UICONTROL Visible Attributes for Category Rules]** に移動し、カテゴリを追加します。
1. Adobe Commerce管理者/ **[!UICONTROL Catalog]** / **[!UICONTROL Categories]** に移動します。
   * 「[!UICONTROL Products in Category]」セクションに移動します。
   * categories 属性を持つ新しい *[!UICONTROL Match products by rule]* 条件を追加します。

<u> 期待される結果 </u>:

カテゴリが正常に保存されました。

<u> 実際の結果 </u>:

* カテゴリを新しいルールと条件で保存することはできません。
* *カテゴリの保存中に問題が発生しました* エラーが表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
