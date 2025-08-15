---
title: ACSD-55305:[!UICONTROL My Account] で会社のユーザーを編集中にポップアップがフリーズする
description: ACSD-55305 パッチを適用すると、[!UICONTROL Edit Company User] &gt; [!UICONTROL My Account] ページのポップアップ [!UICONTROL Company Structure] 画面のローダーでフリーズするAdobe Commerceの問題が修正されます。
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305:[!UICONTROL My Account] で会社のユーザーを編集中にポップアップがフリーズする

ACSD-55305 パッチは、[!UICONTROL Edit Company User]> [!UICONTROL My Account] ページのポップアップ [!UICONTROL Company Structure] 画面のローダーでフリーズする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 がインストールされている場合に使用できます。 パッチ ID は ACSD-55305 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Edit Company User]*/*[!UICONTROL My Account]* ページで *[!UICONTROL Company Structure]* ポップアップを使用しようとすると、画面にローダーが表示されてフリーズするので、エラーが発生します。

<u> 再現手順 </u>:

1. B2B 会社を作成します。
1. 顧客用に複数選択属性を作成します。
1. 会社管理者の新しく作成した属性に値を割り当てます。
1. 会社管理者としてログインします。
1. [!UICONTROL account dashboard] に移動し、**[!UICONTROL Company Structure]** に移動します。
1. ユーザーを選択します。
1. 「**[!UICONTROL Edit Selected]**」をクリックします。

<u> 期待される結果 </u>:

フォームのポップアップが正確に表示され、会社情報を編集するオプションが表示されます。

<u> 実際の結果 </u>:

フォームのポップアップが表示され、編集することはできません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
