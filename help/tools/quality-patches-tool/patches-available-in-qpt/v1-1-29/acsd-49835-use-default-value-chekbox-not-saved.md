---
title: 'ACSD-49835: [!UICONTROL Use Default Value] チェックボックスが保存されていません'
description: ACSD-49835 パッチを適用して、マルチセレクト属性のストアレベルで[!UICONTROL Use Default Value] チェックボックスが正しく保存されないAdobe Commerceの問題を修正します。
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] チェックボックスが保存されていません

ACSD-49835 パッチは、複数選択属性のストアレベルで[!UICONTROL Use Default Value] チェックボックスが正しく保存されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49835です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数選択属性のストアレベルで[!UICONTROL Use Default Value] チェックボックスが正しく保存されません。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に&#x200B;**[!UICONTROL Multiple-select Attribute]**&#x200B;を作成し、属性セットに追加します。
1. **[!UICONTROL Product]**&#x200B;に移動し、**[!UICONTROL Values]**&#x200B;を&#x200B;**[!UICONTROL All Store Views (Default Scope)]**&#x200B;に保存します。
1. 特定の&#x200B;**[!UICONTROL Store View Scope]**&#x200B;に移動し、製品を保存します。
1. **[!UICONTROL Store View Scope]**&#x200B;に移動し、**[!UICONTROL Use Default Value]** チェックボックスをオンにします。

<u>期待される結果</u>:

[!UICONTROL Store View Scope]で[!UICONTROL Use Default Value] チェックボックスをオンにすると、複数選択の属性値が正しく保存されます。

<u>実際の結果</u>:

[!UICONTROL Store View Scope]で[!UICONTROL Use Default Value] チェックボックスをオンにすると、複数選択の属性値が正しく保存されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
