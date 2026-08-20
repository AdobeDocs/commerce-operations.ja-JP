---
title: ACSD-49706：値が選択されていない場合にスウォッチ属性に保存されるデフォルト値
description: 値が選択されていない場合に視覚的なスウォッチ属性のデフォルト値が保存されるAdobe Commerceの問題を修正するには、ACSD-49706 パッチを適用します。
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49706：値が選択されていない場合にスウォッチ属性に保存されるデフォルト値

ACSD-49706 パッチでは、値が選択されていない場合に、視覚的なスウォッチ属性のデフォルト値が保存される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49706です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

値が選択されていない場合、デフォルト値は視覚的なスウォッチ属性に保存されます。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動します。
1. **[!UICONTROL Add New Attribute]**&#x200B;をクリックします。
1. フィールドに入力します。

   * 例えば、入力タイプ *[!UICONTROL Visual Swatch]*&#x200B;を選択し、複数のオプション（*赤*、*緑*&#x200B;など）を追加します。 これらのオプションのいずれかをデフォルトとして選択してください。
   * **[!UICONTROL Save Attribute]**&#x200B;をクリックします。

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;に移動します。
1. *[!UICONTROL Default]*&#x200B;属性セットを編集します。
1. *[!UICONTROL New Attribute]*&#x200B;を列&#x200B;*[!UICONTROL Unassigned Attributes]*&#x200B;から中間列の&#x200B;*[!UICONTROL Product Details]* フォルダーに移動します。

   * **[!UICONTROL Save]**&#x200B;をクリックします。

1. *[!UICONTROL Default]*&#x200B;属性セットを使用して新しい製品を作成します。

   * *[!UICONTROL New Attribute]*&#x200B;を空のままにして、保存します。

1. 保存すると、*[!UICONTROL New Attribute]*&#x200B;に値が表示されます。

<u>期待される結果</u>:

デフォルトでは、*[!UICONTROL New Attribute]*&#x200B;に値が割り当てられていません。

<u>実際の結果</u>:

商品を保存すると、デフォルト値が属性に適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
