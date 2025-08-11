---
title: ACSD-66118:[!UICONTROL Store View Code] を更新すると、[!UICONTROL Design Configuration] が更新されない場合 [!UICONTROL Configuration Cache] 設定がクリアされる
description: ACSD-66118 パッチを適用して、Adobe Commerceの問題を修正してください。[!UICONTROL Store View Code] を更新すると、テー [!UICONTROL Design Configuration] が正しく更新されない場合に [!UICONTROL Configuration Cache] （テーマとカスタム設定）がクリアされます。
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
source-git-commit: ef4d6e420f304b0229c54c8ec7bd5500039bcb6b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# ACSD-66118:**[!UICONTROL Store View Code]** を更新すると、**[!UICONTROL Design Configuration]** が更新されない場合 **[!UICONTROL Configuration Cache]** 設定がクリアされる

ACSD-66118 パッチは、**[!UICONTROL Store View Code]** が更新されない場合に **[!UICONTROL Design Configuration]** を更新すると **[!UICONTROL Configuration Cache]** 設定がクリアされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66118 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

テー **[!UICONTROL Design Configuration]** ルが更新されない場合、**[!UICONTROL Store View Code]** フィールドを更新すると、**[!UICONTROL Configuration Cache]** の設定（テーマやカスタム設定など）がクリアされます。

<u> 再現手順 </u>:

1. パネルにログイ **[!UICONTROL Admin]** します。
2. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL All Stores]** に移動します。
3. **[!UICONTROL Content]**/*[!UICONTROL Design]*/**[!UICONTROL Configuration]** でカスタムテーマが設定されているストア表示を編集します。
4. **[!UICONTROL Code]** フィールドを変更します（例：`storeview_1` から `storeview_main`）。
5. 「**[!UICONTROL Save Store View]**」をクリックして、変更を保存します。
6. 更新された **[!UICONTROL Content]** の *[!UICONTROL Design]* / **[!UICONTROL Configuration]** / **[!UICONTROL Store View]** ページを更新するか再度開きます。テーマは選択されません。

<u> 期待される結果 </u>:

**[!UICONTROL Store View Code]** を更新した後も、**[!UICONTROL Design Configuration]** （テーマやカスタム設定を含む）は変更されません。

<u> 実際の結果 </u>:

**[!UICONTROL Design Configuration]** がクリアされます。 テーマがデフォルトに戻り、カスタム設定は失われます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
