---
title: 'ACSD-66118: [!UICONTROL Configuration Cache]が更新されない場合、[!UICONTROL Store View Code]を更新すると[!UICONTROL Design Configuration]設定がクリアされる'
description: '[!UICONTROL Configuration Cache]が正しく更新されない場合、[!UICONTROL Store View Code]を更新すると[!UICONTROL Design Configuration] （テーマとカスタム設定）がクリアされるAdobe Commerceの問題を修正するには、ACSD-66118 パッチを適用します。'
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-66118: **[!UICONTROL Configuration Cache]**&#x200B;が更新されない場合、**[!UICONTROL Store View Code]**&#x200B;を更新すると&#x200B;**[!UICONTROL Design Configuration]**&#x200B;設定がクリアされる

ACSD-66118 パッチは、**[!UICONTROL Configuration Cache]**&#x200B;が更新されない場合、**[!UICONTROL Store View Code]**&#x200B;を更新すると&#x200B;**[!UICONTROL Design Configuration]**&#x200B;設定がクリアされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66118です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Configuration Cache]**&#x200B;が更新されない場合、**[!UICONTROL Store View Code]** フィールドの更新時に&#x200B;**[!UICONTROL Design Configuration]**&#x200B;設定（テーマ設定やカスタム設定など）がクリアされます。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** パネルにログインします。
2. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**&#x200B;に移動します。
3. カスタムテーマが&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**&#x200B;に設定されているストアビューを編集します。
4. **[!UICONTROL Code]** フィールドを変更します（例：`storeview_1`から`storeview_main`）。
5. **[!UICONTROL Save Store View]**&#x200B;をクリックして変更を保存します。
6. 更新された&#x200B;**[!UICONTROL Store View]**&#x200B;の&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** ページを更新または再度開くと、テーマは選択されません。

<u>期待される結果</u>:

**[!UICONTROL Store View Code]**&#x200B;を更新した後も、**[!UICONTROL Design Configuration]** （テーマとカスタム設定を含む）は変更されません。

<u>実際の結果</u>:

**[!UICONTROL Design Configuration]**&#x200B;がクリアされます。 テーマはデフォルトに戻り、カスタム設定は失われます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
