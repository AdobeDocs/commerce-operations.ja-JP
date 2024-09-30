---
title: 'ACSD-49628: [!DNL Page Builder] CORS エラーにより製品を保存できない'
description: ACSD-49628 パッチを適用して、 [!DNL Page Builder] CORS エラーによって商品の保存が妨げられるAdobe Commerceの問題を修正してください。
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628:[!DNL Page Builder] CORS エラーにより製品を保存できない

ACSD-49628 パッチは、CORS エラーが原因で管理者 [!DNL Page Builder] 製品を保存できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-49628 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

CORS エラー [!DNL Page Builder]、製品の保存を妨げます。

<u> 再現手順 </u>:

1. 管理者としてログインします。
1. 次の権限を持つユーザーロールを作成します。

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**。
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**。

1. *[!UICONTROL Content]* の権限を追加しないでください。
1. 別の管理者ユーザーを作成して、上記で作成した役割をこのユーザーに割り当てます。
1. 製品を作成し、ログアウトします。
1. 2 人目の管理者としてログインします。
1. 製品を編集して保存してみてください。

<u> 期待される結果 </u>:

2 人目の管理者は製品を保存できますが、「**[!UICONTROL Edit with Page Builder]**」ボタンは *[!UICONTROL Content]* の権限を持たない管理者には表示されません。

<u> 実際の結果 </u>:

複数の [!DNL Page Builder] エラーが発生したので、2 人目の管理者は製品を保存できません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
