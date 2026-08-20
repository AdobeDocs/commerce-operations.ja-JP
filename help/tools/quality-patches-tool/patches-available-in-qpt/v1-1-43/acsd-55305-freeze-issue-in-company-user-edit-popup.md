---
title: 'ACSD-55305: [!UICONTROL My Account]での企業ユーザー編集中にポップアップがフリーズする'
description: ACSD-55305 パッチを適用して、[!UICONTROL My Account] > [!UICONTROL Company Structure] ページの[!UICONTROL Edit Company User] ポップアップが画面のローダーでフリーズするAdobe Commerceの問題を修正します。
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-55305: [!UICONTROL My Account]での企業ユーザー編集中にポップアップがフリーズする

ACSD-55305 パッチでは、[!UICONTROL My Account]> [!UICONTROL Company Structure] ページの[!UICONTROL Edit Company User] ポップアップが画面のローダーでフリーズする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-55305です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* ページで&#x200B;*[!UICONTROL Edit Company User]* ポップアップを使用しようとすると、画面にローダーが表示されてフリーズするというエラーが発生します。

<u>複製する手順</u>:

1. B2B企業を設立する。
1. 顧客用に複数選択属性を作成します。
1. 会社管理者の新しく作成した属性に値を割り当てます。
1. 会社管理者としてログインします。
1. [!UICONTROL account dashboard]に移動し、**[!UICONTROL Company Structure]**&#x200B;に移動します。
1. ユーザーを選択します。
1. **[!UICONTROL Edit Selected]**&#x200B;をクリックします。

<u>期待される結果</u>:

フォームのポップアップが正確に表示され、会社情報を編集するオプションが提供されます。

<u>実際の結果</u>:

フォームのポップアップが表示され、編集する可能性はありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
